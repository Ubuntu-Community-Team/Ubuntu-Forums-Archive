---
title: "Re - LTSP - boot failing"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by wilman100 on 2009-07-31
Hi,


In a new installation i am trying today........................
My client is stopping soon after picking up an ip address from the server.

It stops with the following on the client :-



TFTP
TXE-T01 : File not found.
PXE - E3B: TFTP Error - file not found

I think it looks as though it needs the client image and have tried

sudo ltsp-build-client --arch i386

but get a NOTE: adding default distribution and components to security mirror and a few rows lower

Failing getting release file [http://archive.ubuntu.com](http://archive.ubuntu.com)


I would add that there is no internet connection

Can anyone help ?

Regards


Dave

---

### Post by Perkins on 2009-08-31
So far as I know, that script gets the latest packages from which to build the client image from the internet.  No internet = no image.  It *might* work to make sure that you have an alternate install CD listed in the apt sources, but I haven't actually tried it.  So I don't know for certain if all the necessary packages are actually on the CD.

---

