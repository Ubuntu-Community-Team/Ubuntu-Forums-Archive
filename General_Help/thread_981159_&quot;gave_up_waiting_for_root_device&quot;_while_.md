---
title: "&quot;gave up waiting for root device&quot; while booting"
date: 2008-11-13
forum: General Help
---

### Post by DE255 on 2008-11-13
when I turn on my PC and boot 8.10 the splash screen disappears and this error message is prompted.

when I reboot 8.10 starts without problems.

any hints?

[screenshot]("http://dominikengbers.gmxhome.de/bug.JPG")

---

### Post by Coreigh on 2008-11-13
Attach image?


Oops sorry I was trying to figure out how people attach a clickable thumbnail instead of giant pictures.

---

### Post by DE255 on 2008-11-13
something wrong? should I post a clickable version? too big? :oops:

removed the monster screenshot and made a linked pic.

---

### Post by Coreigh on 2008-11-13
No I didn't mean to complain but I have seen people do this:
[http://ubuntuforums.org/showthread.php?t=978984](http://ubuntuforums.org/showthread.php?t=978984)
and I want to know how. I posted a question here:
[http://ubuntuforums.org/showthread.php?p=6169473](http://ubuntuforums.org/showthread.php?p=6169473)

---

### Post by psusi on 2008-11-13
Wait a moment and then type exit.  If it works fine after that it just isn't waiting long enough for your hardware to come up, so adjust the rootdelay= parameter like it suggests.

---

### Post by DE255 on 2008-11-16
after waiting and typing "exit" the system boots.

So I guess you're right.

> dominik@athlon:~$ cat /proc/cmdline
root=UUID=105e82bc-3131-428f-ad9e-aa5f55833421 ro quiet splash 
dominik@athlon:~$ 


how can I adjust the rootdelay?

I only use Ubuntu with Gnome. No terminal experiences...:confused:

---

### Post by psusi on 2008-11-16
Edit your /boot/grub/menu.lst.

---

### Post by elkanguro on 2008-11-23
I have exactly the same problem as DE255. I added all_generic_ide to tehe kernel options in /boot/grub/menu.lst and the BusyBox doesn't appear now but the starting time of the system is 2m20s!
What is wrong?

---

### Post by DE255 on 2008-11-30
> **psusi said:**
> Edit your /boot/grub/menu.lst.

increased the wait up to 20 sec.
no change.
same error.

I tried something else:
after the BusyBox error I only waited 1 or 2 seconds and after typing EXIT everythings fine. strange, hm?

the wait-time isn't the core-problem I guess.

---

### Post by mebegreedy on 2008-12-11
I'm having the same problem, however just typing exit did not fix it.  the only way i have had it load into Ubuntu is when i start windows first and then restart and it starts up normally.  also if i wait long enough it starts to spit out other errors.

Any help would be greatly appreciated

---

### Post by theff on 2009-02-07
> **mebegreedy said:**
> I'm having the same problem, however just typing exit did not fix it.  the only way i have had it load into Ubuntu is when i start windows first and then restart and it starts up normally.  also if i wait long enough it starts to spit out other errors.

Any help would be greatly appreciated

I have the exact same issue. It would be really nice if someone could help, because right now it is very difficult to boot into Ubuntu which is quite frustrating.

---

### Post by avtolle on 2009-02-07
Take a look at [http://www.ubuntu.com/getubuntu/releasenotes/810#Boot%20failures%20on%20systems%20with%20Intel%20D945%20motherboards](http://www.ubuntu.com/getubuntu/releasenotes/810#Boot%20failures%20on%20systems%20with%20Intel%20D945%20motherboards)
The fix is apparently setting 90 as the time out in the kernel parameter.

---

### Post by DE255 on 2009-02-08
thank you!

rootdelay=90 works fine!:KS

---

### Post by iceolate on 2009-04-24
Does anyone have an update on this? 

I upgraded from 8.10 to 9.04 using apt-get. When I restarted, it gave the error and put me at an initramfs prompt.

I have tried to boot to Windows and back to Ubuntu and that does not work. 

Also, I can't seem to find where you people type 'exit' at that prompt, because even after waiting 5 or 10 minutes and longer, I type the word and nothing displays on the screen. I hit Enter and nothing happens either. 

I would love to be able to try adjusting the rootdelay, but I cannot figure out how to get past this prompt.

---

### Post by Monotoko on 2009-04-24
Try to boot into a livecd and edit the file that way?

---

### Post by iceolate on 2009-04-24
> **Monotoko said:**
> Try to boot into a livecd and edit the file that way?

No, I didn't, but thanks. I was able to mount my partition and edit the file. However, there is no change and still gives me that error. 

I'm sure I put the rootdelay option in the right place. Perhaps that is the problem? What line does it go on in /boot/grub/menu.lst?

---

### Post by DE255 on 2009-04-25
> **iceolate said:**
> No, I didn't, but thanks. I was able to mount my partition and edit the file. However, there is no change and still gives me that error. 

I'm sure I put the rootdelay option in the right place. Perhaps that is the problem? What line does it go on in /boot/grub/menu.lst?

it's a kernel parameter not a line in menu.lst

I did the same mistake.
don't remember where to find the file with the kernel parameters - I'm in a hurry.

---

### Post by sripplinger on 2009-04-25
I'm one of the dummies that never listens to good advice until he has to pay for it. Here are my problems, and please forgive my idiocy.

1. "Gave up waiting for root device" of course
2. Typing exit does not work, no matter how long I wait
3. Was dumb enough to only keep one kernel on the grub boot menu ](*,)
4. Live CD boots fine, and I can see my linux partition from there, but I don't know how to edit files with root permissions.
5. Am willing to do a fresh reinstall, but I was dumb enough to not backup before this whole thing. ](*,) I've recovered some files using the live CD, but I can't see some others.

Anybody who can give me a workaround at any point here, I would be very greatful, and I would promise to always keep at least two or three kernels on my boot menu and to backup my files regularly, especially before doing something crazy like an upgrade. ;)

