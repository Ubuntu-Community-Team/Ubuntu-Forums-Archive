---
title: "Bad Sector (Something to worry about?)"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by enortham on 2007-06-02
I've been using a new hp pavillion dv6000 for about two months and recently installed ubuntu on a small portion of the drive and left Vista to use the rest. I noticed two errors in the system messages' log that appear to have to do with two bad sectors:

---

Jun  2 01:55:05 Laos kernel: [  748.056000] hda: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Jun  2 01:55:05 Laos kernel: [  748.056000] hda: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Jun  2 01:55:05 Laos kernel: [  748.056000] ide: failed opcode was: unknown
Jun  2 01:55:05 Laos kernel: [  748.060000] end_request: I/O error, dev hda, sector 7431960

---

Jun  2 09:44:50 Laos kernel: [28932.924000] hda: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Jun  2 09:44:50 Laos kernel: [28932.924000] hda: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Jun  2 09:44:50 Laos kernel: [28932.924000] ide: failed opcode was: unknown
Jun  2 09:44:50 Laos kernel: [28932.924000] end_request: I/O error, dev hda, sector 7460204
Jun  2 09:44:50 Laos kernel: [28932.924000] printk: 54 messages suppressed.

---


Should I take any steps to resolve this and should I be worried about my hard drive? I've never seen any bad sector errors in Vista. Of course that might just have to do with Vista overlooking them.

Eric

---

### Post by mkoyle on 2007-06-02
I have found a few different explanations for that error.  One is a DMA problem [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2767394](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2767394) another time where it showed up was a cd drive booting with a cd.

I can't tell from what you have posted what the exact problem is.

Post the output from the following commands:

1. /etc/fstab
2. sudo fdisk -l
3. dmesg

To post the output of dmesg, you might want to write it to a file:
dmesg > dmesg.log

Then open dmesg.log with a text editor and paste it here.

With that information I can try to figure out what's going on, (or) someone smarter than I am can come along and tell you what the problem is.

--Matthew

---

### Post by enortham on 2007-06-02
Here's the info you requested

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=8ef1f183-6f20-4976-b407-9f23d0906822 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=37D790BC31D0F15C /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=7ae1b637-5087-4f32-9a53-82d4f751c92b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

sudo fdisk -l

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12942   103951965    7  HPFS/NTFS
/dev/sda2           12943       13190     1992060   82  Linux swap / Solaris
/dev/sda3           13191       14593    11269597+  83  Linux

```

I added the dmesg logs as two files because of the upload size limit.

I also ran check disk in Vista with no errors found.

Thanks for your help.

Eric

---

### Post by tgalati4 on 2007-06-02
Boot from a Live CD and in the terminal, report the output of the following:

sudo fsck /dev/sda3

If this is a new drive, it could be a break-in problem.  Sometimes drives need exercise before they work properly.  Since you put Linux on the outside cylinders, it could be a mechanical/thermal problem that didn't show up until you used the outside cylinders.

Windows wouldn't report any problems because it is on a separate partition.  The good news is that the heads and drive controller are OK.

If this problem persists, load SMART monitoring tools.

sudo apt-get install smartmontools
man smartmontools  (spacebar to page forward, q to quit)

I've seen DMA errors before, but never media errors due to DMA conflicts.  The fact that the error was repeated 54 times indicates to me that it's the hard drive controller having a hard time reading a sector.

Good luck.

---

### Post by mkoyle on 2007-06-02
> **tgalati4 said:**
> If this is a new drive, it could be a break-in problem.  Sometimes drives need exercise before they work properly.  Since you put Linux on the outside cylinders, it could be a mechanical/thermal problem that didn't show up until you used the outside cylinders.

I've seen DMA errors before, but never media errors due to DMA conflicts.  The fact that the error was repeated 54 times indicates to me that it's the hard drive controller having a hard time reading a sector. 

I could be wrong, but doesn't his /etc/fstab indicate that his hard drive is /dev/sda?   His CD drive is listed as /dev/scd0 but if I am not mistaken, that is just a symlink to /dev/hda.

I feel fairly certain that the errors he is seeing are from his cd drive.  I believe that changing his kernel boot string to have the "ide=nodma" argument will probably get rid of this problem, but I do not know if this will affect anything else.  Pretty sure it will not since the cd drive is the only ATA-connected device.  

One other possible solution would be to update the firmware on the drive (if there is new firmware, this might fix it, too).

To see someone having an identical problem with a DVD drive look at [http://www.linuxquestions.org/questions/showthread.php?t=518673;](http://www.linuxquestions.org/questions/showthread.php?t=518673;) if you do a google search for 
"media error (bad sector): status=0x51" you will find quite a few references to cd or dvd drives in the list (the link above being one of the first).

Sorry to be long winded.  Anyway, unless I am way off base, you will probably just have to edit /boot/grub/menu.list looking for the section that looks about like the following:

```

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-lowlatency
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-lowlatency root=UUID=89774ed4-0473-4cd2-abf7-05e8476cddc6 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-lowlatency
quiet
savedefault

