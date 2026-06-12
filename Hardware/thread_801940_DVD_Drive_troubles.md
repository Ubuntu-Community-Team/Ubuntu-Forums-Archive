---
title: "DVD Drive troubles"
date: 2008-05-21
forum: Hardware
---

### Post by xenofixus on 2008-05-21
So I recently decided to start using linux again on my laptop and it had been going great.

I have run into a few problems but this one is really starting to annoy me and I have been unable to find any fixes that seem to work for me.

Whenever I put a disk into my DVD drive, It is detected but I am left with an error.  I am using gnome.

At first this error was something along the lines of "Unable to mount the filesystem."

After changing the mount line in the fstab from



**/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0**

to 

**/dev/hda /media/cdrom0 udf,iso9660 0 0**



I a now being told that I lack the privileges to mount the drive (even when I mount it using sudo.)

What I find the wierdest about this is that it reads the disk and sees its title.  Any help would be appreciated, my full fstab (just incase it is wanted) is 



[B]proc            /proc           proc    defaults        0       0
UUID=dcdf1067-f9a6-4137-a7f2-f7720b494308 /               ext3    relatime,errors=remount-ro 0       1
UUID=0a7b34b4-4110-4f45-a877-183e44bbf602 none            swap    sw              0       0
/dev/hda /media/cdrom0 udf,iso9660 0 0[/B]




Oh, another thing (following the advice of previous thread)
After an attempt at mounting, dmesg returns



**udf: bad mount option "0" or missing value**



Not that it matters much, but the disk is ISO 9660:1999 format and As of 12 hours ago (when the machine was running XP) the disk and drive were working fine.

Any help would be appreciated

EDIT: forgot to mention, using Ubuntu 8.04 LTS Desktop Edition

---

### Post by prshah on 2008-05-21
> **xenofixus said:**
> 
Whenever I put a disk into my DVD drive, It is detected but I am left with an error.  I am using gnome.
At first this error was something along the lines of "Unable to mount the filesystem."

A more exact error will be available using the command ```
dmesg | tail
``` a few mins after inserting the offending DVD.

> **xenofixus said:**
> After changing the mount line in the fstab from
**/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0**
to **/dev/hda /media/cdrom0 udf,iso9660 0 0**


Playing with the fstab without fully understanding it first is a bad idea. You have skipped the "options" field in the fstab, which is mandatory.

Change the fstab line to ```

/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
``` Then put in the above command (dmesg) if you still run into trouble.

btw, are you _sure_ your CDrom device is /dev/hda? If it was put in automatically, it's probably OK, but if you've typed it in yourself I'd guess there is something wrong.

I've a feeling that you are giving us only half the information; what else have you tried?

---

### Post by xenofixus on 2008-05-21
Ok, I took your advice and changed back the fstab line: And it was originally set to /dev/hda (its a laptop idk.)

After restarting, I put a disk in (same problem regaurdless of whether disk is UDF or ISO).

the dmesg | tail returns



[B][   48.500280] [fglrx] interrupt source 20008000 successfully enabled
[   48.500286] [fglrx] enable ID = 0x00000004
[   48.501373] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   55.338693] NET: Registered protocol family 10
[   55.339544] lo: Disabled Privacy Extensions
[   53.040291] hda-intel: Invalid position buffer, using LPIB read method instead.
[  123.363108] eth0: no IPv6 routers present
[  124.062848] ath0: no IPv6 routers present
[  107.772381] UDF-fs: No VRS found
[  108.087031] ISOFS: Unable to identify CD-ROM format.[/B]



As for not including the whole story, I guess in a way.
Following a thread found via google (a wonder eh?)
I also added (in turn and later removed both)



[B]libata
ata_piix
piix[/B]

and 

**ide-generic**



to the /etc/modules file.  This did absolutely nothing.
After changing the fstab back, I am getting the old error again which is exactly



**Invalid mount option when attempting to mount the volume 'YB152'.**



YB152 is the disks title.  Thanks for the help so far, really hopen to get this fixed :D.

As I said before, the disk is burnt in ISO 9660:1999.
I used Nero 8 to burn it however I do not feel that is the problem as it fails to read UDF disks, ISO 9660, and even factory pressed disks.
It does however recognize they are there and returns the title. Weird eh?

---

### Post by prshah on 2008-05-21
> **xenofixus said:**
> As I said before, the disk is burnt in ISO 9960:1999.


OK try removing the "iso9660" from the fstab line and rebooting... (just a guess)?

No forget that; boot off a live CD, then try to read the disc.. does it work? If it does, note the fstab from that...

---

### Post by xenofixus on 2008-05-21
After following your advice, disks are readable again BUT!!!
Only disks that are burnt with UDF and/or ISO 9660.

I am still unable to read disks burnt in SOLELY ISO 9660:1999 format.
Here is my dmesg | tail after inserting a disk and waiting a while