---

### Post by apienk01 on 2009-04-26
I second this plea. After updating to 9.04, BusyBox. No matter how long I wait before exiting, I just get brought back to it. No booting. I checked that Grub recognizes my partitions, and UIDs in menu.lst are good. So what's the problem?

I would really love to know a workaround other than a complete reinstall.

Thanks in advance.

---

### Post by DE255 on 2009-04-27
> **iceolate said:**
> I'm sure I put the rootdelay option in the right place. Perhaps that is the problem? What line does it go on in /boot/grub/menu.lst?

this entry solved my problem
[SIZE="1"]> title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		105e82bc-3131-428f-ad9e-aa5f55833421
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=105e82bc-3131-428f-ad9e-aa5f55833421 ro quiet splash [COLOR="Magenta"]rootdelay=90[/COLOR] 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet[/SIZE]

---

### Post by apienk01 on 2009-04-28
Thanks, DE255. I've already known this workaround. Tried everything, including chrooting to rebuild linux image and grub. Finally, I decided to copy critical data, format and reinstall my root partition. Now it works. I believe the problem was a short wireless network disconnection at the beginning of update to Jaunty. The update script apparently cannot cope with such a situation.

My advice to anybody who plans to upgrade:

1) Always keep your /home on a separate partition
2) Choose your most stable internet connection
3) Never allow the update script to delete old kernel images

---

### Post by iceolate on 2009-05-04
It didn't work for me either. I think my problem was your #2, apienk01. Because I had a wholly UNRELIABLE Verizon internet connection, and it probably quit in the middle of the upgrade. 

I was able to boot off the live CD, mount my partition and get everything off it. So I'm going to do another clean install and then try it again, without Verizon this time.

---

