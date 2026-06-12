---
title: "USB &amp; CD: Automount Problem"
date: 2005-10-25
forum: Hardware &amp; Laptops
---

### Post by petervk on 2005-10-25
Recently my ubuntu stopped automounting anything. When I first installed/started using breezy everything worked great. All cds/dvd were reconized, any usbkey I tried worked, etc. A Icon would be added to my desktop, and the link to the resource would be added in the tree in nautilus. But now, in the last few days it suddenly stopped working. CD's don't automount, and my usb key isn't automatically detected.

If I run the disk mounter gnome applet, I can mount my cdrom manually, but the desktop icon is not created, and the link is not added to the places/tree menu in gnome/nautilus (respectively) 

For my USBkey, at first nothing would happen. An icon would appear under "Computer" in nautilus, but when this was clicked a "Error: given UDI is not a mountable volume" error message would appear.

After adding the line:
```
/dev/sda	/media/sda	vfat	defaults,auto,user,umask=000	0	2
```
to my /etc/fstab I can now manually mount my usbkey through the disk mounter applet, but once again, not automatically, or does it add the icons on the desktop or in the places/tree menu.

dmesg output when usb-key is inserted:
```

[4305385.521000] usb 2-1: new full speed USB device using uhci_hcd and address 4[4305386.633000] scsi5 : SCSI emulation for USB Mass Storage devices
[4305386.634000] usb-storage: device found at 4
[4305386.634000] usb-storage: waiting for device to settle before scanning
[4305391.637000]   Vendor: USB       Model: Flash Drive       Rev: 1.11
[4305391.637000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4305391.643000] SCSI device sda: 507901 512-byte hdwr sectors (260 MB)
[4305391.647000] sda: Write Protect is off
[4305391.647000] sda: Mode Sense: 37 00 00 00
[4305391.647000] sda: assuming drive cache: write through
[4305391.660000] SCSI device sda: 507901 512-byte hdwr sectors (260 MB)
[4305391.664000] sda: Write Protect is off
[4305391.664000] sda: Mode Sense: 37 00 00 00
[4305391.664000] sda: assuming drive cache: write through
[4305391.664000]  /dev/scsi/host5/bus0/target0/lun0: p1
[4305391.672000] Attached scsi removable disk sda at scsi5, channel 0, id 0, lun 0
[4305391.674000] usb-storage: device scan complete

```

I would really like to get this working again. Ubuntu is great but this is making it rather annoying to use.

This has been mentioned in several other threads, but no working method has been found.

Link to related Bug Report:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=17562]("http://bugzilla.ubuntu.com/show_bug.cgi?id=17562")

