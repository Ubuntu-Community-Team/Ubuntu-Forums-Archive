---
title: "apt-get update errors in one site"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by ezacon on 2009-02-15
I have two Ubuntu 8.04 servers (one 32bit an another 64bit) on 2 sites.
Both servers have 2 nics and act as gateway (nat) and firewall (shorewall) for internal networks. I have also set up an IPSEC vpn with racoon to connect both internal networks.
Everithing is working as expected, except for "apt-get update" in the 64bit server.
I get very long delays with "Waiting for headers" message, gzip2 error, gpg keys error. The errors are random, bup i always get the "waiting for headers" several times. I have replaced in sources.list with diferent countries.
With the same sources.list, at the same time, i get errors in one site and it works fine in the other.
In failing server and network, i have no conectivity issues other than apt-get.
I have tested installing a vmware server virtual machine in same server with same results with apt.
I have also tested apt after clearing shorewall firewall with same result.
I know it is not a configuration issue because i get same results in server host and new installed virtual machine.

I am realy out of ideas..

Anybody can help?

---

### Post by ezacon on 2009-02-18
Still no luck with this.
Is there an apt trobleshooting faq?
Where can i start?

Realy need some help.

Thanks

---

### Post by ezacon on 2009-02-21
After lots of readings, still not found the issue.
I have successfuly updated one time with apt-get update, apt-get upgrade, with lots of pauses with "Waiting for header" message.

Now i need to install a software sute for the MGE UPS. I have added:
deb [http://opensource.mgeops.com/stable/debian](http://opensource.mgeops.com/stable/debian) binary/
to /etc/apt/sources.list but i get:

W: Imposible obtener [http://es.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release.gpg](http://es.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release.gpg)  Mala línea de cabecera

W: Imposible obtener [http://opensource.mgeops.com/stable/debian/binary/Packages.gz](http://opensource.mgeops.com/stable/debian/binary/Packages.gz)  Mala línea de cabecera

E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.

The message talk about "Bad Header line" in release.gpg.

I have tested same repository in another servir AND IT WORKS. I can install the required package.

Realy, is there any way to reset all APT GPG keys, cache, databases etc...
I realy dont want to reinstall the server to get the same error in a couple of weeks.

---

