---
title: "PXE boot from Ubuntu"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by xe2bss on 2009-06-12
I do have a Dell Latitude C400 with no CDROM drive and no OS, I need to load Windows XP on it, so I decided to try PXE boot using another laptop running Ubuntu 8.10.

So far I have the dhcp server running fine: 

ddns-update-style none;
default-lease-time 86400;
max-lease-time 604800;
option domain-name-servers 172.16.1.1;
authoritative;
#
#
subnet 172.16.1.0 netmask 255.255.255.0 {
         range 172.16.1.10 172.16.1.254;
         filename "/tftpboot/winxp/i386/startrom.n12";
         next-server 172.16.1.1;
         option subnet-mask 255.255.255.0;ddns-update-style none;
default-lease-time 86400;
max-lease-time 604800;
option domain-name-servers 172.16.1.1;
authoritative;
#
#
subnet 172.16.1.0 netmask 255.255.255.0 {
         range 172.16.1.10 172.16.1.254;
         filename "/tftpboot/winxp/i386/startrom.n12";
         next-server 172.16.1.1;
         option subnet-mask 255.255.255.0;
         option routers 172.16.1.1;
         }
#

I choose onboard NIC boot in the C400 and it grabs an IP ok, no problem so the DHCP part of the whole PXE boot process is ok. I created a folder in the Ubuntu laptop called /tftpboot/winxp/i386 and copied all the contents of the i386 folder of an Windows XP install CD into it, I have followed several recommendations on how to do this part but so far no luck, I have got as far as getting the 
"setup is checking your computer" message from the beggining of the install process but it halts right there. Does someone has a step by step on what files the dhcpd server must pass to the host and what other files have to e available and in what order?

Thanks
XE2BSS

---

