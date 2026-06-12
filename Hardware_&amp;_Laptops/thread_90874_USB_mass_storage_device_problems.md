---
title: "USB mass storage device problems"
date: 2005-11-16
forum: Hardware &amp; Laptops
---

### Post by mosabua on 2005-11-16
Hi!

I am trying to get my new iRiver IFP899 flash audio player to talk to my Kubuntu510 box. However I seem to be a bit lost on the go.. 

When I plug in the device the kernel correctly find it and I get something like

Nov 15 21:55:59 localhost kernel: [4308967.203000] usb 3-5: new high speed USB device using ehci_hcd and address 3

when I look at my log in /var/log/messages.

Also 
cat /proc/bus/usb/devices
finds the device correcly and I get

T:  Bus=03 Lev=01 Prnt=01 Port=04 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=4102 ProdID=1008 Rev= 0.01
S:  Manufacturer=iRiver Limited.
S:  Product=IFP-800 HIGH SPEED
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms

But what do I do now? With my USB SD cardreader it gets me a SCSI emulation mounting the card at /sdc1 .. nothing like that happens with the player? I assume I have to mount the fs somehow? But what device mountpoint do I use? Or am I totally missing something...

---

### Post by jliedeka on 2005-11-16
Assuming your iRiver supports the USB bulk storage interface (mine doesn't but there's a utility for it), you need to set up a mount point for it.

The first step is to create an empty directory which will become your mount point.  I call mine /media/usbdisk but it doesn't matter what you call it or where you put it.  Step two is to create an entry in /etc/fstab.  Here's mine:

/dev/sda1 /media/usbdisk vfat rw,nosuid,nodev,sync,noatime,quiet,uid=1000,gid=10

Your device (in my case, /dev/sda1) may be different.  If you boot with the device attached, you should see it in your dmesg output.  You may or may not want all the options I used, the important one is rw.

Once the entry is created, you can mount the device when it is attached by typing:

sudo mount /media/usbdrive 

(or whatever you called it).  In the old days I used to put all my mount points under the /mnt directory but it really doesn't matter.

     Jim

---

### Post by mosabua on 2005-11-19
Thanks for the tip. Didn't work though. My HD is a SATA drive at sda and my usb cardreader normally get mounted at sdc. The player however does not get anything. I tried a lot of combinations.. 

I assume that my player support mass storage. I installed the latest firmware right after I bought it on a different machine.

I did find the ifp package though. Now I get 

Nov 19 19:09:42 localhost kernel: [4315425.420000] usb 3-6: new high speed USB device using ehci_hcd and address 3
Nov 19 19:09:43 localhost usb.agent[10736]:      ifpdev: loaded successfully

in the syslog when I connect the device. 

How can I find out where the drive gets connected. lsusb shows the device just fine.

Bus 003 Device 003: ID 4102:1008 iRiver, Ltd. iFP-800 series mp3/ogg vorbis player

I checked the boot log (dmesg) and there was no mention of a partition the drive is mounted on. Just the one line 
usb 3-5: new high speed USB device using ehci_hcd and address 2

At this stage I am a bit stumped...

---

### Post by mosabua on 2005-11-19
I am sorted out. Looks like my firmware is not a UMS firmware... I installed the ifpline tool and can access the player fine on the command line.

Might have to look for a gui next.

---

