---
title: "Missing letters on DELL latitude E7450"
date: 2015-03-14
forum: Hardware
---

### Post by martin.venus on 2015-03-14
Hi,

I have a new Dell Latitude E7450 and I have problems with missing letters (please see the attachment). The problem appears non deterministic and reboot (or several reboot) solves the problem. Could you please help me?

Thank you very much.

More info:
Ubuntu 14.10 (kernel 3.16.0-23)

lspci:
> 00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Broadwell-U Camarillo Device (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection (3) I218-LM (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
01:00.0 SD Host controller: O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01)
02:00.0 Network controller: Intel Corporation Wireless 7265 (rev 48)

[ATTACH=CONFIG]260615[/ATTACH]

---

### Post by Vladlenin5000 on 2015-03-14
Hello and welcome.

Do you have the support for your language fully installed and locale set accordingly? Check system settings > Language support.

---

### Post by martin.venus on 2015-03-14
Hi,

I have checked language support and I have it fully installed. At this moment I have everything OK - all letters are as expected. But after reboot sometimes happens that letters are missing.

---

### Post by martin.venus on 2015-03-14
Now I have realised that also log out and log in solves the problem...

It seems that it's somehow related to user account. Now I have logged in as guest account and all was OK. Then I relogged to my account and letters were missing. Then I relogged back to guest account and letters were again OK. Then I had to twice log in and log out to my account to solve the problem.

---

### Post by martin.venus on 2015-03-14
I have made some tests and if I delete all files from my home folder then everything is ok. Even if I move back hidden folders. But as soon as I move there any other folder (Documents, Desktop) then I have problems with missing letters.

---

### Post by JoGiz on 2015-04-14
I have the exact same problem on my brand new Dell Latitude E7450 running Ubuntu 14.10.

Found any solution to this?

---

