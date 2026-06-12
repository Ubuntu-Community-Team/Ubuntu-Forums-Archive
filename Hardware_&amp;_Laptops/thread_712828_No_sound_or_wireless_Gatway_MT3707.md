---
title: "No sound or wireless Gatway MT3707"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by kuroiokami on 2008-03-02
I have just installed linux mint 4.0 and My sound and wireless internet do not work. I have found a good link that helped ubuntu users but I am unaware of what version they are running and how to convert the solution int linux mint.
[http://ubuntuforums.org/showthread.php?p=3524207](http://ubuntuforums.org/showthread.php?p=3524207)
here are the results of lspci if that helps.
sean@sean-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

if there is anything else I can do to help you help me please ask.
ps. I have already posted this in the linux mint forum but there seems to be no avail after 2 days T_T

---

### Post by Yellow Pasque on 2008-03-02
OSS4 seems to work a lot better than ALSA for atiixp users for some reason.
Try to build from source, the directions are included in the file. If that's too difficult for you or doesn't work for some reason then use the .deb package and follow the OSS4 howto in my sig

---

### Post by kuroiokami on 2008-03-02
Hold on how do I find out which version of oss I have?

---

### Post by Yellow Pasque on 2008-03-02
OSS4 is not available in the Ubuntu repo. Ubuntu retained OSS3.x for compatibility purposes.

---

### Post by kuroiokami on 2008-03-02
here are the outcome of sudo apt-get install gcc gcc-4.1 gcc-4.1-base make build-essential binutils linux-headers-`uname -r` libssl-dev libssl0.9.8

sean@sean-laptop:~$ sudo apt-get install gcc gcc-4.1 gcc-4.1-base make build-essential binutils linux-headers-`uname -r` libssl-dev libssl0.9.8
[sudo] password for sean:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I could be because I'm updating so I'm going to wait until it finishes updating (hopefully that solves the problem though)

---

### Post by kuroiokami on 2008-03-02
I'm sorry your guide is confusing can you give me any step-by-step instructions? and you do realize that I am running linux mint 4.0 ??? right?

---

