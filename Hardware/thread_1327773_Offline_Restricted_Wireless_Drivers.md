---
title: "Offline Restricted Wireless Drivers"
date: 2009-11-15
forum: Hardware
---

### Post by RandyJCB on 2009-11-15
Hey all, I need a way to get Ubuntu's restricted wireless drivers before I install Ubuntu on this sketchy laptop. I looked in the device manager to find that the wireless card in question is a Dell 1390 WLAN Mini-Card (Ubuntu said something about it being a Broadcom though). The laptop is an Aspire 3680, and the ethernet port is broken so there's no way for me to just let Ubuntu figure it out on its own. Thanks for the help

---

### Post by gpwil1 on 2011-01-11
I realise this is digging up an old thread - but to help out anyone else having a similar issue, the STA drivers that come with the Ubuntu install are quite useful.

edit - to do this via the command line I use the following script, its hacky I know...

echo "--Adding network settings"
	sudo awk -v var="blah" '{ gsub(/dns mdns4/,"wins dns mdns4",$0); print }' /etc/nsswitch.conf > temp.conf
	sudo mv temp.conf /etc/nsswitch.conf

echo "--Installing network drivers"
	sudo apt-get --reinstall install bcmwl-kernel-source
	sudo modprobe -r b43 ssb wl
	sudo modprobe wl

---

