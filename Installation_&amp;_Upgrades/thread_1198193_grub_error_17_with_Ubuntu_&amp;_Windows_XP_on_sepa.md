---
title: "grub error 17 with Ubuntu &amp; Windows XP on separate HDD"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by HolgerBurghardt on 2009-06-27
Hello,

in short words an introduction: I'm new to Linux, new to Ubuntu & new to UbuntuForums.org - I did search for my problem both on UbuntuForums.org and the internet in general, but what I found was usually off by one bit of detail. I'll come to that later.

**Problem**
*Original State of Things, or When Everything Was Working Alright*
I have a PC with an Intel DuoCore and originally had a 750GB SATA HDD on which I had three partitions. I run Windows XP HE on the first, the two other NTFS partitions were for data storage. Eventually that drive showed signs of corruption, so I bought a WD SATA HDD with 1TB - on which I created again three partitions and installed again Windows XP HE. (Btw, I used EASEUS Partition Manager 4.01 HE for the partitions.)

*The Change, or What I Did to Create the Problem*
Now, a friend gave me a 15GB IDE HDD which I installed. Now I decided to install Ubuntu 9.04 on that drive. I used the original desktop download from Ubuntu.com and used the build-in partitioning program to format and partition the drive.

*The Error, or What Is the Actual Problem Now*
Once installation was complete, I was asked to remove the disk and to reboot the system. When the PC passed the BIOS tests, GRUB would start loading and then display the following message:

```
GRUB Loading stage 1.5
 
 
GRUB loading, please wait ...
Error 17
```And that's it. No further action possible. I believe you can guess already that I can't start neither Windows nor Ubuntu.

