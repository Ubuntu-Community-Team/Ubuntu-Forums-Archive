---
title: "[HOWTO] Create Gparted LiveUSB"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by ryu kun on 2007-05-20
Gparted's [LiveUSB]("http://gparted.sourceforge.net/liveusb.php") installation script currently has some problems but you can make a bootable USB disk manually by following these instructions.

I adapted the [instructions]("http://gparted-forum.surf4.info/viewtopic.php?pid=1725#p1725") of LarryT to Ubuntu Feisty Fawn and latest Gparted ISO file.

1. Download Gparted LiveCD ISO file from [here]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828").
2. Mount the ISO file: ```
mount -o loop gparted-livecd.iso /mnt
```
3. Change the directory: ```
cd /mnt
```
4. Plug your usbstick (64mb and fat16/32 are required), and see where it is mounted (e.g. : /media/disk), or mount it manually, like this (before see #1 below) : ```
sudo mount /dev/sdc1 /media/disk
```
5. Copy files to your USB disk. (see #2) ```
cp gparted.dat boot/gparted* syslinux/* /media/disk/
```
6. Unmount the USB disk. ```
umount /media/disk
```
7. Install syslinux. ```
sudo aptitude install syslinux
```
8. Make the usb disk bootable (see #1). ```
syslinux /dev/sdc1
```

Plug your key and boot off USB.

#1: It might be attached to /dev/sdb1 or somewhere else. You can find it by running Gparted and changing the device from top-right corner.
#2: Your USB disk might be mounted to somewhere else. If so Nautilus can tell.

---

### Post by tirengarfio on 2007-07-13
Gracias por el tutorial.

Me da el siguiente los siguentes errores tras realizar el paso 5:

cp: leyendo `gparted.dat': Input/output error
cp: leyendo `boot/gparted': Input/output error
cp: leyendo `boot/gparted.igz': Input/output error
cp: leyendo `syslinux/boot.msg': Input/output error
cp: leyendo `syslinux/options.msg': Input/output error
cp: leyendo `syslinux/splash.lss': Input/output error
cp: leyendo `syslinux/syslinux.cfg': Input/output error

Edgy/Intel

---

### Post by mikelpierre on 2008-02-17
Thank you ryu kun.

I did all the steps in a asus eee without any error or warning, but when I try to boot from the usb device (a sdhc card in my case) I only get a blank screen with a blink cursor on the left upper corner. The sd card is flagged as boot. Any clue?

---

### Post by bobby_d on 2008-03-22
Hi all, 

Not maybe related to the original post, but here are my experiences with gparted live USB. I guess it is not maintained any more ([http://gparted-forum.surf4.info/viewtopic.php?id=1137](http://gparted-forum.surf4.info/viewtopic.php?id=1137)), so I couldn't get a registration to their forum to post there.. But anyway.. 

If you go to the main page, [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/), it says: 
> LiveUSB
Since 0.3.4-x version, GParted LiveUSB can be created from the iso LiveCD.
So there is no need to download another file !

That, unfortunately did NOT work for me.. Btw, running Ubuntu 8.04, with a master hard drive (showing up in ubuntu as /dev/sda with corresponding partitions /dev/sda1 etc) and a USB key (showing up in ubuntu as /dev/sdb for the disk, and the only partition being /dev/sdb1)

As suggested there, I downloaded 
[http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-11.iso](http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-11.iso) 
which is the last available LiveCD iso, and followed the instructions on the webpage - that is, tried to run the set_usb.sh tool there... First there was a problem with the script saying "function not found" (the same problem as, and solved using, "Problem running script" [http://ubuntuforums.org/showthread.php?t=640165](http://ubuntuforums.org/showthread.php?t=640165)). After that was solved, I kept on getting 

```
kernel panic: not syncing: VFS: Unable to mount root fs on unknown-block (1,0)
```

The interesting thing is that, on boot from the usb key, I could see usbehci (or other USB module) load and probe the USB ports - however, no /dev/sdb* device was ever attached.. 
At first I thought that while the script ran, I thought I'd seen it run syslinux on the /dev/sdb device (the disk), not /dev/sdb1 (the partition on it). So I ran syslinux again on /dev/sdb1 device - still no luck. 

So after reading 
[http://www.livedistro.org/resources/documentation/help-guides/knoppix-usb-based-faq?PHPSESSID=6c21acd4361ae29e94692e8b60230389](http://www.livedistro.org/resources/documentation/help-guides/knoppix-usb-based-faq?PHPSESSID=6c21acd4361ae29e94692e8b60230389)
I tried looking into the gparted *.igz file (rename to *.gz first, then it can be extracted with Archive Manager) and funnily enough, couldn't see any usb related objects (how then, was the probing executed, I wonder?? :confused: )

Then, noticing also that old versions of the dedicated liveUSB version are kept: 
[QUOTE=http://gparted-livecd.tuxfamily.org/]Browse releases of the old LiveUSB version here[/QUOTE]

I downloaded the last available Live USB version: 
[http://downloads.sourceforge.net/gparted/gparted-liveusb-0.3.1-1.zip](http://downloads.sourceforge.net/gparted/gparted-liveusb-0.3.1-1.zip)

and simply removed the old files from the USB dongle, and copied the contents of this zip in it (as I had previously ran syslinux)... 

Tried to boot from that one, and could then see both USB ports, and messages like "Attached scsi removable disk sd*", meaning the drives should be there. (Interestingly, while Ubuntu registers my hard drive as /dev/sda, the gparted boot recognizes the same drive as /dev/hda) And, finally as it says here:
[http://gparted.sourceforge.net/larry/livecd/others/boot_hd/boot_hd.htm](http://gparted.sourceforge.net/larry/livecd/others/boot_hd/boot_hd.htm)
> Now reboot the computer and select GParted from the boot menu. When the GParted LiveCD/USB Extra Boot Options comes up select "Pick boot device".

I had not seen these Boot Options in the previous LiveCD boot - so it was good I could see it at that point.. In "pick boot device" I had to ender simply sdb1 (for the /dev/sdb1 partition of the USB thumb flash), click Ok, then click Done in main menu - and finally gparted booted properly.. 

Well, hope this helps, 

Cheers

---

