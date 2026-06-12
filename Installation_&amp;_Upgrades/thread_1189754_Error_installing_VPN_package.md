---
title: "Error installing VPN package"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by V1RR on 2009-06-17
Hi. I've installed Ubuntu 9.04 yesterday, today i decided to connect to Internet but had not installed needed packages. Rebooted to Windows, downloaded them:
network management framework (PPTP plugin)
network-manager-openvpn

But while installing got an error:
[B]network management framework (PPTP plugin)
Error: Dependency is not satisfiable: pptp-linux

[/B]And this:[B]
network-manager-openvpn
Error: Dependency is not satisfiable: libnm-glib-vpn0 (>= 0.7.0)

[/B]I need to install them to connect to my VPN internet. How can I install them?

---

### Post by Mark Phelps on 2009-06-17
The first is listed in Synaptic, you would use it to install that package. But the problem is really the second -- the library.

Use the link below to search for Debian packages:

[http://www.debian.org/distrib/packages]("http://www.debian.org/distrib/packages")

Once you find the package, download and install it using the package manager (by right-clicking) on the .deb file.

But realize, each package is able to have additional dependencies, you might have to do this LOTS of times.

---

