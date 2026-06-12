---
title: "Linblock"
date: 2005-11-27
forum: General Help
---

### Post by ace2005 on 2005-11-27
This is Linblock: [http://dessent.net/linblock/](http://dessent.net/linblock/)

linblock.pl is a Perl script that automatically downloads a list of IP address ranges that are to be blocked, and installs them into the Linux kernel using the iptables interface. The script is intended to give Linux users the easy and automatic blocking that Windows users enjoy with programs such as PeerGuardain or Protowall. The intended audience for this script are BitTorrent tracker administrators who wish to use the "antip2p" blocklist to deny access to undesired parties.

These are the usage instruction i'm using: [http://dessent.net/linblock/linblock.html](http://dessent.net/linblock/linblock.html)

When i try to use it i get this:

> ace@Linux:/mnt/archive/Applications - DEB - Kubuntu/LinBlock$ sudo ./linblock.pl -i /mnt/archive/Applications - DEB - Kubuntu/LinBlock/level1.txt
Can't locate IPTables/IPv4.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./linblock.pl line 39.
BEGIN failed--compilation aborted at ./linblock.pl line 39.
ace@Linux:/mnt/archive/Applications - DEB - Kubuntu/LinBlock$

Can anyone help?  :confused:

---

### Post by jamesford on 2005-11-27
cant help but the linux version of peerguardian works quite fine for me

---

### Post by ace2005 on 2005-11-27
Ok i'll try that then

---

