---
title: "usb harddisk extremely slow"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by kurt-beule on 2006-12-16
Hi folks, I got a very strange problem with a new USB 2.0 Harddisk.
System: Ubuntu Edgy on a p4 laptop.

Mounting my new external usb harddisk was not a big issue.
As root, I could set suitable ownership and permissions
 (root:users, drwxrwxr-x), and after plugging it is mounted
 and accessible (desktop icon, file manager window).

But when writing data to the device, first it goes fine
 at up to about 30 MB/s, but then after about 420 MB have been copied,
 the rate goes down to below 1 MB/s.

Apparently, the data is still copied at high speed
 but only in small chunks of a few MB each,
 with inactive time intervals in between (a second or so),
 as suggested by peaks and pauses in cpu activity (monitored in ksysguard).

I canceled the copy and left the truncated file on the disk,
 and then tried to copy something else.
Now that went painfully slow from the beginning.

However when everything was deleted from the disk,
 again the first 400 MB or so would be copied very fast
 and then the rate goes down again like before.
(I tried copying a ~1GB video file and some directories with photo images).

The device was preformatted as vfat,
 but formatting to ext3 (with either qtparted or gparted)
 did not change the problem,
 so apparently it is independent of the file system.

Formatting the disks took more than one hour when creating ext3 partitions.
Interestingly, the status bar immediately went to 6%
 and then stuck and proceeded by only 1% per minute.
Formatting back to vfat took only a few seconds. Strange isn't it?

I tried two different hard disks from different vendors, with very similar results.
The first one was a MAXTOR HDD 320GB 16MB USB U14H320,
 and the second one a TrekStore DataStation maxi t.u 250 GB
 (with a penguin and "Linux compatible" printed on the box).

This is agonizing! I really need the device to work at decent speed.
I guess it might have to do with the usb drivers but how can I know?...
Anyone experienced similar problems?
](*,)

---

### Post by Zamber on 2006-12-19
I have a simmilar problem with my usb pen (Mobile Disk 1GB from TwinMOS). I'm googling for an answer for this issube but for now there is nothing said about it ;/
I have a feeling that it's the drivers fault :P.

Hang there mat I'm looking for a answer ;)

---

On the next tab from my google search I found [this]("http://ubuntuforums.org/showthread.php?p=1802071"). Maybe it will help - testing.

---

ehci_hcd and uhci_hcd is loaded in the kernel

cat /proc/bus/usb/devices shows...

T:  Bus=05 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=126f ProdID=0163 Rev= 1.00
S:  Manufacturer=USB2.0
S:  Product=Mobile Disk
S:  SerialNumber=c1608310e173c0
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr= 80mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=125us
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=  64 Ivl=16ms

Blacklisting in /etc/default/linux-restricted-modules-common is not working as onyxrev said so I'll do it by renameing

sudo mv /lib/modules/2.6.17-10-generic/kernel/drivers/usb/host/ohci-hcd.ko /lib/modules/2.6.17-10-generic/kernel/drivers/usb/host/ohci-hcd.bak

Added the high speed modules to /etc/modules in the proper order:

ehci_hcd
uhci_hcd

Rebooting...

---

The same as before ;/

lsmod is vewing both modules, lspci:

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
(It's connected to the right port :P)

Dunno why it's acting so strange ;/ I'll test my second 1gb pendrive and google more later.

---

The second one (diff vendor) acts the same.

---

### Post by welders4linux on 2007-01-12
Don't know if this helps.  But I had the same problem. 

In moving small files there was no problem.  However larger files would stall/stop.
It was only when I tried the Hard Drive on another computer with  ubuntu live,  that everything worked fine.

The problem was (for me) my main Linux Laptop had USB 1.1 and not 2.0, don't know if its a problem with the linux kernel or the controller on the USB HD not being backwards compatiple 

Moving files via usb 1.1 to my usb 2.0 flash drive is slow but it does transfer.

regards
w4l

---