/edit
This is another bug that seems to be related
[http://https://bugzilla.ubuntu.com/show_bug.cgi?id=7641]("http://https://bugzilla.ubuntu.com/show_bug.cgi?id=7641")

Related Posts:
[http://ubuntuforums.org/showthread.php?t=53728]("http://ubuntuforums.org/showthread.php?t=53728")
[http://ubuntuforums.org/showthread.php?t=77141]("http://ubuntuforums.org/showthread.php?t=77141")
[http://ubuntuforums.org/showthread.php?t=76278]("http://ubuntuforums.org/showthread.php?t=76278")

---

### Post by nish81 on 2005-10-25
From what I understood from your reply, (which isn't much, since I have no idea what half of it means...) I think I have the same problem...when i insert by flashdisk it doesn't mount, basically

---

### Post by petervk on 2005-10-25
Possible Solution? not tested yet
[http://qa.mandrivalinux.com/twiki/bin/view/Main/HotPluggableHardwareRemovableMedia]("http://qa.mandrivalinux.com/twiki/bin/view/Main/HotPluggableHardwareRemovableMedia")

Also could be a problem with hal user groups:
[http://http://www.ubuntuforums.org/showthread.php?t=49939]("http://http://www.ubuntuforums.org/showthread.php?t=49939")
Will also test and see if it works.

---

### Post by jeffreyvergara.NET on 2005-10-25
same here... i have this problem too... I also experienced this before in Breezy Preview, and all I can do is to do a fresh installation... yet again...

---

### Post by petervk on 2005-10-25
I was running through the several different possible solutions on this forum and on the net, and now none of my drives mount on the desktop. I had it set so my Windows XP drive was mounted, and that a Fat32 partition was mounted automatically on boot-up. But now they are gone from the desktop/places.

Hopefully someone can find a fix/reason. I'll keep searching and trying things.

---

### Post by petervk on 2005-10-25
Ok, I just tried:
```
sudo hotplug restart
```
and it now detects my USBkey and everything with it works great.

This is after reinstalling hal, and adding the user "hal" to the group "disk".

But my two other partitions are not mounted correctly. They are in nautilus under /etc/media/ but not on the desktop as they used to be or in the places menu for Gnome. And I dought that the USBkey support will last a reboot.

---

### Post by MakubeX on 2005-10-25
In my setup, I don't have autofs installed. Everything still just work.

---

### Post by jeffreyvergara.NET on 2005-10-26
so this means I need to do clean install my Ubuntu again? I think no ones how to fix this yet.. Y_Y

---

### Post by pbrockway2 on 2005-10-26
Hi,

I've been getting the same error as the OP (Error: given UDI is not a 
mountable volume) for about 36 hours.  I've been setting up 5.10,
changing lots of things, and don't know at what stage I lost USB access.

Following a suggestion in one of the threads mentioned above, I
had a look at the group membership of the "hal" user.  In particular
I set the following rights:
    Enable access to external storage devices automatically
    Use CD-ROM devices
    Use floppy drives

(The thread I was reading referred to actual group names, but these
seemed to correspond).

After a reboot my USB key appeared on the desktop!  I hope it stays there
and that this may fix the woes of others - as a "quick fix" checking the hal group
membership beats reformatting the USB key (which I did), or reinstalling
Ubuntu (which I was contemplating)...

Cheers,

Peter

---

### Post by jeffreyvergara.NET on 2005-10-26
the link to hal user seems to be down

"Die Seite kann nicht angezeigt werden."

edited
lol... the link usage is wrong, [http://www.ubuntuforums.org/showthread.php?t=49939]("http://www.ubuntuforums.org/showthread.php?t=49939")

---

### Post by jeffreyvergara.NET on 2005-10-26
[QUOTE=pbrockway2]Hi,

I've been getting the same error as the OP (Error: given UDI is not a 
mountable volume) for about 36 hours.  I've been setting up 5.10,
changing lots of things, and don't know at what stage I lost USB access.

Following a suggestion in one of the threads mentioned above, I
had a look at the group membership of the "hal" user.  In particular
I set the following rights:
    Enable access to external storage devices automatically
    Use CD-ROM devices
    Use floppy drives

(The thread I was reading referred to actual group names, but these
seemed to correspond).

After a reboot my USB key appeared on the desktop!  I hope it stays there
and that this may fix the woes of others - as a "quick fix" checking the hal group
membership beats reformatting the USB key (which I did), or reinstalling
Ubuntu (which I was contemplating)...

Cheers,

Peter[/QUOTE]

thank you very much!!! it really worked!!! :p :p :p :p :p :razz: :razz:

---

### Post by petervk on 2005-10-28
Since I started this thread, I better update my situation.

Before, to try help remedy this problem I installed autofs and usbmount. This didn't help, infact they made the problem worse, so I uninstalled them. Now my usb still doesn't automount right away when I boot up, but after breezy is up and running if I run the command:
```
sudo hotplug restart
```
And then everything works. My other windows partitions are still not loaded as icons on the desktop, but I made links to them in my home directory.

So my problem still exists, but I can use this temporary fix.

On bootup their isn't a "yes" after the "starting hotplug system". No "failed", just nothing at all. Does anyone know how to get hotplug to startup properly?

---

### Post by essexman on 2005-10-29
This is a bug that is being worked on.

The interim fix is via System >> Administration >> Users and Groups

Select the Groups tab an check the box to turn on "Show all users and groups"

Find the groups 'plugdev' and 'cdrom' and add the group member 'hal' to both of them.

Also Make sure that your users are added to these groups as well.

---

### Post by petervk on 2005-10-31
unfortunately that is already the case on my computer, and hotplug doesn't work on boot up. I have to restart the hotplug service every time I start my computer.

---

### Post by essexman on 2005-10-31
[quote=petervk]unfortunately that is already the case on my computer, and hotplug doesn't work on boot up. I have to restart the hotplug service every time I start my computer.[/quote]

Peter

Have you undone everything else?  Did you remove the /dev/sda line that you added fstab?

Just to be sure, because the fix I posted, taken from the bugfix worked well, even though I get no message during boot up.  The same as you, no -OK or failed, but it works.:confused:

---

### Post by petervk on 2005-10-31
My /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro,user_xattr 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto	0       0
/dev/hda1 	/media/winxp 	ntfs 	umask=0222 	0 	0
/dev/hda5 	/media/fat32	vfat 	umask=000 	0 	0

```
As you can see I undid the /dev/sda.
Glad to hear that someone is working on it though. Rather annoying, but I can live with the ```
sudo hotplug restart
``` thing for now.

---

### Post by lfrossati on 2005-11-15
I solved this problem here doing this:

- added hal to the user groups cdrom and plugdev
- installed the packages:

devfsd (1.3.25-23)
liblockfile1 (1.06)
lockfile-progs (0.1.10)
usbmount (0.0.12)
usbview (1.0-6ubuntu1)

I rebooted and everything is working fine now (CDROM and USB Pendrive)

Hope this help someone.

Regards,

Leonardo.

---

### Post by anjilslaire on 2006-03-22
[QUOTE=lfrossati]I solved this problem here doing this:

- added hal to the user groups cdrom and plugdev
- installed the packages:

devfsd (1.3.25-23)
liblockfile1 (1.06)
lockfile-progs (0.1.10)
usbmount (0.0.12)
usbview (1.0-6ubuntu1)

I rebooted and everything is working fine now (CDROM and USB Pendrive)

Hope this help someone.

Regards,

Leonardo.[/QUOTE]

Beautiful!
This fixed all my problems!
Thanks

---

### Post by herger on 2007-12-30
Excuse me, I am new with Ubuntu, coming from 2 happy years with Fedora.
I ahve the same problem, but I can't fix it: I ahve NOTHING in Users and Groups, so I can't add 'hal' to anything...
Could You be so kind to guide me or let me know where I can find the route?
Thanks, ragrds and the best wishes for a Happy New Year

Herger :popcorn:

---

