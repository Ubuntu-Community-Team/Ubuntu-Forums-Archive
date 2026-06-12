---
title: "[SOLVED] Windows XP dual boot problem"
date: 2008-09-15
forum: General Help
---

### Post by uLBhudda on 2008-09-15
I need some help with my dual boot system. I am new to Linux/Ubuntu, I just started messing with it 2 days ago. Here is the problem.

I had windows XP already on my system and read a few How-To's to get dual boot working. I then downloaded the Ubuntu 8.01.1 LiveCD. Got it to install and everything was good untill the reboot. Now when i restart my computer without the live cd in the cd drive it tells me:
```
Error reading the hard drive
Press Ctrl+Alt+Del to restart.
```

In order to boot i have to have the ubuntu cd in the cd drive and then I choose the option "boot from first hard drive". When i pick this option i get the GRUB loader and then if I choose Ubuntu it loads up with no problems or complaints. But if I choose Windows XP the screen clears and it says:
```
Starting up ...
```
and it just sits there.

I have tried to search the forums for an answer but have been unable to narrow it down. Although few of the posts i read made mention of:
```
sudo fdisk -l
```
here is the output from my terminal:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5a2bfdfd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36308   291643978+   7  HPFS/NTFS
/dev/sda2           36309       60801   196740022+   5  Extended
/dev/sda5           36309       60426   193727803+  83  Linux
/dev/sda6           60427       60801     3012156   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44c444c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2c5c6ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14593   117218241    7  HPFS/NTFS

```

I think the error might be in where grub thinks my windows resides. I cant be sure but I know one of you guys will know the answer. So in addition here is the contents of my /boot/grub/menu.lst:
```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ce5031f4-89d2-4977-956a-855315da1fd5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ce5031f4-89d2-4977-956a-855315da1fd5 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

Please help! I would like to get to my programs that are windows specific. Thanks

---

### Post by scooterpd on 2008-09-15
you could of just done a wubi install from windows and be done with it.  That's probably the easiest way to set up a dual-boot if you are just getting into linux.

---

### Post by ontherooftop on 2008-09-15
I will tell you the easiest way to dual boot  xp and ubuntu. First off delete ubuntu or anything with ubuntu, the go into windows xp 
and download a program called wubi 8.04 (google it)  and it will 
literally do all the work for you it will download and formatt a partitions
and make a boot menu to choose from windows xp or ubuntu, all you have to 
do is decide how much hard drive space you want ubuntu to use and a username
anmd password. Wubi 8.04 is the best for your problem.

---

