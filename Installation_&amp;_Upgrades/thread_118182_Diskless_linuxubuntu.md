---
title: "Diskless linux/ubuntu"
date: 2006-01-16
forum: Installation &amp; Upgrades
---

### Post by ssalman on 2006-01-16
I have asked a similar question in a different post, but got no answer, so I’m going to take a step back and ask a general question.
   
  I have an old ultra-slim&light laptop (Thinkpad X20) with no FD or CD drives, but it connects to my home network, where I have PCs with CD/DVD drives. How can I get Linux on this laptop? How about Ubuntu in specific?
   
  For now, I swapped the HD with another laptop that has a CD drive and installed Ubuntu and then swapped it back, but I think there must be a better more permanent solution out there.
   
  Thanks.

---

### Post by earobinson on 2006-01-16
I searched the ubuntu wiki (see sig) for [ubuntu network install] and found [this]("https://wiki.ubuntu.com/Installation/WindowsServerNetboot?highlight=%28network%29%7C%28install%29"), is that what you are looking for?

---

### Post by epostma on 2006-01-16
This thread seems to be about a solution:
[http://ubuntuforums.org/archive/index.php/t-28948.html]("http://ubuntuforums.org/archive/index.php/t-28948.html")
It starts from a windows installation, but I guess you can start from any other OS with minor changes.

---

### Post by ssalman on 2006-01-16
Exactly what I needed, I'll give it a try tonight, thanks you VERY much!!

---

### Post by earobinson on 2006-01-16
let us know how it goes

---

### Post by ssalman on 2006-01-19
I followed the steps in [this]("https://wiki.ubuntu.com/Installation/WindowsServerNetboot") link, and it worked. Thanks earobinson!!
   
  Okay, I it gave me a small hiccup, but eventually it worked. After setting and configuring TFTPD32, and following all steps, it gave me the below message and error. 
   
```
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:10:A4:8E:36:E4 [16/01 23:02:27.515]
  DHCP: proposed address 192.168.2.2 [16/01 23:02:27.515]
  Rcvd DHCP Rqst Msg for IP 0.0.0.0, Mac 00:10:A4:8E:36:E4 [16/01 23:02:28.500]
  Previously allocated address acked [16/01 23:02:28.500]
  Read request for file <\netboot\pxelinux.0>. Mode octet [16/01 23:02:28.515]
  OACK: <tsize=11830,> [16/01 23:02:28.546]
  File <netboot\pxelinux.0> : error 10054 in system call recv An existing connection was forcibly closed by the remote host. [16/01 23:02:28.546]

```    
  I figured it is an IP conflict issue, as it proposed 192.168.2.2, the same IP address for the WIN box running TFTPD32, I toyed with the settings and saved every time but nothing helped, finally I gave up and shut it down, the following day I pulled it up and it just worked. I guess the save button only saves settings to the disk and TFTPD32 had to be restarted for the changes to take effect. At least this is my explanation. 
   
  Anyway, I booted Ubuntu&#8217;s netboot image, and installed Ubuntu on the media-less laptop.
   
  I&#8217;m including the below links, as it may help other people in their search:
  [Installing Ubuntu using Netboot - 1]("https://wiki.ubuntu.com/Installation/Netboot")
  [Installing Ubuntu using Netboot - 2]("https://wiki.ubuntu.com/NetbootInstallRemarks")
  [Installing Ubuntu from Windows]("https://wiki.ubuntu.com/Installation/FromWindows")
  [General PXE/Netboot howto]("http://cui.unige.ch/info/pc/remote-boot/howto.html")
   
  

Enjoy!!

---