[B][  112.599125] NET: Registered protocol family 10
[  112.600788] lo: Disabled Privacy Extensions
[   52.488049] hda-intel: Invalid position buffer, using LPIB read method instead.
[  124.316724] ath0: no IPv6 routers present
[  124.904226] eth0: no IPv6 routers present
[10320.315481] UDF-fs: No VRS found
[10320.357624] ISO 9660 Extensions: Microsoft Joliet Level 3
[11610.474095] ISO 9660 Extensions: RRIP_1991A
[10586.862529] UDF-fs: No VRS found
[23839.610126] ISOFS: Unable to identify CD-ROM format.[/B]



As you can see, the first disk was burnt in plain ISO 9660 w/ joliet and was readable.
The second was burnt in ISO 9660:1999 and comes up as unable to identify.
I am really looking to remedy this problem as I have about 50 DVDs I need to get to that are burnt in this format.

Any help would be appreciated.  Stating this again, the disks that are not working are burnt with Nero 8 in ISO 9660:1999 ONLY!!!

Thanks for the help so far and thanks in advance for any further help.

---

### Post by xenofixus on 2008-05-22
spent a few more hours trying to fix this and still nothing works...

Still need help ><

---

### Post by prshah on 2008-05-22
Did you try booting from a live CD and checking if the disk works?

---

### Post by xenofixus on 2008-05-22
> **prshah said:**
> Did you try booting from a live CD and checking if the disk works?

The same problem still exists when booting from a live CD.

All disks except ISO 9660:1999 are readable.
I know the disks are fine because they were readable in windows only a few days ago...



Thanks so far and thanks in advance (again)

---

### Post by prshah on 2008-05-22
> **xenofixus said:**
> The same problem still exists when booting from a live CD.
Thanks so far and thanks in advance (again)

You can leave the thanks pending until this problem gets cleared... :)

Now I'm just fishing; can you give the output of ```
dmesg | grep -i dvd
```

I'm a little surprised your DVD drive is hda; from what I've seen of hardy, I'd expect it to be sdx, or sr0/sr1 etc.

---

### Post by xenofixus on 2008-05-22
Here is the dmesg | grep -i dvd



[B][   22.086159] hda: Optiarc CD-RW CRX880A, ATAPI CD/DVD-ROM drive
[   22.668536]  sda:<6>hda: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache[/B]



IDK why but this is a laptop and only has one drive.
It was auto detected and set to the hda.
Even with that being the case, why just ISO 9660:1999?

---

### Post by xenofixus on 2008-05-22
edit: sorry for the double post :d

---

### Post by mc4man on 2008-05-22
when you get a chance post ```
sudo lshw -C disk
```

---

### Post by xenofixus on 2008-05-22
> **mc4man said:**
> when you get a chance post ```
sudo lshw -C disk
```

here it is...



[B]  *-disk                  
       description: ATA Disk
       product: Hitachi HTS54168
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: SB2O
       serial: SB2241SGCTG6NE
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0533bb44
  *-cdrom
       description: DVD reader
       product: Optiarc CD-RW CRX880A
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: KX07
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
       configuration: mode=udma2 status=ready
     *-medium
          physical id: 0
          logical name: /dev/hda
[/B]



again I would like to stress that these disks are burnt in ISO 9660:1999 using Nero 8 and were readable with XP when it was installed on this machine (only a couple days ago).

---

### Post by mc4man on 2008-05-22
there'ss an issue i've seen when upgrading with a setup that has only 1 cd/dvd drive. Your problem may not be a result of that, the easiest thing would be to read this thread and if you think it may apply to you post the contents of 70-persistent-cd rules. It's in /etc/udev/rules.d
[http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)

---

### Post by xenofixus on 2008-05-23
> **mc4man said:**
> there'ss an issue i've seen when upgrading with a setup that has only 1 cd/dvd drive. Your problem may not be a result of that, the easiest thing would be to read this thread and if you think it may apply to you post the contents of 70-persistent-cd rules. It's in /etc/udev/rules.d
[http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)

checked out the thread and does not seem to apply to me, just incase here are the contents of said file...



[B]# Optiarc_CD-RW_CRX880A (pci-0000:00:14.1-ide-0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-ide-0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-ide-0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-ide-0:0", SYMLINK+="dvd", ENV{GENERATED}="1"[/B]



judging by what was contained in the thread, that should be normal, correct?

---

### Post by mc4man on 2008-05-23
> that should be normal, correct? Yeah your fine, was thrown by seeing the drive listed twice. 
Do you remember if you closed the disk(s) out when you burned them?

---

### Post by xenofixus on 2008-05-23
Yea, all the disks (DVDs actually) were burnt in Nero 8 on XP in ISO 9660:1999 with no multisession and finalized

This machine was able to read them when XP was installed so I can only assume its something unrelated to the drive itself...

---

### Post by mc4man on 2008-05-23
there may be a couple of ways to transfer the contents to your hd and leave or reburn from ubuntu. (if that's an option)
Possibly if you install the nero linux Trial it could read the disks (free for 14 or 30 days)
ImgBurn running in wine in read mode might do that also.
What might be interesting to try is to temporarily edit the udf, out of the fstab entry for your drive,  set it to autoplay in file management (for dvds) and maybe it will open in the file browser. If it's not looking for udf maybe it will find the iso 9660-1999 ?

---

