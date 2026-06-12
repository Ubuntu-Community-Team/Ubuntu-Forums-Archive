---
title: "Installation Alternate ISO over network"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by c.monty on 2009-07-03
hi!
I want to install ubuntu alternate version over network.

I have setup DHCP and TFTP in order to prepare the PXE installation.
On the DHCP server, the relevant ISO file is mounted.

The client (target system) connects to the DHCP server, receives an IP adress and starts booting.

However, the installation dialog request to install driver for the CD ROM drive.
but there's no CD ROM drive on the client.
entering the device manually is not an option because the shared ISO (mounted on DHCP server) is not mounted on client.

how can I skip the step of CD ROM installation in order to continue installation process?

THX

---

