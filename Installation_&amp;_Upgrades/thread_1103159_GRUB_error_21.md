---
title: "GRUB error 21"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by chippies on 2009-03-22
Hey guys,

I've got 8.10 installed on my Dell XPS M1330 laptop. My video card hit the fan, and I got the white lines on my screen and could not boot. Contacted Dell and it they seem to also think it's a burnt out vid card. So I wanted to back up my data before I sent the notebook in. I took my HDD out of the notebook, and plugged it into an external enclosure I have. I tried plugging it into my girlfriends Vista machine, and it would not detect the drive (sys tray showed the USB device, and I could unmount it, but I could not access the drive). I then tried it on my work laptop (XP) and had similar results. After I plugged the HDD back into my Dell notebook (only Ubuntu installed, not a dual-boot) it magically worked. The video card, not the HDD. When I booted I got GRUB error loading 15. After messing around and poking around the super grub boot disk utility, I managed nothing other than changing the error to 21. 

All I want to do is access my files and copy them to an external drive, I don't care about the install and I'm willing to wax the whole drive (and actually would like to do that before sending back to Dell). I just REALLY want to retrieve my files, as I can't access them!

Can someone assist me in either retrieving the files through a live-cd boot, or perhaps modifying my MBR so that I can boot my install?

Thanks guys. I've been searching for two days now on this forum and on google, and have had no luck thus far.

---

### Post by upchucky on 2009-03-22
just send the pc to dell without the drive, they have their own live cds to test the system, they do not need a hard drive to fix the video. I took my hard drive out of my xps laptop when they replaced my screen under warranty.

now did you use a live cd to boot the machine? did the vid results do the same? if yes then the card is probably the problem.

if ubuntu 8.04 or knoppix boots up a graphics display then the vid card is ok, and some setting is messed up. probably in the xorg.conf file.

If the pc has an Nvidia card, Ubuntu 8.10 has some problem with nvidia card, there are workarounds for this, but you need a functional commandline ubuntu install to do the workaround.

if you want to back up the drive, you need either another ubuntu machine or a live cd like Knoppix, either will read/write the drive and let you back up to another storage media.

windows can not read linux.

to fix grub mbr, download this:

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then do this

   sudo bash ~/Desktop/boot_info_script*.sh   

post the results here and some well learned people can tell you exactly what to do to fix mbr

---

### Post by chippies on 2009-03-22
> **upchucky said:**
> just send the pc to dell without the drive, they have their own live cds to test the system, they do not need a hard drive to fix the video. I took my hard drive out of my xps laptop when they replaced my screen under warranty.
That sounds good, I'm glad to hear that I'm able to do that.

> now did you use a live cd to boot the machine? did the vid results do the same? if yes then the card is probably the problem.
Yes, I used the livecd to boot, and the livecd ubuntu functioned fine. The real kicker is, I tried to boot the computer without the livecd and the graphics looked fine, judging from only the GRUB error that displays. It seems as though graphical errors have ceased. That being said, I did just recently install the beta nvidia driver, so a xorg.conf file setting error could be the suspect, as you've suggested. 

> if you want to back up the drive, you need either another ubuntu machine or a live cd like Knoppix, either will read/write the drive and let you back up to another storage media.
Could this be done by taking the HDD out of the laptop, putting it in an enclosure, and then booting with the livecd, then accessing the drive on the USB enclosure?

