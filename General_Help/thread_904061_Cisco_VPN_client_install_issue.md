---
title: "Cisco VPN client install issue"
date: 2008-08-28
forum: General Help
---

### Post by bhart007 on 2008-08-28
Hi all. ok I had the 4.8 version of the cisco vpn client installed and working yesterday.. however tonight when I tried starting the service it wouldn't.. and I am sorry but I forgot to record the error.  Anyway I thought I'd just re-install, so I followed the vpn_uninstall.. followed by a rm -R of the dir.. then I re un-tarred the download and attempted to re-run the sh vpn_install script but it bombs with this error:

[I]allanon@sputnik:/usr/src/vpnclient$ sudo sh vpn_install
Cisco Systems VPN Client Version 4.8.02 (0030) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 

vpn_install: 47: Syntax error: "(" unexpected
[/I]

I read somewhere that this might have to do with not having the right headers installed.. but I did verify and I do have the correct headers for my kernel version installed.

Any help is appreciated.

---

### Post by mrmorris on 2008-08-28
Do yourself a favor and install vpnc: 
sudo apt-get install vpnc resolvconf

Not only is it 10x easier to install, it also integrates nicely with Gnome if you want:
sudo apt-get install network-manager-vpnc

/Casper

---

