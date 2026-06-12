---
title: "USB memory stick problems - Windows interoperability"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by dansumption on 2007-12-22
I am having problems getting Ubuntu to recognise USB memory sticks.

I have 2 memory sticks, both FAT formatted, and I'm trying to use them to copy some files from Windows (so that I can get my network adapter working in Ubuntu).

Both work fine under Windows, but neither of them do under Ubuntu. One of them just doesn't show up at all, the other mounts but seems to be showing a completely different partition from the one which shows up in Windows, complete with different files (very odd, as I checked it in Windows Disk Manager and it shows as having just one partition, which takes up the entire disk, so I really don't understand where these other files are hiding).

Can anyone give me some pointers as to how I might get these memory sticks mounted under Ubuntu?

---

### Post by eggdeng on 2007-12-22
For the moment, you don't need to use USB keys to transfer the files as you can easily make your W*nd*ws partition available from Ubuntu.
Create a folder under /media to mount your W*nd*ws partition to, the name doesn't matter
```
sudo mkdir /media/WinXP
```
List your partition tables using 
```
sudo fdisk -l
```
Identify the windows partition, say it is /dev/sda1
Now mount it using the mount command
```
sudo mount /dev/sda1 /media/WinXP
```
You should now see an icon on the desktop and be able to browse to the needed files.

---

### Post by eggdeng on 2007-12-22
As for the usb sticks, you can try  to manually mount the one which doesn't show up at all. Plug in the usb key and (quickly) run ```
dmesg | tail
``` You should see output along the lines of
> [17198227.036000] sdb: assuming drive cache: write through
[17198227.036000]  sdb: sdb1
[17198227.036000] sd 6:0:0:0: Attached scsi removable disk sdb
[17198227.036000] sd 6:0:0:0: Attached scsi generic sg1 type 0
[17198227.036000] usb-storage: device scan complete
This tells you that the device is recognised as sdb and has one partition sdb1.
As before, you can create a folder to mount it to
```
sudo mkdir /media/usbkey
```
Then mount the partition you see as before. Assuming it's called sdb1, type
```
sudo mount /dev/sdb1 /media/usbkey
```

---

### Post by dansumption on 2007-12-22
I admit, I haven't tried your workaround, but I forsee a slight problem with it: as per the original post, I'm using the USB stick so that I can get networking running. I'm not sure how I can grab the files from the Windows machine without using the network? Also, as far as I'm aware, fdisk only lists the disks installed in the machine on which fdisk is run, as opposed to disks on another machine running another OS with no network path between the two machines.

Admittedly, I could burn the files to a CD, but I'd still like to get to the bottom of this USB stick problem. Does anyone have any suggestions?

---

### Post by dansumption on 2007-12-22
Weird (but good) - I was just about to try the dmesg tip on the one that doesn't respond at all, when suddenly it appeared. Not sure what has changed - I already tried it half-a-dozen times without any success, the only thing I've done since then is throw some more (NTFS-formatted) SATA disks inside the box. Anyway, I can at least get at the wireless card drivers now.

If anyone has any thoughts on the other USB stick, with the mystery "hidden" partition, then I'd appreciate hearing them. Thanks.

---

### Post by eggdeng on 2007-12-23
> grab the files from the Windows machine

You hadn't mentioned that the W*nd*ws partition was on a different box #-o Anyway, glad you got the stick sorted.

---

### Post by nickg on 2007-12-23
Dansumption,

What type of USB stick are you using? Some devices have separate security / encrypting usb hub hardware built in which will appear as a drive / volume in windows and missing space or unreadable partitions in Linux.

Posting the output from running  lsusb and sudo fdisk -l might help us to identify any inbuilt hub hardware and the nature of the partitions that you have on these keys. Also in windows when you run ctrl-alt-del is there a process 'gemini' running?

---

### Post by dansumption on 2007-12-27
I got to the bottom of the dual-partition memory stick: it does indeed have a "security" partition, and this was showing up in Windows, for some reason, as a floppy disk. I've long since learned to ignore floppy disks, so I hadn't noticed it there.

As a result, I now have my wireless adapter working, and am posting this from Ubuntu. BUT... the (USB) network adapter dies from time to time, and won't come back until I reboot the machine one or more times. I think this may be tied in with the reason why the USB memory stick didn't show up at first, because I am seeing messages like the following in dmesg:

```
hub 1-0:1.0: Cannot enable port 1. Maybe the USB cable is bad?
```

I have tried on various USB sockets, including ones directly attached to the motherboard, ones attached to the motherboard via a cable, and ones on a separate PCI card, but all seem to succumb to the same problem sooner or later. Does anyone have any idea what may cause this, or how I can diagnose the problem some more?

---

### Post by Dngrsone on 2007-12-27
Flash drives have a limited number of writes to them.  If this is an older stick (in other words, it's been written to a lot), then it may be on the verge of failure.

The first signs of this, when running on a Windows machine, is a popup saying something to the effect that the USB port being used is a USB v1.1 when it is actually USB v2.0 (at the same time, the stick in question might not run on a v1.1 port any longer).

If you suspect this is the case (or even if not), I'd suggest you back up all the data from the stick.  Many thumbdrive manufacturers have a lifetime warranty on their USB memory devices (Kingston, for one), and  so you may be able to get your device replaced under warranty when it does fail (performing a format on a already shaky device is often enough to kill it completely).

---

### Post by dansumption on 2007-12-27
The flash drive is not really the problem - it's working fine now that I know what's where, except that under Linux it sometimes drops out. But I see the same problem with the USB network adapter, so the problem seems to be with the USB interface on the Ubuntu machine.

---

### Post by Dngrsone on 2007-12-27
In that case... open up your machine and clean it out.  Make sure your fans are all working properly and that there isn't anything that is causing your Southbridge to overheat (or not get cooled).

---

### Post by dansumption on 2007-12-28
The machine is clean - I've only just built it - admittedly out of old parts, but I gave all the fans and heat dissipators a good going over with the compressed air to force out old dust. All the fans are also working.

The USB network adapter has just gone for its longest period yet - over 24 hours - but it cut out again the moment I plugged in a USB hard disk. Can't paste the full log from dmesg, as I'm back on Windows now while I copy files from the external disk, but it did once again include that same USB error message.

---

### Post by Dngrsone on 2007-12-28
[img]http://xs109.xs.to/xs109/06476/argh.gif[/img]  Hrm... this is sounding like a hardware problem...

Have you tried the sticks in different USB ports?

---