> 
windows can not read linux.
to fix grub mbr, download this:
[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 
then do this
   sudo bash ~/Desktop/boot_info_script*.sh 
post the results here and some well learned people can tell you exactly what to do to fix mbr

OK, here ya go:

ubuntu@ubuntu:~$ sudo bash /home/ubuntu/Desktop/boot_info_script28*.sh 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Desktop

```

============================= Boot Info Summary: ==============================

 => Grub0.97-os.1 is installed in the MBR of /dev/sda and looks on boot drive 
    #2 in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /bootmgr /BOOTMGR /ntldr /NTLDR 
                       /NTDETECT.COM /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b3a73

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    483,153,920   488,394,751     5,240,832   c W95 FAT32 (LBA)
/dev/sda2         470,158,290   488,392,064    18,233,775   5 Extended
/dev/sda5         470,158,353   488,392,064    18,233,712  82 Linux swap / Solaris

/dev/sda1 overlaps with /dev/sda2
/dev/sda1 overlaps with /dev/sda5

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="MEDIADIRECT" UUID="54BD-4638" TYPE="vfat" 
/dev/sda5: UUID="3217f915-608e-475b-a097-235ccc08fb1b" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768


```

---

### Post by upchucky on 2009-03-22
yes you can place the drive in a separate enclosure and read/write it from a live cd.


it looks like the /boot/grub/menu.lst file is missing

check to see if it was saved as /boot/grub/menu.lst.bac or something like that. it needs to be restored to boot/grub

be careful tho, perhaps wait for someone to post the exact way to do this,

I can repair the machines, but my weakness is exact commands for software.

---

### Post by FrostDust on 2009-03-22
> **chippies said:**
> I took my HDD out of the notebook, and plugged it into an external enclosure I have. I tried plugging it into my girlfriends Vista machine, and it would not detect the drive (sys tray showed the USB device, and I could unmount it, but I could not access the drive). I then tried it on my work laptop (XP) and had similar results.
...
All I want to do is access my files and copy them to an external drive, I don't care about the install and I'm willing to wax the whole drive (and actually would like to do that before sending back to Dell). I just REALLY want to retrieve my files, as I can't access them!

Install ext2ifs: [http://www.fs-driver.org](http://www.fs-driver.org). It's a Windows driver that lets you access ext2 and, therefore, ext3 file systems. In most situations, ext3 is the default file system for Linux installs, so I presume it'd work for you.

Install it to a Windows system, and then mount your hard drive in your USB enclosure like before, and you'd be able to browse it like any other hard drive. This should let you then copy the data you want to save to your Windows machine, burn the data to a disc, or whatever you'd want to do.

---

### Post by meierfra. on 2009-03-22
> ```
dev/sda1    *    483,153,920   488,394,751     5,240,832   c W95 FAT32 (LBA)
/dev/sda2         470,158,290   488,392,064    18,233,775   5 Extended
/dev/sda5         470,158,353   488,392,064    18,233,712  82 Linux swap / Solaris
```

Your partition table is messed up. Your Ubuntu partition does not even appear.

If you are lucky, you just need to fix your partition table:

Boot your Live CD, download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static  /dev/sda

```

After starting testdisk with the above command, choose
  "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and more importantly,

---

### Post by chippies on 2009-03-23
> **meierfra. said:**
> Please post the output of the screen that has the deep search results.

OK, see below.

> please let me know exactly which partitions give you a directory listing, and more importantly,

Umm, I may not be an English major, but I believe that last sentence is a trail off. Normally that wouldn't bother me, but the fact that the sentence ends off on "and more importantly," kind of freaks me out. I hope you didn't leave out anything important!

Anyways, here's what's being displayed below the status of the deeper scan:

```

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
P Linux                    0   1  1 29265 254 60  470158224
P Linux Swap           29266   1  1 30400 254 47   18233696
P FAT32 LBA            30074 239 54 30401  42 41    5240832 [MEDIADIRECT]


```

When I highlight each item in the list (after making sure a 'P' appears next to the item) the following information shows up (in respect to the order above)

```

Structure: Bad. Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT3 Large file Sparse superblock Recover, 240 GB / 224 GiB


Structure: Bad. Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, 
     Enter: to continue
SWAP2 version 1, 9335 MB / 8903 MiB


Structure: Bad. Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT32, 2683 MB / 2559 MiB

```

---

### Post by meierfra. on 2009-03-23
> the sentence ends off on "and more importantly,

Sorry, I had copied and pasted the text from a similar thread, and it seems I missed the last line.



What is supposed to be on the drive?
It looks like you had partition for Ubuntu and a swap partition. 
The Media Direct partitions seems to be left over from the time before your installed Ubuntu. 
Is that right?

If that is correct, select the "Swap" partition. Then use the  "left arrow" key so that the "D" at the beginning of the "swap" line turns into an "L". (if testdisk does not let you choose an "L" choose "P" instead).


Then press "enter" to continue. Choose "write" and then press "Y" to confirm.   Then press "q" a few times to quit testdisk. 
Hopefully this will have restored the correct partition table.

---

### Post by meierfra. on 2009-03-23
I hadn't seen your edit, when I posted  my last post. Anyway, go ahead with my instruction. But it looks like you will have some more work to do after the partition table is restored.

---

### Post by meierfra. on 2009-03-23
Hold on for a second.

---

### Post by chippies on 2009-03-23
> **meierfra. said:**
> What is supposed to be on the drive?
It looks like you had partition for Ubuntu and a swap partition. 
The Media Direct partitions seems to be left over from the time before your installed Ubuntu. 
Is that right?
The computer shipped with Vista on it. I booted the machine up, made sure it worked, then formatted and installed Ubuntu (7.04 at the time, I believe). As far as I know, the HDD should only have one partition, and that's for Ubuntu (I don't dual boot).

Given the above information, should I proceed with the following:

> If that is correct, select the "Swap" partition. Then use the  "left arrow" key so that the "D" at the beginning of the "swap" line turns into an "L". (if testdisk does not let you choose an "L" choose "P" instead).

Then press "enter" to continue. Choose "write" and then press "Y" to confirm.   Then press "q" a few times to quit testdisk. 
Hopefully this will have restored the correct partition table.

For the record, when I highlight the swap and choose D and L, the follow displays below, respectively

```
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, 
     Enter: to continue
SWAP2 version 1, 9335 MB / 8903 MiB
```
```
Structure: Bad. Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, 
     Enter: to continue
SWAP2 version 1, 9335 MB / 8903 MiB

```

THANK YOU SO MUCH! I am still very very new, and not entirely comfortable with ubuntu yet, but I'm getting there. I just want to make sure I don't accidently (further) compromise my files.

---

### Post by meierfra. on 2009-03-23
I just noticed that you put "P" in the  beginning of each line.

Instead:

*  for the first line (the Ubuntu partition)
L  for the second line (the swap partition ) (but choose "P" if "L" is not possible.)
D  for the last line (I think the media direct partition is just a left over, since its overlaps with the swap partition)


Then you can  press "enter" and continue with the rest of the instruction.

---

### Post by chippies on 2009-03-23
> **meierfra. said:**
> I just noticed that you put "P" in the  beginning of each line.

Instead:

*  for the first line (the Ubuntu partition)
L  for the second line (the swap partition ) (but choose "P" if "L" is not possible.)
D  for the last line (I think the media direct partition is just a left over, since its overlaps with the swap partition)


Then you can  press "enter" and continue with the rest of the instruction.

Alright, choosing *, L, and D was allowed. I pressed enter and following is displayed
```
Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63

     Partition                  Start        End    Size in sectors

 1 * Linux                    0   1  1 29265 254 60  470158224
 2 E extended LBA         29266   0  1 30400 254 63   18233775
 5 L Linux Swap           29266   1  1 30400 254 47   18233696


[  Quit  ]  [ Write  ]  [Extd Part]

```
Am I looking to 'Write', or 'maximize/minimize extended partition" ?

---

### Post by meierfra. on 2009-03-23
"Write"

---

### Post by chippies on 2009-03-23
OK, I wrote, followed the instructions, and ended up rebooting. After the reboot, I still get GRUB error 21. I'm now back on the livecd. Any thoughts?

---

### Post by meierfra. on 2009-03-23
Lets see whether you can mount your Ubuntu partition:


```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```

This should list the content of the "/" partition of  Ubuntu.

If you didn't get any error messages, then reinstall grub via

```
sudo grub
```

and at the grub prompt:

```
root (hd0,0)
setup (hd0)
quit
```

Reboot and hope for the best.

But if the "mount" command did not work, let me know and I'll show you how to run a file system  check

---

### Post by chippies on 2009-03-23
> **meierfra. said:**
> 
Reboot and hope for the best

The best was hoped for and everything seems to be running perfectly! I can't thank you enough!!!!

I owe you big time, maybe a puppy? Where should I mail your puppy? I'll punch holes in it to make sure it breathes... The box, that is...

And now I franticly back up my files before anything goofy happens with my video card again!

---

### Post by meierfra. on 2009-03-24
> Everything seems to be running perfectly! 
Great.


> Where should I mail your puppy?
The White House
1600 Pennsylvania Ave
Washington DC
USA

---

### Post by Garratt on 2009-03-24
> **meierfra. said:**
> 
The White House
1600 Pennsylvania Ave
Washington DC
USA

I lol'd at the thought of punching holes in a puppy...

then lol'd even harder at the address.

I can see USA going to defcon5, as a mutilated puppy turns up on Obama's doorstep.

---

### Post by meierfra. on 2009-04-13
Thanks for the puppy. It arrived safely

[http://www.cnn.com/video/#/video/politics/2009/04/13/costello.obama.dog.cnn](http://www.cnn.com/video/#/video/politics/2009/04/13/costello.obama.dog.cnn)

---