### Post by dmadsen on 2009-05-09
The increase of *rootdelay* to 90 solved this problem for me, too.  Ubuntu 9.04 server.  Note that I did *not* have this problem before 9.04.

I had earlier upgraded to 8.10 on the system, but I wanted to move to ext4 at this time (from reiserfs), so I backed up everything to another drive already on the system and re-installed using the 9.04 server AMD 64 CD.

I did not have any network issues, it just didn't work when I rebooted.

Hardware: Tyan S2882G3NR-D MB, LSI Logic / Symbios Logic SAS1068 PCI-X Fusion-MPT SAS with 2 MAXTOR  ATLAS10K5_73SAS, LSI Logic / Symbios Logic MegaRAID SATA 300-8X RAID Controller (with 4 drives currently).  The SATA RAID is detected by Linux as sda and the two drives on the SAS controller are sdb and sdc.  I chose not to make them a RAID.  The hardware boots from the first SAS disk (sdb), which contains the OS, and it was that one that had the delay problem.

---

### Post by lookyn on 2009-06-05
> **iceolate said:**
> Does anyone have an update on this? 

I upgraded from 8.10 to 9.04 using apt-get. When I restarted, it gave the error and put me at an initramfs prompt.

I have tried to boot to Windows and back to Ubuntu and that does not work. 

Also, I can't seem to find where you people type 'exit' at that prompt, because even after waiting 5 or 10 minutes and longer, I type the word and nothing displays on the screen. I hit Enter and nothing happens either. 

I would love to be able to try adjusting the rootdelay, but I cannot figure out how to get past this prompt.