```

and add ide=nodma at the end of the kernel line
kernel          /boot/vmlinuz-2.6.20-16-lowlatency root=UUID=89774ed4-0473-4cd2-abf7-05e8476cddc6 ro quiet splash *ide=nodma*
Don't change the line, just insert ide=nodma at the end.  You are probably running a different kernel than I am and you will have to figure out how to fix it if you change anything already there ;)

--Matthew

---

### Post by tgalati4 on 2007-06-03
Ignore everything I said.  You are probably correct.  The hda drive is giving problems and that is probably an optical drive.  I assumed that /dev/sda is a 120 GB SATA drive, since Feisty labels SATA drives as /dev/sda*.  I missed the hda designation in the dmesg output.

My fault.  

We now continue with our regularly scheduled program.

---

### Post by enortham on 2007-06-03
I tried the ide=nodma and I still get the error (I entered e for edit, appended it to the end of the line, hit enter and then b for boot; it's not there after rebooting so I may be doing something wrong though). It definitely appears to be the dvd drive. If I play a dvd in Totem MoviePlayer 2.18.1, xine-lib version 1.1.4 I get the following error at some points on the disk.

An Error Occurred
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

When that error occurs the bad sector log message appears in the logs. I did follow the steps at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and the disc plays properly at some parts but bails with an error. I tried it in VLC also. I don't think it's the DVD disk though. Unfortunately I don't have another movie with me at this time to test but I'll rent one in a day or two to double check. 

Any ideas?

Thanks for all the help,

Eric

---

### Post by mkoyle on 2007-06-03
Editing the command line when grub is starting is a good way to test things.  If you want something to be permanent, you will need to edit the /boot/grub/menu.lst file I mentioned above.  If you are editing it and it doesn't fix it, there is no reason to make that permanent.

Do you get this error when you use CDs?  Since totem gives that error whenever it has a problem with DVD playback, it could simply be a dirty spot or a scratch on the particular DVD you are trying to play.

More ideas?

1. See if hp has released a firmware update for your DVD drive (since I don't know your exact model number I can't look-- there are a lot of models for that pavilion shell).  You will have to do this in Windows ;)

2. Try an older kernel version (or two) (with and without the ide=nodma switch)... this might do it, too.  Just go to the grub menu at startup and see if there aren't a couple versions with 'smaller' numbers than your current kernel (2.6.20-15-generic might already be in that list, for example).

3. Try a different player program.  I have seen some references to problems with totem in this regard and they suggest xine-ui or vlc (it seems you already tried vlc, though) as more likely to work.  Get xine-ui from synaptic or use apt-get:

```
sudo apt-get install xine-ui
```

... and then see if either of those work.

In every specific reference to the exact problem you are having, the ones that solve it claim that they do it with the ide=nodma switch.  It seems to be a controller/DVD drive driver problem of some sort.  If your pavilion happens to have a 64-bit processor, you might even try the 64-bit version of Ubuntu.  Of course you will be working with other how-to's there, but that might fix this problem.  

--Matthew

---

### Post by enortham on 2007-06-20
I tried xine-ui and that didn't work either. I finally got around to testing another DVD and I didn't have any problems. It must have been due to an issue with the other DVD disc.

Thanks for all your help,

Eric

---

