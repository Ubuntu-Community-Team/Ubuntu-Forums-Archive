---
title: "Mounting USB flash drive"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by Eran on 2006-10-20
Hi,

I'm trying to get my USB flash drive recognized by my PC (Ubuntu 6.10) but no success so far. A few facts (based on the search I made in the forums):

- I do have gnome-volume-manager installed
- There is no sd* files in /dev
- There is nothing relevant in /media either (besides of the floppy drive and the CDs)

I understand that it should be recognized automatically, but what shall I do?

---

### Post by kidders on 2006-10-20
Hi there,

You need to take a look at what's going on underneath. Try this...

[LIST=1]
[*]Reboot your machine
[*]Open a terminal and type **tail -n 0 -f /var/log/messages**
[*]Plug in your USB device
[*]Post any output
[*]Hit CTRL+C and CTRL+D to close the terminal.
[/LIST]

The output will tell you whether your USB port is even working, whether Ubuntu tries to load any modules when you plug your device in, whether Linux likes your device and knows what's on it, and so on. Alternatively, you can type **dmesg** to see what's happening.

---

### Post by Eran on 2006-10-20
Resolved - it was my mistake. When I have tried with a newly formatted USB drive it worked smoothly. I guess it didn't recognize the previous file system.
Thank you for your advice!

---

### Post by staib on 2006-10-21
Hi - having same sort of problem. I can see the USB stick in File Browser (shows up as a Generic USB Flash Drive) - but it won't mount.  

Based on the advice above I ran the "tail -n 0 -f /var/log/messages" command and this is what it printed:

dad@dad-desktop:~$ tail -n 0 -f /var/log/messages
Oct 21 12:21:39 dad-desktop kernel: [17180804.428000] usb 3-1: new full speed US B device using uhci_hcd and address 5
Oct 21 12:21:39 dad-desktop kernel: [17180804.564000] scsi4 : SCSI emulation for  USB Mass Storage devices
Oct 21 12:21:44 dad-desktop kernel: [17180809.568000]   Vendor: Generic   Model:  USB Flash Drive   Rev: 1.04
Oct 21 12:21:44 dad-desktop kernel: [17180809.568000]   Type:   Direct-Access                    ANSI SCSI revision: 02
Oct 21 12:21:44 dad-desktop kernel: [17180809.580000] sd 4:0:0:0: Attached scsi removable disk sdc
Oct 21 12:21:44 dad-desktop kernel: [17180809.580000] sd 4:0:0:0: Attached scsi generic sg2 type 0

Only a week into Ubuntu this doesn't tell me much! 

What I want to do is simply format the USB device with FAT32 so that I can move files around from several PC's across from Windows to Ubuntu etc...

Any help much appreciated!

Cheers,

Nick

---

### Post by kidders on 2006-10-21
Ah, so it's not formatted? If that's the case, you can't mount a filesystem you haven't created yet. You need to use a partition editor to decide how you want your filesystem(s) laid out on your USB disk, and format it/them. Then, you shouldn't have any difficulties.

The log messages you posted do tell us *something* though. The device you want to repartition is /dev/sdc.
> Attached scsi removable disk sdc
Bear in mind however that, just like in Windows, device names (drives letters) can change from time to time, so check again, the next time you plug your USB disk in ... just to make sure you don't erase the wrong thing!

Hope that helps.

**Edit:** I forgot to mention that Linux will let you put multiple filesystems on a USB flash disk, just like your hard disks. Windows won't, for some reason, and will probably ignore everything except the first one.

Once you create & format partitions on your disk, Ubuntu will recognise them as /dev/sdc1, /dev/sdc2, etc. and mount them automatically for you, when you plug it in. Afaik Windows will assign a drive letter to the first one, and (rather stupidly) ignore any others.

---