### Post by uLBhudda on 2008-09-15
Thanks but i think its a little late for that since i cant seem to get to windows at all at the moment :(

---

### Post by Jonie on 2008-09-15
I see that either sda1, sdb1 and sdc1 may, in theory, boot XP. 

First question: on which disk is your Windows installation located. And the second one: which one of the three disks is configured in BIOS as your boot device. The order in which BIOS sees the devices (and GRUB is his follower) may sometimes not match the order of sda, sdb, etc.

---

### Post by uLBhudda on 2008-09-15
The windows is installed on the same drive as ubuntu which is the 500 gig

The 160 gig only has a few files on it and  the 120 gig has nothing.

The bios boot order is set to 500 gig then the 160 gig and then the 120 gig

---

### Post by wobbiebobbie on 2008-09-15
sounds like you corrupted your MBR on windows I can help but I need more info  If you had windows first you can use GParted to part your hard drive and then install ubuntu but if you cant get windows to boot go to another computer and download super Grub and use it to boot windows and start over but be careful

---

### Post by Jonie on 2008-09-15
So then... Replace all references to hd2 in your menu.lst with hd0.

Remove the two lines starting with map.

Make sure that in the file /boot/grub/device.map

hd0 is referenced to /dev/sda, if not, make a correction.

launch GRUB

sudo grub

type find /boot/grub/stage1

then type root (hdx,y) where x,y is what was found by the previous command.

(should be (hd0,4))

then type setup (hd0)

type quit and reboot.

P.S. A hard disk is the first boot device, when the system is lauched form that disk. When you boot from cd, disks may be sorted by physical port address or just black magic. Sad to say, it's the only order GRUB setup may rely upon during Ubuntu installation.

---

### Post by uLBhudda on 2008-09-15
Ok thanks I will give that a try once I get home and post my results

---

### Post by cp1969 on 2008-09-15
Be very, very careful.  I had the same problem and went from a beautifully running dual-boot machine to total catastrophy in about ten easy steps trying to fix my Windows installation.

That computer is now dead as a doornail with no hope of repair.  Lost everything.

[http://ubuntuforums.org/showthread.php?t=911783](http://ubuntuforums.org/showthread.php?t=911783)
[http://ubuntuforums.org/showthread.php?t=919314](http://ubuntuforums.org/showthread.php?t=919314)

---

### Post by uLBhudda on 2008-09-16
Yea seems like i wont be able to do this properly till later tomorrow :( .. Thanks for the heads up on being careful. I will make backups of any file that i plan to modify before continuing. Hoping that they can somehow be fixed with live cd if things go south.

---

### Post by uLBhudda on 2008-09-18
Ok finally got around to being able to mess with the computer.

I did as you said Jonie and now the grub loader is coming up on its own without the need of the cd!

But when i try to load windows it still just says
"Starting up ..."
and then just sits there.

---

### Post by Jonie on 2008-09-19
As I wrote you have three bootable Windows partitions on three disks: sda1, sdb1, sdc1.
I can't guess which one of them you're using to load Windows.

If it resides on sda1, its entry in grub's menu.lst should look like this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

Note that for first hard disk there should be no map lines.

If it is on sdb1, replace it with this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

And finally for sdc1, but you know aleady this isn't going to work (unless it didn't look exactly like this):

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
rootnoverify	(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

There's no catch, one of the variants got to work.

---

### Post by uLBhudda on 2008-09-19
Ok here is what im getting from sudo fdisk -l now:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5a2bfdfd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36308   291643978+   7  HPFS/NTFS
/dev/sda2           36309       60801   196740022+   5  Extended
/dev/sda5           36309       60426   193727803+  83  Linux
/dev/sda6           60427       60801     3012156   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44c444c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2c5c6ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14593   117218241    7  HPFS/NTFS

```

Then here is what my menu.lst looks like now:
```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ce5031f4-89d2-4977-956a-855315da1fd5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ce5031f4-89d2-4977-956a-855315da1fd5 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Here is what the contents of my device.map look like:
```

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

```

I do have windows xp on the same drive as my ubundu which is sda1 the 500 gb drive. So can you spot any thing that i missed?

---

### Post by Jonie on 2008-09-19
rootnoverify, not just root. Otherwise it will try to mount the non-Linux filesystem and will choke on it. You see starting up and then nothing, right?

title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Bucky Ball on 2008-09-19
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
```This is not saying sda1 for your non-linux partition, but sdc1. That would equate to (hd2,0). Are you positive your Windoze install is on first partition, first drive?

You may find you need to put the map lines back in but like:

map (hd0) (hd2)
map (hd2) (hd0)

... or possibly the other way around but I think this is right.

---

### Post by caljohnsmith on 2008-09-19
> **Jonie said:**
> rootnoverify, not just root. Otherwise it will try to mount the non-Linux filesystem and will choke on it. You see starting up and then nothing, right?

title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
Actually, Jonie, you only need "root" to boot a Windows partition because when you use the "chainloader" notation to boot the partition boot record (PBR) of that partition, you don't need to mount the partition. :)

I suspect that uLBhudda will need to run a "chkdsk /r" on his Windows partition, and maybe even "fixboot" to make sure the PBR is OK. Hopefully that will be all it takes to get it going, but there could be more problems than that.

---

### Post by uLBhudda on 2008-09-20
Jonie: I tried adding rootnoverify and it still resulted in it saying "Starting up.." and then nothing.

caljohnsmith: How do I run the check disk on the windows partition? and how do i do fix boot. What commands do i need to type in terminal (once again total newbie to this.)

---

### Post by TeXtonyx on 2008-09-20
I think you could boot to Recovery Console and run fixmbr. This will delete grub and install a standard MBR. Target your first disk. Then put all disks and the Linux partition in the boot.ini I will provide an example.

[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP on primary drive"   /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="XP on backup drive" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="XP on data drive" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
C:\ubuntu.bin="Ubuntu"
-----------
Bootpart will easily copy the first 512 bytes of the first sector of your Ubuntu boot partition. The only hard part is reinstalling grub to the first sector of the boot partition after it has been deleted from the MBR,
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5822846](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5822846)
Herman: The easiest way to install GRUB to the boot sector of your Ubuntu partition is to use Super Grub Disk and make your Super Grub CD, USB or floppy disk.
Once you reboot your PC with Super Grub Disk, go 'Super Grub Disk with Help'--> 'Super Grub Disk'-->'Advanced'-->'GRUB'-->'Restore GRUB in Partition' OR: 'Super Grub Disk with Help'--> 'Super Grub Disk'-->'Advanced'-->'GRUB'-->'Restore GRUB in Partition (+ Hard Disk)'
You'll be offered choices to select from there regarding which partition and which hard disk you need GRUB restored to.

I provided this alternate method to grub because most of your systems are NTFS, and they may have a higher priority. When installing Ubuntu, the option to install to first sector of boot partition is shown under Advanced, the screen where you approved your partition choices. So if XP on first disk is sda1, and you install to the first sector of the Ubuntu boot partition rather than the MBR, the dropdown choice is likely sda2.

---

### Post by Jonie on 2008-09-20
@uLBhudda: boot your Windows into Recovery Console using XP CD, select R when you're asked to and while in Recovery console type ```
fixboot *drive_letter*:
``` Windows may be confused in similar way as Linux as far the letter assignment is concerned with multiple disks, so check the actual *drive_letter* by typing *map* first. If you can, note the output of the map command on a piece of paper and post the output for us to analyze.

@TeXtonyx: if ulBhudda's Windows installation is broken in some way, he may be in trouble to boot his computer at all once GRUB is removed

@caljohnsmith: the difference between root and rootnoverify is very subtle, but rootnoverify seems to work in cases when root doesn't for any reason, but now it seems indeed that he's got trouble with his Windows installation. BTW, chkdsk doesn't check PBR, it relies on it, fixboot does.

@Bucky Ball:
UlBhudda has installed Windows on the very same disk as Linux - (hd0). sdc1 is just a bad comment left by Ubuntu installer that had seen different order of drives when started from CD

---

### Post by TeXtonyx on 2008-09-20
@TeXtonyx: if ulBhudda's Windows installation is broken in some way, he may be in trouble to boot his computer at all once GRUB is removed

It depends on what is most important to him. If it is XP on sda, then if fixboot doesn't work, he will have to try fixmbr first and then a Recovery Console repair, either of which will rewrite the MBR and remove grub. So if he writes grub to the first sector of the Ubuntu boot partition, then he can still boot Ubuntu which super grub. And if XP on the other two drives are booting with grub, they will still boot without grub, though one may have to change the drive order in bios and add to the boot.ini. That is why most people new to Linux who dual boot should do the 1st sector method; the other method, MBR, is harder to fix if something goes wrong.

---

### Post by caljohnsmith on 2008-09-20
> **TeXtonyx said:**
> @TeXtonyx: if ulBhudda's Windows installation is broken in some way, he may be in trouble to boot his computer at all once GRUB is removed

It depends on what is most important to him. If it is XP on sda, then if fixboot doesn't work, he will have to try fixmbr first and then a Recovery Console repair, either of which will rewrite the MBR and remove grub. So if he writes grub to the first sector of the Ubuntu boot partition, then he can still boot Ubuntu which super grub. And if XP on the other two drives are booting with grub, they will still boot without grub, though one may have to change the drive order in bios and add to the boot.ini. That is why most people new to Linux who dual boot should do the 1st sector method; the other method, MBR, is harder to fix if something goes wrong.
From my own experience in doing a "Windows repair", I know that it was not necessary to first restore the Windows MBR in order to do a Windows repair, and also the Windows repair itself did not run fixmbr and overwrite my HDD's MBR with the Windows XP boot loader (Grub in the MBR was untouched after the repair). 

I don't see any advantage at this point in asking uLBhudda to put the Windows XP boot loader back in the MBR, because all the Windows MBR does is chain load the partition boot record of whichever primary partition on the HDD is marked active (has its boot flag set on); Grub is perfectly capable of doing that. It seems like his problem is with Windows at this point, not with the MBR some how booting Windows incorrectly. Correct me if I'm wrong though.

---

### Post by Jonie on 2008-09-20
caljohnsmith:

> Correct me if I'm wrong though.

You're absolutely right. Let's not complicate things, if UlBhudda shrunk his Windows filesystem, his PBR might not have been updated for any reason. Either fixboot from Recovery Console will fix it or it may be rebuilt by testdisk: Advanced Filesystem Tools - Boot - Rebuild BS.

---

### Post by caljohnsmith on 2008-09-20
> **Jonie said:**
> 
You're absolutely right. Let's not complicate things, if UlBhudda shrunk his Windows filesystem, his PBR might not have been updated for any reason. Either fixboot from Recovery Console will fix it or it may be rebuilt by testdisk: Advanced Filesystem Tools - Boot - Rebuild BS.
Well again I'm only speaking from experience, but in addition to using fixboot/testdisk to make sure the Windows' PBR is OK, I think he will probably need to run "chkdsk /r" as that usually takes care of the problems that come when resizing the Windows partition. Maybe fixboot will be enough in his case though. :)

---

### Post by uLBhudda on 2008-09-20
@Jonie: Ok I ran the map command:
```

C: NTFS     152626MB     \Device\Harddisk0\Partition1
D: NTFS     114470MB     \Device\Harddisk1\Partition1
E: NTFS     284808MB     \Device\Harddisk2\Partition1
H:               189188MB     \Device\Harddisk2\Partition2
I:                      2942MB    \Device\Harddisk2\Partition3
A:                                        \Device\Floppy0
F:                                        \Device\CdRom0
G:                                        \Device\CdRom1

```

Recovery cd said that windows was on drive E: and it looks like Ubuntu is on drive H:

---

### Post by caljohnsmith on 2008-09-20
> **uLBhudda said:**
> @Jonie: Ok I ran the map command:
```

C: NTFS     152626MB     \Device\Harddisk0\Partition1
D: NTFS     114470MB     \Device\Harddisk1\Partition1
E: NTFS     284808MB     \Device\Harddisk2\Partition1
H:               189188MB     \Device\Harddisk2\Partition2
I:                      2942MB    \Device\Harddisk2\Partition3
A:                                        \Device\Floppy0
F:                                        \Device\CdRom0
G:                                        \Device\CdRom1

```

Recovery cd said that windows was on drive E: and it looks like Ubuntu is on drive H:
It's OK to run fixboot on all your NTFS partitions, so try the following from the recovery console:
```
fixboot C:
fixboot D:
fixboot E:
```
Reboot, and let us know if that helps; if you still get the same problem loading Windows, then go back to the Windows recovery console and do:
```
chkdsk /r C:
chkdsk /r D:
chkdsk /r E:
```
Reboot, and let us know how it goes.

---

### Post by Jonie on 2008-09-20
@UlBhudda:

> Recovery cd said that windows was on drive E: and it looks like Ubuntu is on drive H:

First - run the fixboots anyway.

Edit: Forget my original post, XP CD is fooled just as Ubuntu was. Everything's ok. Linux and Windows are on first hard disk when you boot from HDD.

It seems I got fooled too :lolflag:

---

### Post by Jonie on 2008-09-20
Yet I only wonder, whether in boot.ini there's rdisk(0) or rdisk(2). However, even if it's mismatched, it will complain that it couldn't load hal.dll. By now we haven't gotten so far.

---

### Post by uLBhudda on 2008-09-20
@caljohnsmith & Jonie: I ran fixboot and it ran ok then restated and tried to boot into windows no luck. Still stoppted at the screen saying "Starting up...". Then ran chkdsk /r it said it fixed some problems, restarted but still didnt progress farther than "Starting up..."

---

### Post by meierfra. on 2008-09-20
Did you ever try  

title Microsoft Windows XP Professional
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

?
You might also try

title Microsoft Windows XP Professional
rootnoverify (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

again.


Mount your Windows partitions in Ubuntu and see which one contains "boot.ini":


```
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
ls /mnt/sda1

```

This lists all the file in the root directory of /dev/sda1. Check whether "boot.ini" is among them.

Repeat with "sdb1" and "sdc1" in place of "sda1"

---

### Post by uLBhudda on 2008-09-20
@meierfra: Here is what i get when i do the mount.
```

 DBS.TXT                 MSDOS.SYS                  temp
ATI           Documents and Settings  MSOCache                   VIRTPART.DAT
AUTOEXEC.BAT  Downloads               msvci70.dll                vlc
bootex.log    DVDPATH.TXT             NTDETECT.COM               WINDOWS
boot.ini      EyeCandyLog.txt         ntldr                      wizard.txt
Config.Msi    FolderShareTemp         Program Files              YServer.txt
CONFIG.SYS    IO.SYS                  RECYCLER
Database      iPhone                  System Volume Information

```

and as you can see boot.ini is part of this list.

---

### Post by meierfra. on 2008-09-20
I assume that  was the output from /dev/sda1.

Did any of the other partition also contain a "boot.ini"?


You can look at boot.ini via

```
gksudo gedit /mnt/sda1/boot.ini
```

You might try testdisk to rebuild the Boot sector:

```
sudo apt-get install testdisk
sudo testdisk /dev/sda
```

Choose "proceed" on the first screen, then
 "intel"
 "advanced", 
Select the Windows partition (although it should be selected already) and choose 
"boot"
"RebuildBS"

---

### Post by caljohnsmith on 2008-09-20
> **meierfra. said:**
> 
You might try testdisk to rebuild the Boot sector
I'm just trying to follow your line of reasoning, meierfra, but if uLBhudda all ready ran "fixboot" on his Windows partition, isn't that the same as the testdisk procedure you describe above? 

Seems like since he has all his boot files, and he doesn't seem to be getting an error that would result from an incorrect boot.ini, he is maybe only left with doing a "Windows Repair" at this point if he wants to salvage his Windows partition. He's all ready done "fixboot" and "chkdsk /r" on the Windows partition, so isn't a Windows repair maybe the next logical step? Or do you have some other ideas?

---

### Post by uLBhudda on 2008-09-20
I have a feeling that GRUB is just not looking at the right place to find windows to load it. When i pick the option to boot windows it does nothing after it get to the "Starting up..." it just sits there no hard drive spinning nothing.

---

### Post by meierfra. on 2008-09-20
In  my experience testdisk's  "rebuildBS" and "fixboot"  are not completely identical, so I think "rebuildBS" is worth a shot.    After that, I agree, "Windows Repair" is the only option left (although one might do  "chkdsk /r" one more time and maybe  "fixmbr", there are some strange cases where fixmbr lets you boot windows. I  know that does not make any sense, but it does happen)

No real reason to look at "boot.ini" at this time, but it only takes a second, so one might as well do it.

Anyway, I only got involved since I wasn't convinced that the boot files are on "/dev/sda1" and so "root (hd1,0)" might solve the OP's problem.  But according to   post 31, it seems I was wrong about that.

---

### Post by meierfra. on 2008-09-20
> have a feeling that GRUB is just not looking at the right place to find windows to load it.

Since the boot files are on sda1 and Ubuntu is also on sda (and Ubuntu boots with "root (hd0,4)")   "root (hd0,0)" is definitely the correct address for the Windows System Partition. So Grub is looking at the right place. 

That means the problems lies with the Windows Partition. You can try my testdisk suggestion (which will only take a  few seconds, but only has  small chance  to succeed) or you can   directly follow caljohnsmith advice and do a "Windows Repair" with you Windows CD.

There is also a small chance that  some bug prevents Grub to successfully load the  Windows boot sector. In this case "fixmbr" in the Windows CD console might let you boot  windows again.

Since "chkdsk /r" found and   fixed some errors, you might run it again. Sometimes it takes two or more runs, to fix all the problems.

---

### Post by uLBhudda on 2008-09-20
@meierfra: Ok i did the testdisk but this is the output it has given what do i need to do now?
```

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 36307 254 63  583287957

filesystem size           583287957 583287945
sectors_per_cluster       8 8
mft_lcn                   746015 746015
mftmirr_lcn               13281991 13281991
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1
Extrapolated boot sector and current boot sector are different.


[  Dump  ]  [  List  ]  [ Write  ]  [  Quit  ]

```

---

### Post by meierfra. on 2008-09-20
Select "Write".

---

### Post by uLBhudda on 2008-09-20
ok had to leave for a bit will redo that once I get home

---

### Post by Jonie on 2008-09-20
There's one thing worth trying before the radical steps (restoring Windows MBR, doing Windows repair) are taken. I hope anyway that testdisk will do the trick.

If you have a floppy drive (I know, a relic), format a floppy in Windows XP (not in any other OS). Don't select create an MS-DOS disk. Then copy these three files onto the floppy from a working Windows XP computer: ntldr, ntdetect.com and boot.ini. Then your PC should boot from that floppy directly into XP bypassing Windows Partition Boot Sector. I wouldn't recommend creating an image of that floppy and booting it with GRUB/memdisk as a permanent solution since any attempt to access floppy drive from XP started in this way will result in BSOD. Nevertheless, it's worth a shot, too.

---

### Post by uLBhudda on 2008-09-20
@meierfra: Here is what it gave me back once i hit write.
```


Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 36307 254 63  583287957

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.


```

---

### Post by TeXtonyx on 2008-09-20
uLBhudda wrote: 
I need some help with my dual boot system. I am new to Linux/Ubuntu, 
I just started messing with it 2 days ago. Here is the problem.
I had windows XP already on my system and read a few How-To's to get 
dual boot working. I then downloaded the Ubuntu 8.01.1 LiveCD. Got it 
to install and everything was good untill the reboot. Now when i 
restart my computer without the live cd in the cd drive it tells me:
Code:
Error reading the hard drive
Press Ctrl+Alt+Del to restart.
In order to boot i have to have the ubuntu cd in the cd drive and 
then I choose the option "boot from first hard drive". When i pick 
this option i get the GRUB loader and then if I choose Ubuntu it 
loads up with no problems or complaints. But if I choose Windows XP 
the screen clears and it says:
Code: Starting up ... 
--------------------------------------------------
My thinking was that the XP OS and partition were working before the Ubuntu installation. How can Ubuntu *cause* a corruption? By overwriting the XP partition or causing a problem when grub is written to the MBR. How does Ubuntu create damage that fixboot is supposed to fix? I've seen some posts saying the problem is with Windows and some saying the problem is with grub's configuration. The normal order is fixmbr, fixboot and BOOTCFG/rebuild. 
I think about half the time fixmbr will fix the problem immediately. Since reinstalling grub is a bit complicated, I think OP should just delete Ubuntu and then install Ubuntu again, this time putting grub in the first sector of the Ubuntu boot partition. Why is that the expert method in a system nearly all XP? It removes this problem that has used up four pages of ideas, the problem never occurs. There is no worry about using fixes in the proper order to maximize efficiency. And it does not give up booting Ubuntu with Super Grub while you fix Windows.  The OP is a Ubuntu novice and has had Ubuntu for two days at the time of his first post.  Many of these posts have been directed at fixing grub and that is part of the problem since it takes up time.  I mean uLBhudda could have run fixmbr and reinstalled Ubuntu is 45 minutes.  Maybe a repair install will need to be run but if that needs to be done then it still needs to be done even if you try to retain grub as it is now in the MBR. The problem is that you guys have had the OP messing with grub for 
longer than it takes to do fixmbr, fixboot, BOOTCFG/rebuild and a new Ubuntu install.
Putting grub in the MBR was how I did it with RH6 also because novices just want something that works.  It is an inferior method for dual booting with a 3/4 XP situation.
fixmbr should have been the very first step in the troubleshooting process, because Windows not booting is the problem, maintaining grub in the mbr is non-essential and has led to a big waste of time. I saw a good idea to mount the XP partition from Ubuntu.
The troubleshooting went in reverse order, from trying least likely fixes first (grub) and saving the most likley fixes till last.  The thinking on this problem was not organized. 
You people are competent enough to learn how to set up dual booting the best way, not the way that is easiest for a newcomer.  To make no mistake, I'm not criticizing grub, but I'm critical of using grub for dual booting with Windows once you know a better way. By that I mean it is not grub's fault that Windows is easier to troubleshoot if grub is not in the MBR, that is not its function to provide.

[http://www.linuxquestions.org/questions/linux-general-1/does-a-windows-xp-repair-install-overwrite-the-mbr-551035/](http://www.linuxquestions.org/questions/linux-general-1/does-a-windows-xp-repair-install-overwrite-the-mbr-551035/)
One person said it did overwrite the MBR and another said it didn't during a Repair install.

---

### Post by meierfra. on 2008-09-21
> Here is what it gave me back once i hit write ...

Thats exactly as expected. Just quit testdisk. Reboot and hope for the best.

---

### Post by uLBhudda on 2008-09-21
Woohoo!! well guys I am typing this from windows! I really appreciate all y'all help thank you very much. That last testdisk bit did the trick :) I will be marking this solved. Once again thank you all very much!

---

### Post by caljohnsmith on 2008-09-21
We're all glad you can now boot Windows, uLBhudda. :)

Well I'm definitely going to remember this thread, as I had no idea that using testdisk to repair the Windows partition boot sector could actually be more successful than running Microsoft's own "fixboot"; I thought they were supposed to be virtually equivalent. I guess "virtually" is the key word here though, since they obviously must some how differ. Meierfra, in your experience, is testdisk consistently better at fixing the Windows partition boot sector compared to fixboot, or is it a toss-up every time? In other words, you never know which might give the best results?

---

### Post by meierfra. on 2008-09-21
> meierfra, in your experience, is testdisk consistently better at fixing the Windows partition boot sector compared to fixboot, or is it a toss-up every time? In other words, you never know which might give the best results?

I'm not a 100% sure about it, but this is how I see it:

The boot sector contains the following:

1)  The code necessary to boot XP

2)  Information about the file system of the XP partition,

FixBoot  fixes the  boot code, but not the file system information.

Testdisk "RebuildBS" fixes the information about the file system, but not the boot code. 

So it really depends on the situation which one will  do the job. (And sometimes you will have to use both)

Suppose for example that someone installs grub to the boot sector of the XP  partition. This changes 1) but not 2).  So fixboot will work, but RebuildBS does not. (Although you can still solve the problem with  testdisk: Replace  the boot sector by its backup)

Now suppose  the XP partition is resized, but the partitioning program forgets to update the files system information.  Then RebuildBS will work, but fixboot does not.

---

### Post by caljohnsmith on 2008-09-21
> **meierfra. said:**
> I'm not a 100% sure about this, but this is how I see it:

The boot sector contains the following:

1)  The code necessary to boot XP

2)  Information about the file system of the XP partition,

FixBoot  fixes the  boot code, but not the file system information.

Testdisk "RebuildBS" fixes the information about the file system, but not the boot code. 

I did some googling around, and from what I read, the NTFS initial program loader (IPL) or metadata file $Boot actually can take up to the first 16 sectors of the NTFS partition. Also, the Master File Table (MFT) does not have a set position in sectors in case there are bad sectors near the beginning of the partition, but the MFT is always located near the beginning of the partition as well as possible. 

So when you say "Rebuild BS" fixes the info about the file system, isn't that the job of testdisk's "Repair MFT" function? Isn't "rebuild BS" used to fix the Windows boot loader in the first 16 sectors of the partition? I read that "fixboot" replaces the entire $Boot metadata file, not just technically the first 512 bytes or first sector, so I would hope that "rebuild BS" is similar.

---

### Post by meierfra. on 2008-09-21
> did some googling around, and from what I read, the NTFS initial program loader (IPL) or metadata file $Boot actually can take up to the first 16 sectors of the NTFS partition.
Yes, but I remember reading once that for XP only the first sector really matters.


> Isn't "rebuild BS" used to fix the Windows boot loader in the first 16 sectors of the partition? 

No. "rebuild BS" only changes very few numbers in the first sector.  It  makes no changes to the Window boot loader at all.  I just wrote zeroes to the first 16 sectors of my Vista partition (except I kept the first 16 bytes) After running "rebuildBS"  there were some non zero entries  in  first 80 bytes. There  also was  a "55AA" at the end of the first sector. The rest was still zero.

Before "rebuildBS"  writes the new boot sector it displays the following information:

```
filesystem size           28096512 28096512
sectors_per_cluster       8 8
mft_lcn                   786432 786432
mftmirr_lcn               1756031 1756031
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1

```

I think these are all the numbers "rebuild BS" changes. 
I assume "mft_lcn" is the location of the MFT.  So "rebuild BS" does not change the MFT put it makes sure that one can find the MFT.

---

### Post by Jonie on 2008-09-21
@caljohnsmith

Speaking from my own experience: The difference of fixboot and testdisk rebuild BS functionality also applies to fat32 volumes. Fixboot does no repair of the filesystem, it just installs Windows IPL code to the boot sector of the volume. I can speculate it's designed just to restore bootabilty if the BS is overwritten by an older version of Microsoft OS or if the volume should have been created by that OS. Testdisk does much deeper repair, yet it doesn't have the ability to install Microsoft IPL (copyright). Meierfra is right.

@TeXtonyX: 

> My thinking was that the XP OS and partition were working before the Ubuntu installation. How can Ubuntu *cause* a corruption? By overwriting the XP partition or causing a problem when grub is written to the MBR. How does Ubuntu create damage that fixboot is supposed to fix? I've seen some posts saying the problem is with Windows and some saying the problem is with grub's configuration. The normal order is fixmbr, fixboot and BOOTCFG/rebuild.

GRUB or Ubuntu will never corrupt Windows Partition PBR. NTFS is an unsupported FS and GRUB won't ever try to write to it.

So what, there is corruption, isn't it?

Yes, there is. And there is one cause of it: faulted shrinking of the (previously dirty) volume. Why does it fail then? First of all, NTFS structure is a trade secret of MSFT. Microsoft has released its own tool to shrink NTFS no sooner than with Vista. So working with NTFS is nothing more than a hack. Yes, it is reliable. As long as NTFS is clean. Working on a dirty NTFS is always a minefield. But you can't really tell if it's dirty unless you run chkdsk manually.
GParted is well capable of rebuilding PBR, but it might get confused about space allocation on the dirty NTFS volume. The difference was just 12 sectors.
Also if you clone NTFS with GParted, it just checks the dirty bit of the volume, but as opposed to XP itself it cannot rely on its journal. So provided you haven't run chkdsk previously, if the volume has some inconsistencies, the resulted copy is nothing but junk.

@meierfra:
> 
I'm not a 100% sure about it

But you're 100% right about it :)

---

### Post by caljohnsmith on 2008-09-21
Thanks meierfra and Jonie, I think I know what part of my confusion was about: to restore the NTFS boot sector with testdisk, you have to use the "Backup BS" option (which assumes the backup boot sector is OK), correct? I was getting that mixed up with the "rebuild BS" option I think.

Do either of you know what the symptoms of a bad MFT might be vs. just a bad NTFS partition boot sector? And does Microsoft's "chkdsk /r" provide the same functionality as the "repair MFT" option in testdisk? 

Thanks for all the info, I really appreciate it. :)

---

### Post by Jonie on 2008-09-21
> you have to use the "Backup BS" option (which assumes the backup boot sector is OK), correct?

Backup BS option might be useful in case you want to restore damaged BS with Windows IPL from a copy (f.ex. after power failure). Rebuild BS fixes problems caused by failed shrinking, or if the partition has been moved around the disk or restored into a different physical location.

Fixboot is really useful if the sector 0 of an NTFS volume has been overwritten (not very probable), or damaged. Even in this case you can restore backup with testdisk (assuming the backup contains valid IPL code) and then do Rebuild BS if still needed.

> Do either of you know what the symptoms of a bad MFT might be vs. just a bad NTFS partition boot sector? And does Microsoft's "chkdsk /r" provide the same functionality as the "repair MFT" option in testdisk?

Both can manifest in complete inability to mount the volume from Windows. Bad NTFS BS is essentially very much like bad superblock in Linux. Chkdsk can work as long as Windows can mount the volume. If BS has been rebuilt and the volume is still inaccessible, Repair MFT is worth a try. However bad shrinking would not rather cause the volume to be inaccessible, just not bootable. In the case of an inaccessible NTFS volume I would run a HDD diagnostic tool to find and locate and clear (possibly remap, too) the bad block, in 99.9% of cases there is one, and do a repair with testdisk as the second stage.

Chkdsk /r will fix all the problems with the filesystem except invalid "superblock" provided the volume is mountable from Windows.

A trick: old read-only Linux kernel driver could sometimes mount and access otherwise unreadable NTFS. Personally tested.

---

### Post by TeXtonyx on 2008-09-21
meierfra wrote: "I assume "mft_lcn" is the location of the MFT. So "rebuild BS" does not change the MFT put it makes sure that one can find the MFT.

file:///home/stephen/Documents/testdisk-6.10/doc/advanced_ntfs_boot_and_mft_repair.html
  
Repair NTFS MFT
The MFT (Master File Table) is sometimes corrupted. If Microsoft Check Disk (chkdsk) failed to repair the MFT, run TestDisk and in the Advanced menu, select your NTFS partition and choose Repair MFT. TestDisk will try to repair the MFT using MFT mirror, its backup. [but doesn't create a new MFT]
I found your remarks, meierfra, most edifying.

---

