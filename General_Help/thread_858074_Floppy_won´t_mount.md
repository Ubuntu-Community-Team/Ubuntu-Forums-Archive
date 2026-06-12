---
title: "Floppy won´t mount"
date: 2008-07-13
forum: General Help
---

### Post by charonred on 2008-07-13
I´m gradually getting Ubuntu setup, sorting little quirks out. But this has me stumped; I´ve looked through a few posts, but nothing has worked yet.

First time I put a new floppy in 8.04.1 it wouldn´t mount, despite the light being constantly on ? (tried access via Places / Computer)

Next reboot  it mounted and opened a window, but no matter what I do it won´t [COLOR="Blue"]unmount it[/COLOR] cause [COLOR="Blue"]it´s not mounted[/COLOR], despite the floppy light still being on.

What is the problem here, it&#347; a floppy drive - it may be ancient legacy hardware, but shouldn´t it still work, cause it´s still used (I tried several new floppies, and the drive is 3 week new Sony, and works fine in XP)


off at a tangent; what is with the keyboard (US International)
why do I have to tap **´** or **¨**  twice in order for it to display in text ?

---

### Post by Kevbert on 2008-07-13
Some terminal commands:
To format a floppy with vfat so it can be used with both linux and windows
```
mkfs.vfat -F 32 /dev/fd0
```

To mount the floppy
```
mount /media/floppy0
```

To copy a file to the floppy
```
cp /path-to-file/filename /media/floppy
```

To check file saved to floppy
```
cd /media/floppy0
ls -l
```

