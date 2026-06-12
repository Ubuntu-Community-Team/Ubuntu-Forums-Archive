---
title: "LIRC and RRC-127 Remote"
date: 2010-08-29
forum: Hardware
---

### Post by ssims on 2010-08-29
I recently purchased a Rosewill Windows 7 Certified Media Center Remote RRC-127 ([Newegg]("http://www.newegg.com/Product/Product.aspx?Item=80-101-003")) for use with a freshly installed Ubuntu 10.04 Server / XBMC media center. The problem is that I can't get the darned thing to work...

I found a few threads that talked about needing to install the LIRC CVS version first, then installing through apt-get. I tried installing the LIRC CVS version by issuing: 
```
cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
cd lirc
./autogen.sh
./setup.sh
make
make install
```During the configuration process I select USB Devices then Windows Media Center Transceivers/Remotes (all). After the CVS installation I tested LIRC using the irw command. The receiver has a light that illuminates when a key is pressed, it lit and stayed lit. I unplugged it and plugged it back in, issued apt-get install lirc and tried irw again with the same result.

I have also copied the mceusb remote configuration to the lircd.conf file by issuing:
```
cp /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb /etc/lirc/lircd.conf
```/var/log/syslog shows:
```
[ 1829.016017] usb 5-2: new full speed USB device using uhci_hcd and address 3
[ 1829.211804] usb 5-2: configuration #1 chosen from 1 choice
[ 2027.175015] lirc_dev: IR Remote Control driver registered, major 61
[ 2027.181292] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[ 2027.181299] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[ 2027.181354] usbcore: registered new interface driver lirc_mceusb

```And lsusb shows the receiver is recognized:
```
Bus 005 Device 006: ID 1784:0011 TopSeed Technology Corp.

```However, lspci doesn't show the receiver:
```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
03:01.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)

```If I plug the receiver into my Windows 7 machine I am able to use the remote to successfully launch the media center application and control it using the remote, so I know the receiver/remote work properly.

The receiver shows Product Name: RRC-127, Model #: TSDX-IR07. The remote shows Product Name: RRC-127, Model #:TSGP-IR01 and displays an RC6 IR logo. Any and all help is greatly appreciated. Thanks in advance for your assistance.

-Sean

---

### Post by ellisd on 2010-09-03
SSims, I have also recently purchased this remote and can't get it to work. I am a linux nOOb and am learning as much as I can. Please post back any new developements and if I find something I will do the same. Hopefully we can get this working as others have it seems on New \egg's reviews.

---

### Post by ellisd on 2010-09-09
^bump^...has anyone been able to get this remote to work with Ubuntu?

---

### Post by graying.geek on 2010-09-10
After nearly wearing out  my google I finally followed pretty much the same instructions as above, which are given here:

[http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)

Skip down to the "Downloading using CV" section. 

After rebooting, I was surprised to find the remote now works perfectly. I'm a happy surfer, for now anyway.

My RRC-127 is attached to a Foxconn 330i running Mythbuntu 10.04 Mythtv version 0.23.

---

### Post by autowidget on 2010-09-11
I can confirm I was able to get this working on Lucid with the RRC-127 remote.

I did the install from the CVS repository and used 'Windows Media Center Transceivers/Remotes (all)' as the driver. 

There were two things missing... 

1. /var/run/lirc needs to be created

2. after doing an strace on lircd and starting irw, it seems to expect the socket to be /dev/lirc, however this install creates /dev/lirc0

I did an 'ln -s /dev/lirc0 /dev/lirc' and irw is working correctly.

---

### Post by ellisd on 2010-09-12
Thanks for the confirmation guys!! I just don't know what I'm doing wrong. I've followed all the steps above and on graying.geek's link and explored autowidget's other steps but I cannot seem to get this to work. I get nothing when I test with irw. I am new to Linux/Ubuntu and have a lot to learn so I will continue to test and hopefully figure this out. I suppose it's possible that the new remote is deffective but I don't have a way to test that either. Anyways, again thanks for the responses guys.

---

### Post by rgeyer on 2010-09-28
I got this going after only a couple hours of hacking.

After following the directions from the original post, as well as the MCE_Remotes wiki page, I had the same behavior as the original poster.  I would press a button on the remote, and the receiver LED lit, and stayed on with no real response.

For me, the issue was that the LIRC kernel modules included in Mythbuntu 10.04 were installed and being used instead.  I learned this by doing a;

```
root@htpc:~/compile/lirc# modprobe -v lirc_mceusb
insmod /lib/modules/2.6.32-21-generic/kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko 
insmod /lib/modules/2.6.32-21-generic/kernel/ubuntu/lirc/lirc_mceusb/lirc_mceusb.ko
```

The quick fix is..

```
root@htpc:~/compile/lirc# rm /lib/modules/2.6.32-21-generic/kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko 
root@htpc:~/compile/lirc# rm /lib/modules/2.6.32-21-generic/kernel/ubuntu/lirc/lirc_mceusb/lirc_mceusb.ko
root@htpc:~/compile/lirc# depmod
root@htpc:~/compile/lirc# modprobe lirc_mceusb
root@htpc:~/compile/lirc# /etc/init.d/lirc restart
```

---

### Post by toykilla on 2010-10-17
> **rgeyer said:**
> I got this going after only a couple hours of hacking.

After following the directions from the original post, as well as the MCE_Remotes wiki page, I had the same behavior as the original poster.  I would press a button on the remote, and the receiver LED lit, and stayed on with no real response.

For me, the issue was that the LIRC kernel modules included in Mythbuntu 10.04 were installed and being used instead.  I learned this by doing a;

```
root@htpc:~/compile/lirc# modprobe -v lirc_mceusb
insmod /lib/modules/2.6.32-21-generic/kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko 
insmod /lib/modules/2.6.32-21-generic/kernel/ubuntu/lirc/lirc_mceusb/lirc_mceusb.ko
```The quick fix is..

```
root@htpc:~/compile/lirc# rm /lib/modules/2.6.32-21-generic/kernel/ubuntu/lirc/lirc_dev/lirc_dev.ko 
root@htpc:~/compile/lirc# rm /lib/modules/2.6.32-21-generic/kernel/ubuntu/lirc/lirc_mceusb/lirc_mceusb.ko
root@htpc:~/compile/lirc# depmod
root@htpc:~/compile/lirc# modprobe lirc_mceusb
root@htpc:~/compile/lirc# /etc/init.d/lirc restart
```

This did not work for me

---

### Post by brohmes on 2010-12-04
To anyone still struggling with this, try starting over from scratch.  I just installed ubuntu 10.10 and the latest lirc and my Rosewill RRC-127 MCE remote worked right from the start.  Installed XBMC and all's fine there with the remote as well.  I'm guessing that whatever the issue was, it's been located and resolved.

---

### Post by illdecree on 2011-02-10
> **brohmes said:**
> To anyone still struggling with this, try starting over from scratch.  I just installed ubuntu 10.10 and the latest lirc and my Rosewill RRC-127 MCE remote worked right from the start.  Installed XBMC and all's fine there with the remote as well.  I'm guessing that whatever the issue was, it's been located and resolved.

admittedly, i'm a noob with linux (made the plunge about 6 months ago) and i cannot get this working. i've installed mythbuntu 10.10 and have the exact same remote. everything works on it, except i cannot find an 'escape' key or a 'back' key that works... this is particulaly annoying. any suggestions?

---

