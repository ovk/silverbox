<p align="center">
  <img src="https://user-images.githubusercontent.com/693072/70379633-1406bd80-18fd-11ea-82d6-209c2bb80f24.png">
</p>

Guide on how to build compact, silent and energy-efficient GNU/Linux home server that runs:

- **Unbound** as a forwarding DNS server that forwards queries to the DNS server of your choice and uses DNS-over-TLS and DNSSEC for
extra security and privacy.
- **NFS server** secured with Kerberos (clean NFSv4-only server).
- **Nextcloud** accessible over HTTP(S) with Let's Encrypt certificates (renewed automatically using Certbot with DNS challenge).
- **Transmission** BitTorent client that communicates only over a VPN connection.
- **SOCKS5 proxy server** that proxies traffic securely over a VPN connection.
- **Git server** for hosting Git repositories.
- **Borg and Rclone** for automatic encrypted incremental backups (both on-site and off-site).
- **Monit** for system monitoring and notifications.
- Script to automatically update DNS record pointing to server's public IP address (in case of dynamic IP).

The server also runs:

- SSH server.
- Docker engine (as most of the workloads are run as containers).

The latest HTML version of the guide is hosted online using GitHub Pages
and can be viewed here: https://ovk.github.io/silverbox

# Compiling
The guide is written in [AsciiDoc](https://en.wikipedia.org/wiki/AsciiDoc) format
and can be compiled into different output formats, such as HTML or PDF.

If you have Docker installed, you can use Asciidoctor Docker container.
For example, to build HTML version:

```
git clone https://github.com/ovk/silverbox.git
docker run -it --rm -v $(pwd)/silverbox:/documents asciidoctor/docker-asciidoctor asciidoctor silverbox-server.adoc
```

Or to build a PDF:

```
docker run -it --rm -v $(pwd)/silverbox:/documents asciidoctor/docker-asciidoctor asciidoctor-pdf silverbox-server.adoc
```

This should produce output file (`silverbox-server.html` or `silverbox-server.pdf`) in the `silverbox`
directory, where all the placeholders replaced with your values.

See [Generating Custom Document](https://ovk.github.io/silverbox/#generating_custom_document)
section for more details.

## Customizing Document
Most of the configuration-specific parameters (such as IP addresses, host names, port numbers etc.)
are not hardcoded, but defined using AsciiDoc attributes.
This way you can redefine these attributes with your specific parameter values
and build your very own version of this document.

By default these parameter values contain simple placeholders,
such as `{SERVER_IP_ADDR}` for the server local IP address.
You can replace them with the values you want by editing `parameters.adoc` file and then compiling the document.

# License
This document is licensed under Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0) License.

For more details see:

- https://creativecommons.org/licenses/by-nc/4.0
- https://creativecommons.org/licenses/by-nc/4.0/legalcode