To unmount a floppy (closing all files and finishing any writing to floppy
```
cd /home/username
umount /media/floppy0
```

---

### Post by charonred on 2008-07-13
thanks, tried those earlier

but again; and get this in terminal
unmount /media/floppy0
bash: unmount: command not found

but regardless, shouldn´t I just be able to click on floppy icon to enter (or at minimum right click mount/unmount). I would think it´s a very basic feature for users, and it shouldn´t be a command line type thing.

obviously something is not right; do I need to install something else ?

---

### Post by Kevbert on 2008-07-13
'umount' not unmount (without the N).  Also on the desktop it should be possible to unmount by right-clicking on the floppy0 icon and selecting 'Unmount Volume'.  In Nautilus (filemanager) you should be able to right-click Floppy0 when shown under places and select 'Unmount'.  If not something is corrupted, and it may be worth re-installing nautilus by using Synaptic Package Manager.

---

### Post by charonred on 2008-07-13
oops ta

but
> umount: /media/floppy0 is not mounted (according to mtab) 

and yet the light is still on ??

---

### Post by Kevbert on 2008-07-13
Can you try formatting a blank unformatted floppy (see above) and try using the commands above to copy a file to the floppy.
I've just been looking at launchpad (Ubuntu bugs). [Bug report #203722]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/203722") may be related to your problem.  What I suggest is that you reinstall nautilus and gnome-mount via Synaptic.  If you still get a problem after that I don't know what to suggest.
Good luck.

---

### Post by charonred on 2008-07-13
No luck with formatting, enter command and nothing happens (Nautilus is sleeping light is still on floppy drive, so it&#347; mounted,but it´s not.

---

### Post by charonred on 2008-07-13
WhenI try to Open it

> Unable to mount location
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by forger on 2008-07-13
Ok no-one asked this: Exactly how are you formatting it?
I use my trusted partition editor:
Applications > Add/remove > search: gparted
Check it, install it and head to System > Administration > Partition Editor

I'm not sure if floppies can be used like this, but here's a crash course:
- The **upper right** corner shows you a list with your devices, find your floppy device, right-click on its partition
- If you see unmount, select it, then right-click again > Format to > **fat32** (you could try fat16 a bit later)
- Hit apply to apply the changes
- When it's done, right-click on the floppy partition again and select Check and then Apply once more. This should check if the partition is ok


P.S. Tell me your paypal to buy you a $5 usb disk - kidding :mrgreen:

---

### Post by forger on 2008-07-13
> **charonred said:**
> WhenI try to Open it

That error looks bad.. is this Ubuntu a boot from a live cd or is this on a hard drive?
Try rebooting the computer and try again

---

### Post by charonred on 2008-07-13
problem is I can´t mount or unmount, yet the floppy drive light remains on 

If I right click the floppy icon in Computer and click the mount/unmount  options, it makes no difference. The only way to get the light to go off is to reboot the PC.

I´m wondering if it has anything to do with it being a Sony floppy; I don´t trust their products (had a Sony CD/RW on another PC a couple of years ago - no end of problems with it)

Ubuntu is a clean install of 8.04.1 to a WD sata 640GB drive (all to itself). 
Apart from this floppy problem it seems to run fine; hardware support has been excellent so far (very impressed).
[LIST]
[*]I can access all other drives (500GB each 3 sata, 1 ide)
[*]Used K3b to burn a .iso via Pioneer DVR-215 no probs (haven´t tried the LG GH20NS10 burner yet)
[*]Running 2 x 19¨ (4:3) monitors as one large screen
[*]paired my Nokia with bluetooth dongle
[/LIST]

I have to reboot into XP for a while; have a pre-production dvd video to check, but no sound in Ubuntu - no codecs for .wmv 

will log back in soon enough

---

### Post by tech0007 on 2008-07-13
a light that's constantly on means your machine's trying hard to read the floppy. its usually a sign of either a bad floppy drive or diskette. since it works in XP, it might be a bug in ubuntu. run 'tail -f /var/log/syslog' as you mount/unmount your diskette and paste it here.

---

### Post by forger on 2008-07-13
> **charonred said:**
> problem is I can´t mount or unmount, yet the floppy drive light remains on 

Hm.. try what I told you, but boot from the live cd, and use the partition editor from there
Note: Just load the disk in, run partition editor in live cd and don't mount it!

> **charonred said:**
> 
I have to reboot into XP for a while; have a pre-production dvd video to check, but no sound in Ubuntu - no codecs for .wmv 

I watch several .wmv files:

If you use a 32-bit (or 64-bit for a lot fewer supported codecs) you can check this out:
[http://www.medibuntu.org](http://www.medibuntu.org)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

The packages you require are:
- w32codecs or w64codecs
- libdvdcss2
- libdvdread3
- mplayer

---

### Post by Kevbert on 2008-07-13
> **charonred said:**
> WhenI try to Open it

The error that you've quoted has been seen before.  I've found it on launchpad, [[COLOR="Red"]bug #208282[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/208282"), and the bug report was closed without a solution.  However it's not clear why the error was reported.  I suggest you raise a new bug report on [[COLOR="Red"]launchpad[/COLOR]]("https://bugs.launchpad.net/") along with all the symptoms, hardware (especially the disk drive make/model) and link it to this post (hyperlink). It may also be worth going to terminal, opening a large window and typing
```
dmesg
```
immediately after you get this error (I think this is the right command, I'm not sure).  You need to open a large terminal window to capture all the messages.  Now select all these messages and press Ctrl-Shift-C to copy them and paste these into an empty text file (Applications- Accessories-Text Editor) with Ctrl-P, save the file and add it to the bug report.
You'll need to register for launchpad.  This is probably the best way forward as these people are the experts.

---

### Post by charonred on 2008-07-13
**tech0007**
as requested - it mounted this time, and unmounted, didn´t like the next disk I placed in, so tried mounting another, but didn´t like that either

> :~$ tail -f /var/log/syslog
Jul 14 07:35:47 amd28u8041 NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jul 14 07:35:48 amd28u8041 NetworkManager: <info>  Clearing nscd hosts cache. 
Jul 14 07:35:48 amd28u8041 NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jul 14 07:35:48 amd28u8041 NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Jul 14 07:35:48 amd28u8041 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Jul 14 07:35:48 amd28u8041 NetworkManager: <info>  Activation (eth0) successful, device activated. 
Jul 14 07:35:49 amd28u8041 avahi-daemon[5726]: Registering new address record for fe80::21d:7dff:fe01:10c1 on eth0.*.
Jul 14 07:35:49 amd28u8041 ntpdate[6703]: can't find host ntp.per.nml.csiro.au 
Jul 14 07:35:51 amd28u8041 ntpdate[6703]: step time server 91.189.94.4 offset -28790.379528 sec
Jul 13 23:36:08 amd28u8041 kernel: [   76.009645] eth0: no IPv6 routers present
Jul 13 23:37:48 amd28u8041 NetworkManager: <debug> [1215963468.903959] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_3505_18E3'). 
Jul 13 23:38:52 amd28u8041 kernel: [  147.024866] floppy0: disk absent or changed during operation
Jul 13 23:38:52 amd28u8041 kernel: [  147.024870] end_request: I/O error, dev fd0, sector 0
Jul 13 23:38:52 amd28u8041 kernel: [  147.024873] Buffer I/O error on device fd0, logical block 0
Jul 13 23:38:52 amd28u8041 kernel: [  147.024882] floppy0: disk absent or changed during operation
Jul 13 23:38:52 amd28u8041 kernel: [  147.024884] end_request: I/O error, dev fd0, sector 8
Jul 13 23:38:52 amd28u8041 kernel: [  147.024885] Buffer I/O error on device fd0, logical block 1
Jul 13 23:38:52 amd28u8041 kernel: [  147.024893] floppy0: disk absent or changed during operation
Jul 13 23:38:52 amd28u8041 kernel: [  147.024894] end_request: I/O error, dev fd0, sector 16
Jul 13 23:38:52 amd28u8041 kernel: [  147.024896] Buffer I/O error on device fd0, logical block 2
Jul 13 23:38:52 amd28u8041 kernel: [  147.024903] floppy0: disk absent or changed during operation
Jul 13 23:38:52 amd28u8041 kernel: [  147.024904] end_request: I/O error, dev fd0, sector 24
Jul 13 23:38:52 amd28u8041 kernel: [  147.024905] Buffer I/O error on device fd0, logical block 3
Jul 13 23:38:52 amd28u8041 kernel: [  147.026569] floppy0: disk absent or changed during operation
Jul 13 23:38:52 amd28u8041 kernel: [  147.026571] end_request: I/O error, dev fd0, sector 0
Jul 13 23:38:52 amd28u8041 kernel: [  147.026573] Buffer I/O error on device fd0, logical block 0
Jul 13 23:39:22 amd28u8041 kernel: [  159.043227] floppy0: disk absent or changed during operation
Jul 13 23:39:22 amd28u8041 kernel: [  159.043231] end_request: I/O error, dev fd0, sector 0
Jul 13 23:39:22 amd28u8041 kernel: [  159.043233] Buffer I/O error on device fd0, logical block 0
Jul 13 23:39:22 amd28u8041 kernel: [  159.043242] floppy0: disk absent or changed during operation
Jul 13 23:39:22 amd28u8041 kernel: [  159.043244] end_request: I/O error, dev fd0, sector 8
Jul 13 23:39:22 amd28u8041 kernel: [  159.043245] Buffer I/O error on device fd0, logical block 1
Jul 13 23:39:22 amd28u8041 kernel: [  159.043252] floppy0: disk absent or changed during operation
Jul 13 23:39:22 amd28u8041 kernel: [  159.043254] end_request: I/O error, dev fd0, sector 16
Jul 13 23:39:22 amd28u8041 kernel: [  159.043255] Buffer I/O error on device fd0, logical block 2
Jul 13 23:39:22 amd28u8041 kernel: [  159.043262] floppy0: disk absent or changed during operation
Jul 13 23:39:22 amd28u8041 kernel: [  159.043264] end_request: I/O error, dev fd0, sector 24
Jul 13 23:39:22 amd28u8041 kernel: [  159.043265] Buffer I/O error on device fd0, logical block 3
Jul 13 23:39:22 amd28u8041 kernel: [  159.044940] floppy0: disk absent or changed during operation
Jul 13 23:39:22 amd28u8041 kernel: [  159.044942] end_request: I/O error, dev fd0, sector 0
Jul 13 23:39:22 amd28u8041 kernel: [  159.044944] Buffer I/O error on device fd0, logical block 0


**forger**
I&#314;l try the live CD boot in the morning, and thanks for the codec info, will get onto that in morning as well.

**kevbert**
that is a long list - and will raise a new bug report tomorrow as well


thanks for all advice, will get onto all in morning again; almost midnight here, so gotta go zzzzzzz soon.

---

### Post by Kevbert on 2008-07-13
Charonred thanks for the thanks...  Hopefully you'll get an answer and the launchpad crew sort out your floppy disk problem for you.

---

### Post by nikgare on 2008-07-13
If the floppy light is always on, doesn't that mean the cable is plugged in the wrong way round?

---

### Post by forger on 2008-07-13
hey nikgare's might be right..
charonred: does it work correctly in XP?

---

### Post by charonred on 2008-07-13
From memory the twisted cable end it goes to the floppy drive, and not m/board, so I fitted it to the floppy drive - can any one confirm that's correct (and the cable stripe is fitted on #1 pin end)

And yep, it works fine in XP, not that I use it much, it's really only there for manually flashing ROM or booting up - will probably hardly get used as I mainly use USB flash drives for transferring files, but it should work no matter.

---

### Post by charonred on 2008-09-02
bump

would like to get the floppy working as I need it to 'boot' Win 3.11 & Win 95/98 installs in VirtualBox

---

### Post by an93l on 2008-11-03
quick question that may be a bit obvious but hasn't been asked. does the floppy light stay on when the disk is removed. The light on the drive just means that there is activity not that it is mounted. does the floppy disk show up in any of your menus or in nautilus If not then you have the issue I have, that Lunix didn't detect the drive in the first place to find out do a lsmod | floppy to see if the module has been loaded. If none of this is the case then my bad.

---

### Post by charonred on 2008-11-03
the light just stays on.

since original post in July, my U8.04.1 system has had all updates and now the disk is accessed and a window opens displaying contents (1 existing small file)

However; I can paste another file into the floppies window, but it doesn't start any writing activity, if I close the window and remove the floppy and then put it back, the pasted file doesn't show (cause it never wrote). 

It still refuses to unmount, the light stays on, the icon remains; but once I remove the floppy, then the light goes off and the icon disappears from desktop.

It's a bug with Ubuntu 8.04, I lodged it as a bug, but todate, it's an unresolved issue - the floppy works in XP, Vista

Floppies may not be used much, but any OS should be able to recognise, mount, read/write/delete, and unmount; so it's something that needs fixing.

I haven't tried it in Intrepid yet, so I might reboot and test it with  the live CD (I'll post back when done).

---

### Post by charonred on 2008-11-03
Well, I tried;

Ubuntu 8.10 (x86/32 bit) Live CD - no floppy access

Mandriva One 2009 (gnome) Live CD - found menu item, but need root privileges to read/write - no go

Mandriva one 2008 & 2009 (KDE) Live CD - xserver won't start (newer ATI video cards) so couldn't do a thing.

ZenWalk 5.2  Live CD - couldn't find desktop icon or menu item for Floppy

Gentoo 2008  Live CD - couldn't find desktop icon or menu item for Floppy


There seems to be a general problem with Linux OSs with detecting, mounting/unmounting floppy drives. This may be due to all the above distros being 'Live CD' versions, or maybe due to the hardware being all current 'late model' or new technology items (ie my system as per signature). So I just don't get it; I can boot from a floppy, I can flash ROM from a floppy, I can use it in XP/Vista, but I can't access a floppy from Linux - what gives ???

I build new systems as a part-time hobby/business, nearly all setup for XP/Vista, and the floppy works; but put it near a Linux OS and NO GO. Although they are hardly used anymore, they have been a reliable boot device and small file media since wayback; they are still manufactured, and I still fit one with each system I build, so why don't they work with Linux ??
 :confused:

---