**Solution Wanted**
Most solutions I found were meant for cases where Ubuntu and Windows are installed on the same HDD. I am not sure whether these apply.
I run fdisk on my LiveCD of Ubuntu (it's in German but you should get the idea):

```
ubuntu@ubuntu:~$ sudo fdisk -l

Platte /dev/sda: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spuren, 121601 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x21e621e5

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        8029    64492911    7  HPFS/NTFS
/dev/sda2            8030       60245   419425020    7  HPFS/NTFS
/dev/sda3           60246       69384    73409017+   7  HPFS/NTFS
/dev/sda4           69385      121601   419433052+   7  HPFS/NTFS

Platte /dev/sdb: 750.1 GByte, 750156374016 Byte
255 Köpfe, 63 Sektoren/Spuren, 91201 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xcdb6cdb6

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               2       12876   103418437+   f  W95 Erw. (LBA)
/dev/sdb2   *       12877       65093   419433052+   7  HPFS/NTFS
/dev/sdb3           65094       91201   209712510    7  HPFS/NTFS
/dev/sdb5               2       12876   103418406    7  HPFS/NTFS

Platte /dev/sdc: 15.0 GByte, 15020457984 Byte
255 Köpfe, 63 Sektoren/Spuren, 1826 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x802b81ca

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdc1               1        1744    14008648+  83  Linux
/dev/sdc2            1745        1826      658665    5  Erweiterte
/dev/sdc5            1745        1826      658633+  82  Linux Swap / Solaris

```

---

### Post by merlinus on 2009-06-27
Mount your linux partition from the live cd, and post results of

```

cat /boot/grub/menu.lst

```You can also try using supergrub to boot both oses, and fix the problem.  Good info here:

[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html]("http://members.iinet.net.au/%7Eherman546/SuperGrubDiskPage.html")

---

### Post by HolgerBurghardt on 2009-06-27
```
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
```

:(

---

### Post by merlinus on 2009-06-27
Did you mount your linux partition by clicking on it in nautilus?

Here is info about grub error 17:

[http://members.iinet.net.au/~herman546/p15.html#17]("http://members.iinet.net.au/%7Eherman546/p15.html#17")

also, no colon after cat.

cat /boot/grub/menu.lst

---

### Post by HolgerBurghardt on 2009-06-27
Or maybe I missed something: mounting Linux?

---

### Post by HolgerBurghardt on 2009-06-27
What's a nautilus? I am sorry - I used some Linux before, but the whole (un)mounting business... I don't know anything about it. As I indicated before, I am totally new to Linux, which won't change until I can install a linux distro.

---

### Post by merlinus on 2009-06-27
Nautilus is the file manager and browser.  You should be able to access it from Places in the top menu, and it should show your ubuntu partition.  Clicking on the partition name will mount it.  Or maybe Computer?

---

### Post by HolgerBurghardt on 2009-06-27
Still, I opened the file *menu.lst* with Ubuntu's text editor and copied the following stuff, in case that's what you needed.

```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        XXX
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=XXX ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        XXX
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=XXX ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        XXX
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```

Just in case I replaced the UUID with XXX

---

### Post by merlinus on 2009-06-27
You will notice at the end of menu.lst that there are two windows entries.  One points to sda1 (hd0,0) and the other to sdb2 (hd1,1).  Delete whichever one is incorrect, save the file and restart.

To edit and be able to save it, you will need to enter this command in a terminal:

```

gksudo gedit /boot/grub/menu.lst

```

---

### Post by HolgerBurghardt on 2009-06-27
Okay, I got it. The name Nautilus does not appear unless I look up the *Info* in the menu. I used to GNOME-Terminal for [FONT=Courier New]cat /boot/grub/menu.lst but maybe I need to change the directory?[/FONT]

---

### Post by HolgerBurghardt on 2009-06-27
If I use gedit the file shows up empty inside. :confused:

---

### Post by merlinus on 2009-06-27
That is because it is not loading the one from your ubuntu partition.

---

### Post by merlinus on 2009-06-27
You can try this to reinstall grub so at least you can boot ubuntu.

From the live cd, open a terminal and enter these commands one at a time, pressing Enter after each:

```

sudo grub
root (hd2,0)
setup (hd0)
quit

```

and restart.

---

### Post by HolgerBurghardt on 2009-06-27
Okay, I manually deleted the second Windows from menu.lst so it reads now

```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        XXX
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=XXX ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        XXX
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=XXX ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        XXX
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```

I did reboot, but still get the same GRUB error 17 as before.

---

### Post by merlinus on 2009-06-27
Try reinstalling grub, as indicated in my previous post.

---

### Post by HolgerBurghardt on 2009-06-27
But reinstalling GRUB won't let me start Windows XP (which still has to remain my primary OS)?

---

### Post by merlinus on 2009-06-27
Please try it, or else use supergrub to boot windows.

---

### Post by HolgerBurghardt on 2009-06-27
Okay thanks - I'll try it now.

---

### Post by merlinus on 2009-06-27
If reinstalling grub did not work, then the last thing I can think of is that the UUIDs changed.  You can find out what they are by this:

```

sudo blkid

```

Compare the results with the listings in menu.lst, and change them if they are incorrect.

Beyond that, you can use your xp cd to fixboot or fixmbr by selecting recovery (or repair) from the opening menu.  That will allow you to boot directly to xp, and you can fix the grub problem later.

---

### Post by HolgerBurghardt on 2009-06-27
Just so you know, I really appreciate your help.

Okay, reinstalling GRUB did not help and the UUID is correct. So I guess that leaves SuperGrub and Windows XP repair. Is it sound to say that I can repair the MBR first with WinXP and then use SuperGrub later to create a bootloader for both OS?

---

### Post by merlinus on 2009-06-27
Yes, since xp is your primary os.  Good luck, and please let me know how it all turns out.

---

### Post by HolgerBurghardt on 2009-06-27
Thanks again, Merlinus, and I'll post my answer here, so this thread will have a positive conclusion (aside the positive fact of getting help easily).

---

### Post by merlinus on 2009-06-27
One more thought -- you might check the boot order of your hdds in bios.

---

### Post by HolgerBurghardt on 2009-06-27
Unfortunately I already thought of that. It's OpticalDrive first, then HDD-1TB (or sda), then HDD-15GB (or sdc). The HDD-750GB (or sdb) that will be sooner or later removed, is already out of the boot loop.

Btw, I looked up SuperGrub. It says it's easy, but I hope my case (two OS on two separate HDD) can be addressed. (As always, everybody assumes that you install the two OS on the same HDD).

---

### Post by HolgerBurghardt on 2009-06-27
I was reading a bit on the forum and reviewed the *menu.lst* file. That got me thinking. Maybe Merlin's idea of the boot order does merrit a try by changing the boot order so the linux harddrive comes after the optical drive but before the windows harddrive? :-k

---

### Post by presence1960 on 2009-06-27
> **HolgerBurghardt said:**
> I was reading a bit on the forum and reviewed the *menu.lst* file. That got me thinking. Maybe Merlin's idea of the boot order does merrit a try by changing the boot order so the linux harddrive comes after the optical drive but before the windows harddrive? :-k

that should do the trick, then you may have to change the windows entry in menu.lst. Just note the order of your drives in BIOS after you set the Ubuntu drive to first hard drive to boot. Remember when changing your entry in menu,lst that numbering for hard disks & partitions start at 0. first hard disk is (hd0), first partition on first disk is (hd0,0), second partition on first disk is (hd0,1). Second hard disk is (hd1), first partition on second disk is (hd1,0) etc.

You will need the map lines in there which should correspond to your linux hard disk & Windows hard disk. This is because windows resides on a different hard disk than Linux. Give it a whirl and let us know how it turns out.

example: 
> title		Microsoft Windows 7 RC
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

windows is on second disk to boot (hd1) and linux is on first hard disk to boot (hd0)

---

### Post by HolgerBurghardt on 2009-06-27
Okay, first I thank you again.

Second I have to admit that I am an idiot. Merlin, I think, was onto some great idea. My BIOS recognizes my IDE drive (the one with Ubuntu on it) but does not allow it to be used as a boot drive. When I gave the boot order earlier I did not specifically check it, I just remember having seen my IDE drive in the ASUS BIOS. ](*,)

I have a strong hunch that therein lies the reason for my problem. I'm going to try and find a solution to this issue, but should someone of you habe one, I'd be much obliged. My motherboard is a ASUS P5K SE. I remember reading a while ago that one needs to do something about IDE drives but I don't remember where and what it said exactly. #-o

I am sorry not to have seen this before but while Windows XP ran I could see the IDE drive and using the Ubuntu live CD I could naturally mount the drive too, so I didn't think of that. :oops:

---

### Post by Bearly Able on 2009-06-27
Someone may have a better solution to your problem, but if not, I think this should work.

When I installed Ubuntu as a dual boot with XP, using separate hard drives, I was unable to load Windows from GRUB.  With expert help, I got the system up and running with Windows loading GRUB, rather than the other way around.  You should be able to use the same system, as you can boot from your Windows drive.

The thread with the instructions is [here]("http://ubuntuforums.org/showthread.php?t=1060203").  At the start, we were trying to boot Windows from GRUB; the instructions to do it the other way around begin at #13, and I'm sure you'll find it easy to follow.

Hope this helps!

---

### Post by HolgerBurghardt on 2009-06-27
Okay, couldn't find yet a solution to get my BIOS boot from an IDE drive. Some say it's the motherboard having trouble with those ancient IDE drives (and ancient it is), some others say the drive needs to be jumpered - some say as master, a few say as slave etc. etc.

So I used XP's repair console, [FONT=Courier New]fixmbr [/FONT]so at least I can use Windows again.

Now I'll try Lesley's suggestion. I'll keep you informed...

---

### Post by HolgerBurghardt on 2009-06-27
Okay, I downloaded the bootpart program and run it.

```
G:\Dokumente und Einstellungen\Holger Burghardt\Desktop>bootpart
Boot Partition 2.60 for WinNT/2K/XP (c)1995-2005 G. Vollant (info@winimage.com)
WEB : http://www.winimage.com and http://www.winimage.com/bootpart.htm
Add partition in the Windows NT/2000/XP Multi-boot loader
Run "bootpart /?" for more information

Physical number of disk 0 : 21e621e5
 0 : C:* type=7  (HPFS/NTFS), size= 64492911 KB, Lba Pos=63
 1 : C:  type=7  (HPFS/NTFS), size= 419425020 KB, Lba Pos=128985885
 2 : C:  type=7  (HPFS/NTFS), size= 73409017 KB, Lba Pos=967835925
 3 : C:  type=7  (HPFS/NTFS), size= 419433052 KB, Lba Pos=1114653960
Physical number of disk 1 : cdb6cdb6
 4 : D:  type=f  (Win95 XInt 13 extended), size= 103418437 KB, Lba Pos=16065
 5 : D:  type=7   (HPFS/NTFS), size= 103418406 KB, Lba Pos=16128
 6 : D:* type=7  (HPFS/NTFS), size= 419433052 KB, Lba Pos=206852940
 7 : D:  type=7  (HPFS/NTFS), size= 209712510 KB, Lba Pos=1045719045
Physical number of disk 2 : 802b81ca
 8 : E:  type=83  (Linux native), size= 14008648 KB, Lba Pos=63
 9 : E:  type=5  (Extended), size= 658665 KB, Lba Pos=28017360
10 : E:  type=82   (Linux swap), size= 658633 KB, Lba Pos=28017423
```

Using what Subhash said on [http://www.vsubhash.com/writeups/multiboot_os.asp](http://www.vsubhash.com/writeups/multiboot_os.asp) I created a file using [FONT=Courier New]bootpart 8 ubuntu.lnx Ubuntu[/FONT] and added the line *G:\ubuntu.lnx="Ubuntu"* to boot.ini - now we'll see what's going to happen!

---

### Post by HolgerBurghardt on 2009-06-27
Okay, nothing happened... Unless someone has another idea, I'll ask some of my colleagues. Some know Linux, some have been IT maintenance guys before. Together we might find a solution which I'll post here.

---

### Post by Bearly Able on 2009-06-28
I'm no expert here, and may be barking up the wrong tree, but it looks to me as if you have no boot partition on your Linux drive.  Presumably in your original install, GRUB was installed on your Windows drive, and restoring the Windows boot menu has overwritten that.  There should be an asterisk marking the boot partition in your bootpart results, and I don't see one.  #8 in the instructions caljohnsmith gave me says:

> ```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> setup (hd1)
grub> quit
```

That should install Grub to the MBR of your Ubuntu drive.

I think you'll need to substitute hd2 for hd1.

However, when we decided to use Windows to boot Ubuntu, that changed to:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1,0)
grub> quit
```(post #15), so I guess you should just start with that, again substituting hd2 for hd1.

As I say, I'm no expert, but I think that should do it.

---

### Post by presence1960 on 2009-06-28
ok. i just noticed an earlier post where you said your BIOS boot order for HDD is sda, sdc & sdb. This changes everything. Sometimes Ubuntu & BIOS read drive order differently, hence your sudo fdisk has the order as sda, sdb & sdc. So when you ran the commands to reinstall GRUB it got installed onto the wrong HDD. Give this a whirl:

```

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
5. Type "root (hd1,0)
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

Then edit your windows entry in menu.lst to look like this:
```
title          Microsoft XP Home Edition
rootnoverify   (hd0,0)
map            (hd1) (hd0)
map            (hd0) (hd1)
chainloader    +1
```

The reason you are getting a GRUB error 17 is your GRUB is pointing to your sdb drive which is actually the 3rd drive in your BIOS. When you ran sudo grub and set it up on hd2 you thought it went onto sdc, but it didn't because sdc is set to second boot in BIOS. You would have needed (hd1) in that command. I know you said you checked your boot order in BIOS, but maybe it didn't click that it is different in order from your sudo fdisk -l output.

---

### Post by presence1960 on 2009-06-28
> **Lesley Lutomski said:**
> I'm no expert here, and may be barking up the wrong tree, but it looks to me as if you have no boot partition on your Linux drive.  Presumably in your original install, GRUB was installed on your Windows drive, and restoring the Windows boot menu has overwritten that.  There should be an asterisk marking the boot partition in your bootpart results, and I don't see one.  #8 in the instructions caljohnsmith gave me says:

Lesley actually you are correct, but your terminology is incorrect. he does not have a boot partition, but he has a boot directory. What I believe you mean is that GRUB is not installed to the Ubuntu partition of the correct drive. If he had no boot directory he would have no menu.lst as that is where it is located - /boot/grub/menu.lst. It looks like he installed GRUB to the sdb drive(which doesn't have Ubuntu) and to MBR of the windows disk. So when he boots his windows disk is first in HDD boot order, GRUB takes over and points to sdb which does not have Ubuntu on it. Hence the GRUB error 17 which from the GRUB manual is explained this way:  : Cannot mount selected partition. This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

it is expecting a linux filesystem but that drive is all NTFS partitions. The fix above should install GRUB to Ubuntu partition and to MBR.

P.S. here is the link to the GRUB manual : [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by presence1960 on 2009-06-28
Let me illustrate by showing my fdisk output:
```
raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        4569    36596736    7  HPFS/NTFS
/dev/sda3            4570       29879   203302575   83  Linux
/dev/sda4           29880       30401     4192965   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14519   116623836   83  Linux
/dev/sdb2           14520       16477    15727635   83  Linux
/dev/sdb3           16478       19457    23936850    b  W95 FAT32
raz@raz-desktop:~$ 
```
sda1 is win7 boot, sda2 is windows 7, sda3 is ubuntu /home. sdb2 is Jaunty 9.04

Here is my menu.lst, notice my windows entry:
```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 7 RC
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1
```

notice windows is (hd1,0) How can that be if fdisk says it is sda1? Because in BIOS my boot order of my HDDs is sdb then sda. The same situation appears to be the OPs case as his boot order in BIOS is sda, sdc then sdb, which makes sda (hd0) sdc (hd1) and sdb (hd2).

---

### Post by HolgerBurghardt on 2009-06-28
Okay, right now I have a bit of a problem following you.

Since you've repeated something I wrote earlier but corrected later, let me restate the facts.

I have three HDD drives. Two are connected via SATA to my motherboard (a ASUS P5K SE), one through traditional IDE with jumper setting not verified (as I asked a colleague and he said if it's the only IDE it's not necessary).

My 1TB-SATA drive is split into four NTSF partitions, on the first I have installed Windows XP HE.

My 750GB-SATA drive is split into three NTSF partitions, on the first I have installed Windows XP HE too. This drive will eventually be removed as it is facing breakdown.

My 15GB-IDE drive is the one where I installed Ubuntu using the official LiveCD, thus creating two partitions, the system and the swap partition.

The BIOS can identify all drives, but not for boot order. There the IDE drive does not show up. So the boot order is:

[LIST=1]
[*]Optical drive (from LG)
[*]1TB-SATA drive
[*]empty
[/LIST]
Presently my fdisk output show
```
ubuntu@ubuntu:~$ sudo fdisk -l

Platte /dev/sda: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spuren, 121601 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x21e621e5

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        8029    64492911    7  HPFS/NTFS
/dev/sda2            8030       60245   419425020    7  HPFS/NTFS
/dev/sda3           60246       69384    73409017+   7  HPFS/NTFS
/dev/sda4           69385      121601   419433052+   7  HPFS/NTFS

Platte /dev/sdb: 750.1 GByte, 750156374016 Byte
255 Köpfe, 63 Sektoren/Spuren, 91201 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xcdb6cdb6

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               2       12876   103418437+   f  W95 Erw. (LBA)
/dev/sdb2   *       12877       65093   419433052+   7  HPFS/NTFS
/dev/sdb3           65094       91201   209712510    7  HPFS/NTFS
/dev/sdb5               2       12876   103418406    7  HPFS/NTFS

Platte /dev/sdc: 15.0 GByte, 15020457984 Byte
255 Köpfe, 63 Sektoren/Spuren, 1826 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x802b81ca

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdc1               1        1744    14008648+  83  Linux
/dev/sdc2            1745        1826      658665    5  Erweiterte
/dev/sdc5            1745        1826      658633+  82  Linux Swap / Solaris
```

My menu.lst is as follows
```
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        60b1de8f-2741-4b4f-b2bb-05ab541c990b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=60b1de8f-2741-4b4f-b2bb-05ab541c990b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        60b1de8f-2741-4b4f-b2bb-05ab541c990b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=60b1de8f-2741-4b4f-b2bb-05ab541c990b ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        60b1de8f-2741-4b4f-b2bb-05ab541c990b
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```

I opened GRUB using [FONT=Courier New]sudo grub[/FONT] and entered [FONT=Fixedsys]find /boot/grub/stage1[/FONT] and it gave as result (hd2,0).

---

### Post by presence1960 on 2009-06-28
> **HolgerBurghardt said:**
> Okay, right now I have a bit of a problem following you.

Since you've repeated something I wrote earlier but corrected later, let me restate the facts.

I have three HDD drives. Two are connected via SATA to my motherboard (a ASUS P5K SE), one through traditional IDE with jumper setting not verified (as I asked a colleague and he said if it's the only IDE it's not necessary).

My 1TB-SATA drive is split into four NTSF partitions, on the first I have installed Windows XP HE.

My 750GB-SATA drive is split into three NTSF partitions, on the first I have installed Windows XP HE too. This drive will eventually be removed as it is facing breakdown.

My 15GB-IDE drive is the one where I installed Ubuntu using the official LiveCD, thus creating two partitions, the system and the swap partition.

The BIOS can identify all drives, but not for boot order. There the IDE drive does not show up. So the boot order is:

[LIST=1]
[*]Optical drive (from LG)
[*]1TB-SATA drive
[*]empty
[/LIST]
Presently my fdisk output show
```
ubuntu@ubuntu:~$ sudo fdisk -l

Platte /dev/sda: 1000.2 GByte, 1000204886016 Byte
255 Köpfe, 63 Sektoren/Spuren, 121601 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x21e621e5

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        8029    64492911    7  HPFS/NTFS
/dev/sda2            8030       60245   419425020    7  HPFS/NTFS
/dev/sda3           60246       69384    73409017+   7  HPFS/NTFS
/dev/sda4           69385      121601   419433052+   7  HPFS/NTFS

Platte /dev/sdb: 750.1 GByte, 750156374016 Byte
255 Köpfe, 63 Sektoren/Spuren, 91201 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xcdb6cdb6

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               2       12876   103418437+   f  W95 Erw. (LBA)
/dev/sdb2   *       12877       65093   419433052+   7  HPFS/NTFS
/dev/sdb3           65094       91201   209712510    7  HPFS/NTFS
/dev/sdb5               2       12876   103418406    7  HPFS/NTFS

Platte /dev/sdc: 15.0 GByte, 15020457984 Byte
255 Köpfe, 63 Sektoren/Spuren, 1826 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x802b81ca

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdc1               1        1744    14008648+  83  Linux
/dev/sdc2            1745        1826      658665    5  Erweiterte
/dev/sdc5            1745        1826      658633+  82  Linux Swap / Solaris
```

My menu.lst is as follows
```
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        60b1de8f-2741-4b4f-b2bb-05ab541c990b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=60b1de8f-2741-4b4f-b2bb-05ab541c990b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        60b1de8f-2741-4b4f-b2bb-05ab541c990b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=60b1de8f-2741-4b4f-b2bb-05ab541c990b ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        60b1de8f-2741-4b4f-b2bb-05ab541c990b
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```

I opened GRUB using [FONT=Courier New]sudo grub[/FONT] and entered [FONT=Fixedsys]find /boot/grub/stage1[/FONT] and it gave as result (hd2,0).
Ok I didn't see the correction, but obviously the problem is your IDE disk is not in the boot order so that can be the problem. Why don't you try installing Ubuntu on one of the other disks that BIOS recognizes in Boot Order settings. 
BTW my sdb is an IDE Seagate HDD but it shows in my BIOS. There has to be a way to get your sdc to show in BIOS, maybe a BIOS upgrade? Check your mobo manufacturer's web site.

---

### Post by HolgerBurghardt on 2009-06-28
I am not so sure about installing it on the same drive as Windows XP (my first SATA drive) and the other drive is practically as good as out.

I wonder why my IDE drive does not show up for the boot order? (I just wonder, I don't expect an answer to this on an Ubuntu forum!  :-\" )

---

### Post by Bearly Able on 2009-06-28
Thanks for the explanation, presence1960.  I'm trying to get to grips with correct terminology, but it's a steep learning curve.

I have GRUB installed on my Ubuntu drive and LILO on my Windows drive, so both show up as having boot info.

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfbc4fbc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sda2            4463       19457   120447337+   f  W95 Ext'd (LBA)
/dev/sda5            4463        8295    30788541    7  HPFS/NTFS
/dev/sda6            8296       12416    33101901    7  HPFS/NTFS
/dev/sda7           12417       16600    33607948+   7  HPFS/NTFS
/dev/sda8           16601       19457    22948821    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ec031

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18702   150223783+  83  Linux
/dev/sdb2           18703       19457     6064537+   5  Extended
/dev/sdb5           18703       19457     6064506   82  Linux swap / Solaris

```

I'd also missed the issue of the OPs boot order when looking at this.

---

### Post by Bearly Able on 2009-06-28
OK, I'm probably missing something again, but would my setup not work here?  BIOS boots from my Windows hard drive, but the entry for Ubuntu in the Windows boot menu points to GRUB on the second hard drive.

If the OP's BIOS can boot the Windows drive, surely it doesn't matter that BIOS won't recognise the Ubuntu IDE drive?

---

### Post by presence1960 on 2009-06-28
lesley, My Ubuntu (sdb2) does not have a boot flag, it isn't necessary in most cases for ubuntu. But keep learning & trying to help others. The only way to increase your knowledge is to roll up your sleeves and get in there.
Don't worry about making incorrect statements, we all do at one time or another. most in here will set you straight without putting you down by sharing the facts with you.

---

### Post by Bearly Able on 2009-06-28
Thanks again.  I know my setup isn't usually necessary, but it was the only one that works for me, and it seems to me it would work here for the OP, because then he can boot from his Ubuntu drive without having to worry about getting the BIOS to recognise it.

---

### Post by presence1960 on 2009-06-28
> **Lesley Lutomski said:**
> OK, I'm probably missing something again, but would my setup not work here?  BIOS boots from my Windows hard drive, but the entry for Ubuntu in the Windows boot menu points to GRUB on the second hard drive.

If the OP's BIOS can boot the Windows drive, surely it doesn't matter that BIOS won't recognise the Ubuntu IDE drive?

His machine is booting from the windows drive, GRUB is installed to MBR of the windows drive and points to the Ubuntu partition on the IDE drive. When GRUB in the MBR executes it looks for the menu.lst in the IDE drive. Since that drive is not recognized by BIOS it will not boot, thus the error.

If you did it your way the windows bootloader would take over. When he chooses Ubuntu it will have to point to the Ubuntu partition on the IDE drive. More specifically it will look for menu.lst on the Ubuntu partition. This will have the same result, because BIOS does not recognize the drive. Read this on BIOS : [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

If BIOS will not recognize his IDE drive, it does not matter which bootloader points to it.

---

### Post by Bearly Able on 2009-06-29
Thanks yet again for the explanation.  I'm getting there slowly.

---

### Post by HolgerBurghardt on 2009-06-29
Well, I was "watching" you two guys a while from afar. ;)

It looks like I need my BIOS to recognize the IDE drive. Since I don't seem to find a solution to that problem, I'm going to do what I wanted to avoid for now, i.e. I'll install Ubuntu on my principal harddrive.

This time this shouldn't pose any problems, no matter that the Windows system drive is numbered G (instead of the usual C).

Since I read that GRUB does not support changes in the partition structure, I'm inclined to ask whether the boot order should always remain the same after that and whether changing the Ubuntu install (updating to Ubuntu Studio and changing to KDE, which ever comes first, based on suggestions I'm going to search for in this forum) will affect GRUB?

---

