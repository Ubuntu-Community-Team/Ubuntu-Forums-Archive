---
title: "problem with Installing Ubuntu via Netboot/PXE using Windows"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by crixtiano on 2009-05-01
Hello, 

I'm trying to install ubuntu in a notebook without CD driver.

I'm following this tutorial: 

[http://ubuntuforums.org/showthread.php?t=327597&highlight=pxe+install+intrepid](http://ubuntuforums.org/showthread.php?t=327597&highlight=pxe+install+intrepid)

It works fine, but when I reboot my notebook, appears a black screen and nothing happens. :(

This is the log of Tftpd32 :

> 
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:16:36:35:37:A6 [01/05 01:38:34.249]
DHCP: proposed address 192.168.1.4 [01/05 01:38:36.234]
2664 Request 2 not processed [01/05 01:38:36.281]
Rcvd DHCP Rqst Msg for IP 0.0.0.0, Mac 00:16:36:35:37:A6 [01/05 01:38:36.343]
Previously allocated address 192.168.1.4 acked [01/05 01:38:37.843]
Connection received from 192.168.1.4 on port 2070 [01/05 01:38:37.843]
Read request for file <pxelinux.0>. Mode octet [01/05 01:38:37.843]
Using local port 2418 [01/05 01:38:37.843]
2664 Request 2 not processed [01/05 01:38:37.890]
<pxelinux.0>: sent 29 blks, 14776 bytes in 0 s. 0 blk resent [01/05 01:38:37.968]
Connection received from 192.168.1.4 on port 57089 [01/05 01:38:37.968]
Read request for file <pxelinux.cfg/e0b683e2-08dd-d911-b23e-0016363537a6>. Mode octet [01/05 01:38:37.968]
File <pxelinux.cfg\e0b683e2-08dd-d911-b23e-0016363537a6> : error 2 in system call CreateFile O sistema não pode encontrar o arquivo especificado. [01/05 01:38:37.968]
Connection received from 192.168.1.4 on port 57090 [01/05 01:38:37.968]
Read request for file <pxelinux.cfg/01-00-16-36-35-37-a6>. Mode octet [01/05 01:38:37.968]
File <pxelinux.cfg\01-00-16-36-35-37-a6> : error 2 in system call CreateFile O sistema não pode encontrar o arquivo especificado. [01/05 01:38:37.984]
Connection received from 192.168.1.4 on port 57091 [01/05 01:38:37.984]
Read request for file <pxelinux.cfg/C0A80104>. Mode octet [01/05 01:38:37.984]
File <pxelinux.cfg\C0A80104> : error 2 in system call CreateFile O sistema não pode encontrar o arquivo especificado. [01/05 01:38:37.984]
Connection received from 192.168.1.4 on port 57092 [01/05 01:38:37.984]
Read request for file <pxelinux.cfg/C0A8010>. Mode octet [01/05 01:38:37.984]
File <pxelinux.cfg\C0A8010> : error 2 in system call CreateFile O sistema não pode encontrar o arquivo especificado. [01/05 01:38:37.999]
Connection received from 192.168.1.4 on port 57093 [01/05 01:38:37.999]
Read request for file <pxelinux.cfg/C0A801>. Mode octet [01/05 01:38:37.999]
File <pxelinux.cfg\C0A801> : error 2 in system call CreateFile O sistema não pode encontrar o arquivo especificado. [01/05 01:38:37.999]
Connection received from 192.168.1.4 on port 57094 [01/05 01:38:37.999]
Read request for file <pxelinux.cfg/C0A80>. Mode octet [01/05 01:38:38.015]
File <pxelinux.cfg\C0A80> : error 2 in system call CreateFile O sistema não pode encontrar o arquivo especificado. [01/05 01:38:38.015]
Connection received from 192.168.1.4 on port 57095 [01/05 01:38:38.015]
Read request for file <pxelinux.cfg/C0A8>. Mode octet [01/05 01:38:38.015]
File <pxelinux.cfg\C0A8> : error 2 in system call CreateFile O sistema não pode encontrar o arquivo especificado. [01/05 01:38:38.015]
Connection received from 192.168.1.4 on port 57096 [01/05 01:38:38.015]
Read request for file <pxelinux.cfg/C0A>. Mode octet [01/05 01:38:38.031]
File <pxelinux.cfg\C0A> : error 2 in system call CreateFile O sistema não pode encontrar o arquivo especificado. [01/05 01:38:38.031]
Connection received from 192.168.1.4 on port 57097 [01/05 01:38:38.031]
Read request for file <pxelinux.cfg/C0>. Mode octet [01/05 01:38:38.031]
File <pxelinux.cfg\C0> : error 2 in system call CreateFile O sistema não pode encontrar o arquivo especificado. [01/05 01:38:38.031]
Connection received from 192.168.1.4 on port 57098 [01/05 01:38:38.046]
Read request for file <pxelinux.cfg/C>. Mode octet [01/05 01:38:38.046]
File <pxelinux.cfg\C> : error 2 in system call CreateFile O sistema não pode encontrar o arquivo especificado. [01/05 01:38:38.046]
Connection received from 192.168.1.4 on port 57099 [01/05 01:38:38.046]
Read request for file <pxelinux.cfg/default>. Mode octet [01/05 01:38:38.062]
OACK: <tsize=129,> [01/05 01:38:38.062]
Using local port 2429 [01/05 01:38:38.062]
<pxelinux.cfg\default>: sent 1 blk, 129 bytes in 0 s. 0 blk resent [01/05 01:38:38.109]
Connection received from 192.168.1.4 on port 57100 [01/05 01:38:38.109]
Read request for file <ubuntu-installer/amd64/boot-screens/menu.cfg>. Mode octet [01/05 01:38:38.124]
OACK: <tsize=824,> [01/05 01:38:38.124]
Using local port 2430 [01/05 01:38:38.124]
<ubuntu-installer\amd64\boot-screens\menu.cfg>: sent 2 blks, 824 bytes in 0 s. 0 blk resent [01/05 01:38:38.218]
Connection received from 192.168.1.4 on port 57101 [01/05 01:38:38.218]
Read request for file <ubuntu-installer/amd64/boot-screens/stdmenu.cfg>. Mode octet [01/05 01:38:38.234]
OACK: <tsize=396,> [01/05 01:38:38.234]
Using local port 2431 [01/05 01:38:38.234]
<ubuntu-installer\amd64\boot-screens\stdmenu.cfg>: sent 1 blk, 396 bytes in 0 s. 0 blk resent [01/05 01:38:38.327]
Connection received from 192.168.1.4 on port 57102 [01/05 01:38:38.327]
Read request for file <ubuntu-installer/amd64/boot-screens/text.cfg>. Mode octet [01/05 01:38:38.343]
OACK: <tsize=405,> [01/05 01:38:38.343]
Using local port 2432 [01/05 01:38:38.343]
<ubuntu-installer\amd64\boot-screens\text.cfg>: sent 1 blk, 405 bytes in 0 s. 0 blk resent [01/05 01:38:38.437]
Connection received from 192.168.1.4 on port 57103 [01/05 01:38:38.437]
Read request for file <ubuntu-installer/amd64/boot-screens/amdtext.cfg>. Mode octet [01/05 01:38:38.437]
File <ubuntu-installer\amd64\boot-screens\amdtext.cfg> : error 2 in system call CreateFile O sistema não pode encontrar o arquivo especificado. [01/05 01:38:38.437]
Connection received from 192.168.1.4 on port 57104 [01/05 01:38:38.437]
Read request for file <ubuntu-installer/amd64/boot-screens/gtk.cfg>. Mode octet [01/05 01:38:38.452]
File <ubuntu-installer\amd64\boot-screens\gtk.cfg> : error 2 in system call CreateFile O sistema não pode encontrar o arquivo especificado. [01/05 01:38:38.452]
Connection received from 192.168.1.4 on port 57105 [01/05 01:38:38.452]
Read request for file <ubuntu-installer/amd64/boot-screens/amdgtk.cfg>. Mode octet [01/05 01:38:38.452]
File <ubuntu-installer\amd64\boot-screens\amdgtk.cfg> : error 2 in system call CreateFile O sistema não pode encontrar o arquivo especificado. [01/05 01:38:38.468]
Connection received from 192.168.1.4 on port 57106 [01/05 01:38:38.468]
Read request for file <ubuntu-installer/amd64/boot-screens/stdmenu.cfg>. Mode octet [01/05 01:38:38.468]
OACK: <tsize=396,> [01/05 01:38:38.468]
Using local port 2436 [01/05 01:38:38.468]
<ubuntu-installer\amd64\boot-screens\stdmenu.cfg>: sent 1 blk, 396 bytes in 0 s. 0 blk resent [01/05 01:38:38.546]
Connection received from 192.168.1.4 on port 57107 [01/05 01:38:38.546]
Read request for file <ubuntu-installer/amd64/boot-screens/adtext.cfg>. Mode octet [01/05 01:38:38.546]
OACK: <tsize=572,> [01/05 01:38:38.546]
Using local port 2437 [01/05 01:38:38.546]
<ubuntu-installer\amd64\boot-screens\adtext.cfg>: sent 2 blks, 572 bytes in 0 s. 0 blk resent [01/05 01:38:38.656]
Connection received from 192.168.1.4 on port 57108 [01/05 01:38:38.656]
Read request for file <ubuntu-installer/amd64/boot-screens/adamdtext.cfg>. Mode octet [01/05 01:38:38.656]
File <ubuntu-installer\amd64\boot-screens\adamdtext.cfg> : error 2 in system call CreateFile O sistema não pode encontrar o arquivo especificado. [01/05 01:38:38.656]
Connection received from 192.168.1.4 on port 57109 [01/05 01:38:38.656]
Read request for file <ubuntu-installer/amd64/boot-screens/adgtk.cfg>. Mode octet [01/05 01:38:38.671]
File <ubuntu-installer\amd64\boot-screens\adgtk.cfg> : error 2 in system call CreateFile O sistema não pode encontrar o arquivo especificado. [01/05 01:38:38.671]
Connection received from 192.168.1.4 on port 57110 [01/05 01:38:38.671]
Read request for file <ubuntu-installer/amd64/boot-screens/adamdgtk.cfg>. Mode octet [01/05 01:38:38.671]
File <ubuntu-installer\amd64\boot-screens\adamdgtk.cfg> : error 2 in system call CreateFile O sistema não pode encontrar o arquivo especificado. [01/05 01:38:38.671]
Connection received from 192.168.1.4 on port 57111 [01/05 01:38:38.671]
Read request for file <ubuntu-installer/amd64/boot-screens/vesamenu.c32>. Mode octet [01/05 01:38:38.671]
OACK: <tsize=144392,> [01/05 01:38:38.687]
Using local port 2441 [01/05 01:38:38.687]
<ubuntu-installer\amd64\boot-screens\vesamenu.c32>: sent 283 blks, 144392 bytes in 0 s. 0 blk resent [01/05 01:38:38.812]
Connection received from 192.168.1.4 on port 57112 [01/05 01:38:39.062]
Read request for file <pxelinux.cfg/default>. Mode octet [01/05 01:38:39.077]
OACK: <tsize=129,> [01/05 01:38:39.077]
Using local port 2442 [01/05 01:38:39.077]
TIMEOUT waiting for Ack block #0  [01/05 01:38:54.124]



Please, what's wrong? :confused: 

Thank you!

Cristiano M. Magalhaes

---