the same boot problem with me!! except that I met it within 8.10 installation. My IDE DVD-RW can not be detected ,and so with my SATA Harddisc(WD640).
"wait a bit longer and type exit..." do not work,also "rootdelay = *anyvalue*".....:(
Now I can launch menu.lst from /boot/grub,and boot into rescue mode.So I chang the menu.lst file with addition "rootdelay" flag,do not work....I don't know what to do next.....

There was a bugreport([Bug 290153]("https://launchpad.net/bugs/290153")) mention similar problem(right! unfortunately Intel D945 in my machine...)

---

### Post by apienk01 on 2009-06-08
If you managed to boot into the rescue mode, try to reinstall linux-image and grub packages:

```
sudo apt-get install --reinstall grub linux-image
```

This should help.

---

### Post by mattdan79 on 2009-07-01
hmmmm I just ran into the same issue.
Now in my case I think it is hardware.  I replaced my power supply after the problem started (system would randomly freeze - I was getting error "...gave up waiting for root..."

Just out of curiosity, is your error always the same.  Does the system freeze randomly at other locations?  My rule of thumb is "if the error is consistent & I can reproduce then it is more than likely software".  If it is inconsistent you may want to think about hardware.

I personally suggest you use the 9.04 live mode and see if system freezes/acts up even with that.

Many of us can attest that when hardware is the problem it is the hardest to fix.

---

### Post by shaneburton on 2009-09-15
I ran into this same issue and tried all of the suggestions.  What I didn't realize was that my menu.lst was point to /dev/sdc5 rather than /dev/sdd5.  The reason it changed was because after the install I plugged in a USB HDD and that somehow managed to be /dev/sdc so the bootloader could find my drive.
 
Stupid noob mistake, but removed the drive and all was well.
 
at the initramfs prompt type cat /proc/partitions to see all of the available partitions.

---

### Post by tim.j.stewart on 2009-09-30
I have a SanDisk Cruzer 8GB USB drive that I've installed Jaunty to (from the Ubuntu Jaunty Live CD).  I'm trying to run Jaunty from the USB drive on my x64 AMD Pavilion dv4.  When I boot from the USB, I get a &quot;Gave up waiting on root device&quot; message and the BusyBox prompt. 

I've tried many of the suggested solutions:

   rootdelay=30 (up to 300)
   add usb_storage to /etc/modules
   replace UUID with /dev/sdb1 in modules.lst and fstab.
   adding all_generic_ide floppy=off irqpoll pci=nomsi  to the kernel line in my /boot/grub/modules.lst

None of these solutions prevented me from seeing the BusyBox prompt.   When I boot I cannot see my USB boot partition (/dev/sdb1).

The only thing that has worked for me is:

   While the boot process says it's waiting for the root device, remove the USB drive that it's booting from and immediately insert it again.  

   At that point some messages appear on the screen saying that sdb1 and sdb5 have been found.

   Then it boots fine. 

   This is not a fix (although it makes my USB drive's data more secure).  Any ideas why I need to remove and reinsert my USB drive while booting?

Thanks.

---

### Post by tim.j.stewart on 2009-09-30
In my previous post, I mentioned that I had to remove the USB drive at one point during the boot.  After I successfully booted and got into GNOME, the Update Manager ran and it installed the 2.6.28-15-generic kernel.  Now I no longer need to remove the USB drive during the boot process.  BTW, my previous kernel version was 2.6.8-11-generic.

---

### Post by mcdjork on 2009-12-11
If you have this problem, it's possible also that your root partition is actually corrupt. This happened to me.

All you need to do is boot into a live cd or rescue prompt and run fsck /dev/sda5 (or whatever your root partition is). This runs a fix disk on your root, and if successful, you will then boot just fine.

---

### Post by nateharward on 2010-04-06
Fix that worked for me with Ubuntu 9.10.

When typing exit again and again and adding rootdelay=90 didn't help my problem i tried this:

Fix meant for Karmic and beyond.

1- boot up live disk (cd or usb).

2- open a terminal (F2 -> gnome-terminal)

3- Find your root partition your having trouble booting up with:```
$ sudo fdisk -l
```

4- type the following and replace sda5 with whatever partition you choose) This will fix any corruption with the partition:```
$ sudo fsck /dev/sda5
```

5- now we'll chroot into your root partition to update the grub. Type the following: ```
$ sudo mount /dev/sda5 /mnt
$ sudo mount --bind /dev /mnt/dev
$ sudo chroot /mnt
$ update-grub
```

6- Press Ctrl-D to get back to normal prompt and type to unmount:```
$ sudo umount /mnt/dev
$ sudo umount /mnt
```

7- Restart and boot without live disk

Good Luck

---

### Post by Avoozl on 2010-05-05
Thanks nateharward.  I had the same problem with karmic and your fix worked.

As an added note I dual boot with XP and I had to run update-grub again once I was booted into linux proper because the initial update-grub (run from the boot disc) erased my XP entry.

---

### Post by Amadameus on 2010-06-14
I'm having similar problems - for now, I have no solution.

Signs seem to show (for both you and me) that there's a problem with the hard drive's boot sector. 

GRUB is asking the hard drive for information on how to boot up, and the hard drive is taking so long that GRUB gives up and falls into a shell.

...why it succeeds in running Ubuntu after dropping to the BusyBox command line is beyond me. Long access time means a problem, but how to fix it?

---

### Post by msriram on 2010-07-20
> **nateharward said:**
> Fix that worked for me with Ubuntu 9.10.

When typing exit again and again and adding rootdelay=90 didn't help my problem i tried this:

Fix meant for Karmic and beyond.

1- boot up live disk (cd or usb).

2- open a terminal (F2 -> gnome-terminal)

3- Find your root partition your having trouble booting up with:```
$ sudo fdisk -l
```

4- type the following and replace sda5 with whatever partition you choose) This will fix any corruption with the partition:```
$ sudo fsck /dev/sda5
```

5- now we'll chroot into your root partition to update the grub. Type the following: ```
$ sudo mount /dev/sda5 /mnt
$ sudo mount --bind /dev /mnt/dev
$ sudo chroot /mnt
$ update-grub
```

6- Press Ctrl-D to get back to normal prompt and type to unmount:```
$ sudo umount /mnt/dev
$ sudo umount /mnt
```

7- Restart and boot without live disk

Good Luck
thanks! fsck literally fu**ed my partition

---

### Post by cr0max on 2010-09-21
To me, the live CD didn't even display the drive anymore. I had to manually
```
sudo mount -t ext4 /dev/sda1 /mnt
```and then 
```
sudo chroot /mnt
sudo update-grub
```did the job. Before, the /boot/grub/menu.lst was missing, so was /proc/modules. Guess it was fsck's fault.

Thanks for your help.

---

### Post by chrisclay on 2010-09-24
hi i have been reading this thread and i have the same problem but i am having some problems editing the boot/grub/menu.lst i cant even find it so could someone please post step by step instructions for new users

thanks chris

---

### Post by zeeshaan on 2010-09-28
Here's a 100% working solution. 
_**[COLOR=Navy] Zee's 6 step Ubuntu fix![/COLOR]**_
[http://zeeis.me/ubuntu-boot-error-simple-fix-gave-up-waiting-for-root-device/](http://zeeis.me/ubuntu-boot-error-simple-fix-gave-up-waiting-for-root-device/)
If you wanna share it with anyone or post it on your website, please mention a linkback as credit.

---

### Post by Thobold on 2010-11-14
[COLOR=#000000]Today, after running Ubuntu got this message:
[/COLOR]> Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
     - Check rootdelay= (did the system wait long enough?)
     - Check root= (did the system wait for right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/a0c70102-b5d8-4b82-a14c-225330e1c4d4  does not exist. Dropping to a shell!


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _                      **I have Ubuntu 10.04 and grub2.** What should i do?

*Additional information*
> root@laptop:~# fdisk -l
Disk / dev / sda: 160.0 GB, bytes: 160041885696
255 heads, sectors / track: 63 Cylinders: 19457
Units = cylinders of 16065 * 512 = 8225280 bytes
The sector size (logical / physical) in bytes: 512 / 512
Size of I / O (the minimum / optimum) in bytes: 512 / 512
Disk identifier: 0x46f349d8

Device Boot Start End Blocks Id System
/ Dev/sda1 * 1 9916 79650238 + 83 Linux
/ Dev/sda3 9917 19457 76638082 + 5 Extended
/ Dev/sda5 18504 19457 7663005 83 Linux
/ Dev/sda6 9917 18503 68975014 + 83 Linux

Partition table entries are not in that order, as the disk> root@laptop:~#  blkid
/dev/sda1: LABEL="Zapasowa" UUID="6ed5d725-45bd-4b95-852f-5b581ea00119" TYPE="ext4" 
/dev/sda5: LABEL="Ratunkowa" UUID="79a4ace1-60f4-45e8-a795-3fcc349b329e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="Systemowa" UUID="a0c70182-b5d8-4b82-a14c-225330e1c4d4" TYPE="ext4"                      > root@laptop: ~ # apt-get install - reinstall linux-image grub
Reading package lists ... Done
Building dependency tree
Reading state information ... Done
Failed to install some packages. This may mean
that requested an impossible situation or an unstable
that some required packages have not yet been created or been moved
Incoming directory ("Przychodz&#261;ce").
The following information may help resolve the situation:

The following packages have unmet dependencies:
linux-image: Depends: linux-image-generic (= 2.6.32.24.25) but 2.6.32.25.27 is to be installed
E: Broken packages

---

### Post by rbp on 2010-11-17
thanks for tips guys. I found booting into Windows and then choosing an old version from Grub was the magic formula.

---

### Post by awcyber on 2010-11-20
thanks for tips guys,,,,, work... ;)

---

### Post by T-S-B on 2010-11-26
I had this problem, which was temporarily fixed by changing the rootdelay to 90, but this extended the boot time.

Because I was also getting a long "Searching for drive" delay when loading BIOS, I switched the master-slave jumper on my optical (IDE) drive and this has also fixed the problem in Ubuntu 10.10.  Rootdelay is still set at 90 but Ubuntu loading doesn't sit around that long waiting.

Hope this helps somebody, and maybe helps identify the root cause.

---

### Post by ErikDeBruijn on 2010-12-27
After none of the solutions in this thread got me any further (no pun intended!), I finally solved this problem on my Ubuntu 10.10 system.

If rootdelay=90 doesn't fix it for you, please check if somehow the dmraid package got uninstalled. Here's my solution to a problem that had the same symptoms. If you have these problems, take a look at my solution. It might work for you:
[http://ubuntuforums.org/showthread.php?p=10283846](http://ubuntuforums.org/showthread.php?p=10283846)

Hope this helps!

---

### Post by jamil.farooq@hotmail.com on 2011-06-30
Hi,

I have similar problem where i can't boot from my lvm partition.


it gives similar ALERT /dev/mapper/lmspv1-lmslv1 not found error
before this it also give error of not finding physical volume with given uuid. 

   1. as i have swap some disks here n there so i m not sure if uuid changes due to this.
   2.  exit intrifms does not work so i think its not rootdelay problem.
   3.  how come i can't see my lvm partition uuid by calling ls -l /dev/disk/by-uuid
   

please help its urguent

regards

---

### Post by psusi on 2011-06-30
Please start a new thread instead of hijacking an old one.

---

### Post by chrisclay on 2011-06-30
Hi on my system the problem was that in the bios i had the pc to boot from the cd drive that was an ide device and my hard disks were sata disks and it seemed to not like this mix of interfaces as when changed the first boot device to the sata disk it continued looking for the cd drive to boot from,after about ten attempts to install ubuntu i gave up and put a new cd drive in a, sata one reinstalled and it was all fine.I subsequently had to install Ubuntu twice more on the same system and had no other problem.
 
 
i hope this helps
 
regards c claydon

---

### Post by nclpltt on 2011-07-31
nateharward's method worked also for me.
I'd like to add just a personal note, to avoid that other people make my mistakes, that is:
You must boot a live distro of the same architecture of the system to recover, unless chroot won't work. In fact I had to restore the grub of a x64 Ubuntu 10.04, and a 32 bit live OS didn't work. I managed with a x64 version of Parted Magic, which is enough for this operation.
Thank you!

---

### Post by Rokanten on 2011-08-08
In my case adding "rootdelay=90" in kernel params does not help and typing  "*exit*" in initramfs prompt just drop to initramfs shell again.
(Ubuntu Server 10.04 LTS /Xeon 5507/Server Board S5520).
In /dev/mapper was only "control" device. 
After "*vgchange -ay*" logical volumes all appear in place and now, after "*exit*" command, system finished booting.
Looks like initramfs`s init trying to mount root too fast or not executing "*vgchange -ay *" at all... 
Temporary fixed this by adding script activate_lvs in /etc/initramfs-tools/scripts/init-premount/
```
#!/bin/sh
sleep 10
vgchange -ay
sleep 1
```
And generating after that initrd, of couse: 
"*update-initramfs -u*"
Hope it survives after updates...

---

### Post by dbots on 2011-09-04
Hi, I had the same problem and after managed to login, tried to run cfdisk.
It replied with message :
FATAL ERROR: Bad primary partition 1: Partition ends in the final partial cylinder
and after running fdisk -l, I see :

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4661    37431296   83  Linux
/dev/sda2            4661        4866     1648641    5  Extended
/dev/sda5            4661        4866     1648640   82  Linux swap / Solaris

See that sda1 ends at 4661 and sda2 starts at the same 4661.

During installation, for partition I selected "Guided - use entire disk" so the automatic partitioner caused this. I used Ubuntu 10.04 LTS 64bit.

I think that if this causes the problem, all other solutions like updating grub or setting 90 seconds to wait etc are useless since partitioning is wrong.

---

