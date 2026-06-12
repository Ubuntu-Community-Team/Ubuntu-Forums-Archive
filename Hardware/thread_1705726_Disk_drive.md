---
title: "Disk drive"
date: 2011-03-12
forum: Hardware
---

### Post by smileyboyblue on 2011-03-12
Hi all, total newbie here. I recently made the jump to ubuntu (10.10) and mostly am very happy with it, I just have one quite annoying problem, my disk drive doesn't seem to work. The strange part is it shows up in the my computer section but when I put a disk in (dvd or cd) nothing happens. I'm using vlc as my only media player but I have tried movie player and rhythmbox, neither of which did anything. 
Being such a novice i have no idea where to start troubleshooting this problem, any help/thoughts would be greatly appreciated.

---

### Post by deconstrained on 2011-03-12
Nothing is supposed to happen when you put in a DVD unless you choose settings that would dictate some action being taken automatically when you do so. You could make it this way by opening up a Nautilus (file browser) window and selecting Edit -> Preferences in the menu. You'll find the settings under the "Media" tab.

Otherwise, you usually have to specify within the media player program that you would like to watch a movie, by selecting it from the menu ("Movie" in Movie Player, "Media" in VLC).

Anyhow, put a DVD in, try this command and see what kind of output it gives you:
```
vlc -v dvd:///dev/sr0
```

If that doesn't work, post the output; there's something wrong with the device in that case (or, less likely: udev assigned it a different name).

---

### Post by smileyboyblue on 2011-03-13
Sorry i should have been more clear there. I have already been to the properties of the disk drive and set it to open vlc when any disk is placed in the drive, when that wasn't happening i was going into vlc and selecting media > open disk. Occasionaly vlc gives this error  p, li { white-space: pre-wrap; } [COLOR=#FF0000]"Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/dvd".[/COLOR]
 [COLOR=#FF0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details."[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]How do I check the log?[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]I ran the command you suggested, i got the same error from vlc and this output in the terminal:[/COLOR]
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x8156914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb662d0d4, 0xb662d048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1299191215)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:12747): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Could not open input: No medium found
libdvdread: Can't open /dev/sr0 for reading
libdvdnav: vm: failed to open/read the DVD
[0xb4c06b24] dvdnav demux warning: cannot open dvdnav
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Could not open input: No medium found
libdvdread: Can't open /dev/sr0 for reading
[0xb4c06b24] dvdread demux error: DVDRead cannot open source: /dev/sr0
[0xb4c00634] main input error: open of `dvd:///dev/sr0' failed: (null)

---

### Post by deconstrained on 2011-03-14
> 
************************************************
** **
** No css library available. See **
** /usr/share/doc/libdvdread4/README.Debian **
** for more information. **
** **
************************************************
libdvdread: Could not open input: No medium found
libdvdread: Can't open /dev/sr0 for reading
You need to install encrypted DVD menu/playback support. [Enable the Medibuntu repository](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository) and install libdvdcss;
[https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs](https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs)

---

### Post by smileyboyblue on 2011-03-14
I've done that, i ran sudo apt-get upgrade/update and I'm still getting

(process:9188): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
libdvdnav: vm: failed to open/read the DVD
[0x9450f34] dvdnav demux warning: cannot open dvdnav
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
[0x9450f34] dvdread demux error: DVDRead cannot open source: /dev/sr0
[0xb3f0050c] main input error: open of `dvd:///dev/sr0' failed: (null)


I'm thinking maybe its just my drive :confused:

---

### Post by deconstrained on 2011-03-14
> **smileyboyblue said:**
> I'm thinking maybe its just my drive :confused:
And sr0 exists in /dev? udev might have given it a different alias (I use a SATA optical drive, mind you, so it might be different from what you have).

Anyhow, let's get some more info on that drive. Save the following as devinfo.sh, make it executable, and invoke using "./devinfo.sh /etc/device" on /dev/sr0:
```
#!/bin/bash
udevadm info -q path -n $1 | xargs udevadm info -a -p
```

I haven't any experience using more advanced diagnostic tools on devices than just looking at what information Linux can gather on them, because that usually tells me what I need to solve the problem, or the device makes a noise that indicates it's actually malfunctioning (at least that could be said of optical drives).

---

### Post by smileyboyblue on 2011-03-16
Sorry you lost me with "save/make executable/invoke. If i run the coomand i just get

jude@smileyboyblue:~$ #!/bin/bash
jude@smileyboyblue:~$ udevadm info -q path -n $1 | xargs udevadm info -a -p
info: option requires an argument -- 'n'
info: option requires an argument -- 'p

I have found some more info on the problem. The drive works if i boot the computer with disk already in but as soon as i open/close the drive it becomes unresponsive. If i run sudo lshw -C disk when i boot i get

*-cdrom
       description: DVD-RAM writer
       physical id: 1
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=nodisc

Or if the disk is in the last part becomes :statusready

Once i've opened/closed the drive the last part reads :statusopen and i can't use it.

So it appears to not be noticing I've closed it.

Also I've looked at my fstab and i get

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3da859b6-c8b4-446a-9e7d-829f1c324eec /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b356bc37-b4ba-4445-8e05-3774f0cf7c71 none            swap    sw              0       0


From looking at others online mine seems to missing the last few lines, something like

/dev/scd0       /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0       0
/dev/sr0       /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0       0


I'm not sure about editing this though as I dont want to mess up my fstab.


Thanks for your input on this, I really appreciate you taking the time help a noob out.

---

### Post by deconstrained on 2011-03-17
> **smileyboyblue said:**
> Sorry you lost me with "save/make executable/invoke. If i run the coomand i just get

jude@smileyboyblue:~$ #!/bin/bash
jude@smileyboyblue:~$ udevadm info -q path -n $1 | xargs udevadm info -a -p
info: option requires an argument -- 'n'
info: option requires an argument -- 'p
Replace the "$1" with the path to the block device of your choosing (a device in /dev). $1 in bash is an environment variable -- the first argument passed to the program.

*To make a file executable:*
```
chmod +x file
```

> **smileyboyblue said:**
> 
I have found some more info on the problem. The drive works if i boot the computer with disk already in but as soon as i open/close the drive it becomes unresponsive. If i run sudo lshw -C disk when i boot i get

*-cdrom
       description: DVD-RAM writer
       physical id: 1
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=nodisc

Or if the disk is in the last part becomes :statusready

Once i've opened/closed the drive the last part reads :statusopen and i can't use it.

So it appears to not be noticing I've closed it.

I'd be guessing at this point that it's a hardware or BIOS settings issue. I doubt it's a kernel/driver problem; optical drives (and most scsi devices for that matter) are pretty generic, like hard drives, and don't to my knowledge require any special treatment or module that varies based on the vendor/design, like (for instance) NIC's.

> **smileyboyblue said:**
> From looking at others online mine seems to missing the last few lines, something like

/dev/scd0       /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0       0
/dev/sr0       /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0       0


I'm not sure about editing this though as I dont want to mess up my fstab.
You don't really need the lines in fstab. They would only be useful if you want to manually mount the disk's filesystem.

> **smileyboyblue said:**
> Thanks for your input on this, I really appreciate you taking the time help a noob out.
You're making it way easier than most noobs do. ;-) Seeing someone on the forums actively taking part in investigating and trying to diagnose their own issue restores some of my faith in humanity.

---

