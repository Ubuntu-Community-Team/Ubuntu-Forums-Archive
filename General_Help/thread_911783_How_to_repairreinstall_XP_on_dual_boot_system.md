---
title: "How to repair/reinstall XP on dual boot system?"
date: 2008-09-06
forum: General Help
---

### Post by cp1969 on 2008-09-06
I need to repair or reinstall XP on the same hard drive that Ubuntu 7.10 is on.  I used to have a dual boot system and it worked fine until one day it locked up so bad that cutting the power was the only way out.  It never booted up under Windows after that.

The Windows CD won't do it.  It is not a problem with the CD; there is a problem with the Linux partitions that are on the hard drive that prevents the CD from functioning correctly. The installation program just hangs up.

If I used Gparted to get rid of the partitions, the CD *might* work.  But, what are the risks of doing that?

Wish I knew how to post a screen shot of the current partition arrangement.  I thought when I created this system that I created three partitions: one for Windows, one for unbuntu, and one for data.  But according to Gparted, it lists /dev/sda1 thru /dev/sda4, with #2 having /dev/sda's 5 thru 8 under it.

The only reason I want to keep Windows, and I may be mistaken, is that I want to install a wireless router (Linksys WRT54GS) so that two other computers (one Vista, one XP) can access the internet and hopefully share the printer that is connected to this computer.  Maybe I need to trade places with the XP desktop and put the wireless card in this machine rather than the other way around as I'd planned.

Any help will be greatly appreciated.

Thanks.

---

### Post by sujitkale on 2008-09-06
if u have 2 other computers then connect your hard disk to one of those computer and use partition magic or partition manager to rectify the problem.

---

### Post by cp1969 on 2008-09-06
I don't have partition magic.  The only partition tool I have is Gparted on this computer.  As far as I know, the other computers have nothing installed on them which  would allow me to manipulate the partitions any better than Gparted.  (The desktop has XP; the laptop Vista).  But thanks for the suggestion.

---

### Post by chiefgeargrinder on 2008-09-06
can you boot into safemode in xp?

---

### Post by cp1969 on 2008-09-06
No.

---

### Post by cp1969 on 2008-09-08
I found this thread:

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/#comment-54889](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/#comment-54889)

It talks about using a Linux tool called 'ms-sys' to repair the MBR of the Windows installation.  However, more than a few posters claim it will not work, while others claim it worked beautifully.

It basically goes like this:

Boot up using the Ubuntu Live CD.
Go to System > Administration > Software Sources and enable 'Universal'
Then open a terminal and type
sudo apt-get install ms-sys

Then, 
sudo fdisk -l  to determine the correct location of the hosed Windows installation

Then,
sudo ms-sys-m /dev/sda, where the /sda is what was returned by the fdisk -l query

What do you think?  Gonna blow the whole thing to Kingdom Come?

---

### Post by caljohnsmith on 2008-09-08
> **cp1969 said:**
> I found this thread:

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/#comment-54889](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/#comment-54889)

It talks about using a Linux tool called 'ms-sys' to repair the MBR of the Windows installation.  However, more than a few posters claim it will not work, while others claim it worked beautifully.

It basically goes like this:

Boot up using the Ubuntu Live CD.
Go to System > Administration > Software Sources and enable 'Universal'
Then open a terminal and type
sudo apt-get install ms-sys

Then, 
sudo fdisk -l  to determine the correct location of the hosed Windows installation

Then,
sudo ms-sys-m /dev/sda, where the /sda is what was returned by the fdisk -l query

What do you think?  Gonna blow the whole thing to Kingdom Come?
First of all, can you still boot into Ubuntu on that HDD? Is it only Windows that won't boot from the Grub menu? If that is true, using "ms-sys" to replace Grub with a Windows master boot record (MBR) won't help; Grub can boot Windows just fine (as has been the case for you up until now), and your problem sounds like it is entirely Windows related and not Grub related.

Also, if you think that your Linux partitions are some how preventing the Windows Install CD from working, you can always set their "hidden" partition flag so that Windows won't even see them. Keep in mind that when you do that, you won't be able to use Grub until you "unhide" them. But if you think that is holding up your Windows CD, here is how to temporarily hide your linux partitions (using the Live CD):
[LIST]
[*]First figure out which are your Ubuntu partitions are with:
```
sudo fdisk -lu
```
[*]Then figure out what their Grub equivalent is, e.g. sda1 is (hd0,0), sda2 is (hd0,1), sda3 is (hd0,2), etc. Then use that:
```
sudo grub
grub> hide (hdX,Y)
grub> quit
```[/LIST]
When you are ready to unhide those partitions, use "unhide" instead of hide. Let me know how it goes or if you need more details/info.

---

### Post by cp1969 on 2008-09-08
I can still boot into ubuntu.

sudo fdisk -l returns:
/dev/sda1, which is bootable and it's system is HPFS/NTFS

I've already tried hiding the partitions; all that did was make it so that neither xp nor ubuntu would boot.

I am at my wits end.  As a test, I took the xp/ubuntu drive completely out of the computer.  I then tried to do an XP installation on a different hdd.  Things went OK until it got  to the point where it asks you to reboot the computer to finish.  At that point, I got a 'disk read error; press controll-alt-delete' to continue.  I thought, erroneously, that if I could get XP running on that drive, then I would just install ubuntu on it, move my data, and all would be good.  

Remember the scene in Office Space where the three progagonists attack the copier (or was it a printer?) in the open field?  I am just about there, except it will not be with a baseball bat.  I think a 12 gauge, loaded with 00 Buck is in order.

---

### Post by cp1969 on 2008-09-08
Results for sudo fdisk -l:

255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12041203

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2598    20868403+   7  HPFS/NTFS
/dev/sda2            4990       15413    83730780    f  W95 Ext'd (LBA)
/dev/sda3           15414       19457    32483430   83  Linux
/dev/sda4            2599        4989    19205707+  83  Linux
/dev/sda5            5100       10198    40957686    e  W95 FAT16 (LBA)
/dev/sda6           10199       15297    40957686    e  W95 FAT16 (LBA)
/dev/sda7           15298       15413      931738+  82  Linux swap / Solaris
/dev/sda8            4990        5099      883512   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffff6a32

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS

Below is a screenshot of Gparted.

---

### Post by cp1969 on 2008-09-08
FWIW, here is what is in GRUB:

For Windows:
root (hd0,0)
save default
makeactive
chainloader +1

For ubuntu:
root (hd0,3)
kernel /boot/linuz-2.6.22-14-generic root=UUID=791650d6 ->
initrd /boot/initrd.img-2.6.22-14-generic
quiet

---

### Post by cp1969 on 2008-09-09
bump

---

### Post by caljohnsmith on 2008-09-10
> **cp1969 said:**
> FWIW, here is what is in GRUB:

For Windows:
root (hd0,0)
[COLOR="Blue"]save default[/COLOR]
makeactive
chainloader +1

Just a small detail, but the "save default" should actually be "savedefault". Unfortunately I don't think that will solve your problem, but it would be good to make sure that is correct. Also, another thing that certainly won't hurt is if you can run "fixboot" from you Windows Install CD, which will make sure the Windows partition's boot sector is OK. Can you describe exactly what happens when you try and boot into Windows? Any error messages?

Have you maybe tried contacting Microsoft about the problem? They might actually have a documented workaround or fix for when a Windows Install CD does not detect the installed Windows on the HDD.

---

### Post by cp1969 on 2008-09-12
That save default is probably a typo on my part.

When I try to boot into Windows by making the menu choice for Windows in Grub, it looks like it makes it thru POST then the monitor gives a brief "no signal" message (just like when shutting down), then it returns to the Grub menu.

When I try to boot via the CD, nothing.   A semi-dark screen.  If I unplug the drive which contains ubuntu and XP and try to boot to yet another drive which also contains an unbootable installation of XP, I get the screen in which you are asked whether you want to install XP or repair it.  So I know the CD is good to that point, plus I've installed XP successfully with it twice.

It may be that I have to delete ubuntu from the disk, reinstall xp, then reinstall ubuntu.  I will probably lose all my data if that is the case because I have no drive space in which to copy my unbuntu files.  The other hard drive is essentially empty, but it was formatted NTFS when xp was installed.

---

### Post by caljohnsmith on 2008-09-12
> **cp1969 said:**
> 
It may be that I have to delete ubuntu from the disk, reinstall xp, then reinstall ubuntu.  I will probably lose all my data if that is the case because I have no drive space in which to copy my unbuntu files.  The other hard drive is essentially empty, but it was formatted NTFS when xp was installed.
You can easily mount NTFS partitions as read-writable in Ubuntu, so being NTFS shouldn't stop you from saving your important Ubuntu files to that drive if you wish to do so. But you will of course lose each files' permissions and ownership info when you copy them into an NTFS file system.

---

### Post by meierfra. on 2008-09-12
I  have had unexplainable  problems  booting from the XP CD  in the past. But I was able to solve them by using SBM (Smart Boot Manager). 
I'm not sure that I will work for you, but you might give it a try:

download the attached file "smb.tar.gz", extract it and save the two files "memdisk.bin" and "sbootmgr.dsk" to your grub folder. Then add this to the end of your "menu.lst"


title  CD via SBM
root (hdX,Y)        #use the same numbers as for Ubuntu
kernel /boot/grub/memdisk.bin
initrd /boot/grub/sbootmgr.dsk

Reboot and select "CD via SBM" from the grub menu.

---

### Post by cp1969 on 2008-09-13
deleted

---

### Post by cp1969 on 2008-09-13
> **meierfra. said:**
> I  have had unexplainable  problems  booting from the XP CD  in the past. But I was able to solve them by using SBM (Smart Boot Manager). 
I'm not sure that I will work for you, but you might give it a try:

download the attached file "smb.tar.gz", extract it and save the two files "memdisk.bin" and "sbootmgr.dsk" to your grub folder. Then add this to the end of your "menu.lst"


title  CD via SBM
root (hdX,Y)        #use the same numbers as for Ubuntu
kernel /boot/grub/memdisk.bin
initrd /boot/grub/sbootmgr.dsk

Reboot and select "CD via SBM" from the grub menu.

That returned "error 13; Invalid or unsupported executable format."

Here is what I put in:

# This entry was added by cep to try to make xp boot from CD
title		CD via SBM
root		(hd0,3)
kernel		/boot/grub/memdisk.bin
initrd		/boot/grub/sbootmgr.dsk


I don't know what's with all the extra space between the first word, such as "root" and the rest of its line, "(hd0,3)", but all of the entries in my menu.lst file look that way.  I had to hit the Tab key twice to get things lined up like they were in entries above what I put in.

---

### Post by meierfra. on 2008-09-13
Some how memdisk.bin got corrupted when I created the archive.  I replaced the attachment in my previous post. So  download the file again and hopefully it will work this time.

---

### Post by cp1969 on 2008-09-13
Thank you!!!  That does, at least, allow me to boot from the Windows CD.

After booting from the CD, I tried the following "Repairing Windows XP in Eight Commands."

The commands are:
from the C:\Windows  prompt given by the CD in Repair mode

cd ..   (jumps to root directory)
attrib -h c:\\boot.ini
attrib -s c:\\boot.ini
attrib -r c:\\boot.ini
del boot.ini  (the three previous steps set up this deletion)
BOOTCFG /Rebuild
Chkdsk /r/f (I omitted this step)
FIXBOOT

Doing all this returns a question "Add installation to boot list?" to which I answered 'no' because I figured Grub already has an entry for this.  Maybe that was a mistake.  Then it asked for "OS Load Options" to which I put in "/fastdetect".

It didn't work.

I wonder, though, now that I can boot to the XP CD, if I should try to reinstall.  I have had no luck doing a reinstall on that other unbootable drive, however.

---

### Post by meierfra. on 2008-09-13
> "Add installation to boot list?" to which I answered 'no' because I figured Grub already has an entry for this. Maybe that was a mistake. 

Yes it was. Grub only calls the Windows Boot loader. The Windows  boot loader looks at  the boot list (boot.ini) to see what OS to boot. 

So I suggest to try again.

---

### Post by cp1969 on 2008-09-13
It was great while it lasted but it didn't last long.  

Now, SBM injects itself into the boot process (it did not the first time I tried the repair) giving me the boot options of:

Quit to BIOS
Power off
Reboot

I can do a 'rescan' and it will populate the list with other options, but none of them are the CD.  

So my booting from the CD seems to be impossible now that SBM has popped up.

---

### Post by cp1969 on 2008-09-13
WTF?  BIOS still shows that my CD is first in the boot list, yet it makes no attempt to boot from the CD and Smart Boot Manager does not list the CD as a choice.

Sequence of events goes like this:
With CD in drive, power on goes straight into Grub menu.  No message saying 'press any key to boot from CD'  If I select 'CD via SBM' from the Grub menu, it takes me to the three-choice menu in SBM, none of which will even try to boot the system, via the CD or otherwise.

---

### Post by meierfra. on 2008-09-13
Sorry, I have no idea what is going on. You might try editing "boot.ini" from ubuntu.  It should look something like this:

[Boot Loader]
timeout=30
Default=multi(0)disk(0)rdisk(0)partition(1)\Windows
[Operating Systems]
multi(0)disk(0)rdisk(0)partition(1)\Windows="Windows XP" /fastdetect

---

### Post by cp1969 on 2008-09-13
Nor do I.  Now the damned thing won't even boot into ubuntu.  I get the ubuntuo logo, but the little scroll bar never fills out.

edit:  eventually, it drops into a shell.  But I have no idea what command to issue at the shell.

---

### Post by meierfra. on 2008-09-13
Are you able to boot from the Ubuntu Live CD? If yes, run a file system check on your ubuntu partition:

```
sudo fsck -y /dev/sda4
```

You might do the same for "/dev/sda3". 

If you ever get to boot your Windows CD  again, you should also run "chkdsk /r/f"

---

### Post by cp1969 on 2008-09-13
Can't boot from any CD, unbuntu or windows.  It doesn't even try.  The Cd never spins.

---

### Post by Gannon8 on 2008-09-13
I had this happen when I had 2 CD drives. The first one broke, and the bios would not try to boot from the working second one. I had to go into the case and disconnect the broken one.

---

### Post by cp1969 on 2008-09-13
I only have one CD drive and it works because I was just able to boot up the ubuntu Live CD...but only after unplugging HDD #1.  So, I can now boot up, via the Live CD, but the drive I need to work on is unplugged.

---

### Post by Gannon8 on 2008-09-13
Hmm...Maybe a Drive Jumper problem? I can't explain it, but maybe someone else can.

Though if it were that, it would probably lead to data corruption. Anyway, consider a USB enclosure for the hard drive.

---

### Post by meierfra. on 2008-09-13
> but the drive I need to work on is unplugged. 

Can you plug the drive in after you booted the LiveCD?

---

### Post by cp1969 on 2008-09-13
> **meierfra. said:**
> Can you plug the drive in after you booted the LiveCD?

Physically, yes, I can plug it in.  I wonder how well it will like that.

---

### Post by meierfra. on 2008-09-13
> I wonder how well it will like that.

No idea, I never physically mess around with my internal drives. Maybe somebody else knows?

---

### Post by cp1969 on 2008-09-14
Update:

Now, for whatever reason, I can get the Live CD to run with both hdd's plugged in.  So, maybe I can fix ubuntu?

When I go to Places and click on 'Computer', though, I do not see the drives as they used to be.  Formerly, I had one 160G hdd cut up into partitions, one containing xp, others we made by ubuntu during its installation, etc.  The other drive was not partitioned, and showed up as a 149GB drive.  At any rate, it used to list separate drives of 20G(the xp partition), 30G(ubuntu), etc., and the 149GB drive.  Now, when you look under Places it shows the 149GB drive, a floppy, a CD, and 'filesystem'.

But if I look using Gparted, it shows /dev/sda and /dev/sdb, just like before, and the partitions all look just like they did before this mess occurred. 

Is it best to try to repair my ubuntu installation or try to reinstall over the top of the existing one?

Thanks.

---

### Post by cp1969 on 2008-09-14
> **cp1969 said:**
> Results for sudo fdisk -l:

255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12041203

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2598    20868403+   7  HPFS/NTFS
/dev/sda2            4990       15413    83730780    f  W95 Ext'd (LBA)
/dev/sda3           15414       19457    32483430   83  Linux
/dev/sda4            2599        4989    19205707+  83  Linux
/dev/sda5            5100       10198    40957686    e  W95 FAT16 (LBA)
/dev/sda6           10199       15297    40957686    e  W95 FAT16 (LBA)
/dev/sda7           15298       15413      931738+  82  Linux swap / Solaris
/dev/sda8            4990        5099      883512   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffff6a32

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS

Below is a screenshot of Gparted.


OK, today's results of fdisk -l:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12041203

[B]This doesn't look like a partition table
Probably you selected the wrong device.[/B]

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?           1        2598    20868403+   7  HPFS/NTFS
/dev/sda2            4990       15413    83730780    f  W95 Ext'd (LBA)
/dev/sda3           15414       19457    32483430   83  Linux
/dev/sda4            2599        4989    19205707+  83  Linux
/dev/sda5            5100       10198    40957686    e  W95 FAT16 (LBA)
/dev/sda6           10199       15297    40957686    e  W95 FAT16 (LBA)
/dev/sda7           15298       15413      931738+  82  Linux swap / Solaris
/dev/sda8            4990        5099      883512   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffff6a32

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 


Notice the "this doesn't look like a partition table. Probably you selected the wrong device".  Wonder what that's about?

Hey, at least I've got the Live CD running.

But when I double click on the partition that I think contains ubuntu, some bad news appears.  See screenshot.

---

### Post by meierfra. on 2008-09-14
If you don't have any valuable data on /dev/sda I suggested to use gparted to delete all the partitions (and maybe use dban to completely wipe the hard drive) and start from scratch.

But if you have valuable data, you could use  testdisk and fsck to try to rescue your system.

---

### Post by cp1969 on 2008-09-14
I have quite a bit of valuable data on the ubuntu drive.  Or should I say, *had* valuable data on it.


Unbelievable.  Ubuntu was running fine yesterday; with the addition of Smart Boot Manager to try to fix a hosed XP installation, I am on the verge of losing, or have already lost, everything.

This is pretty disgusting.  The chain of events set in motion by a simple freezing up of Firefox has now led to total meltdown.

1. Everything fine; able to boot into XP or Ubuntu at will.
2. Firefox freezes, computer must be powered down.
3. Windows XP refuses to boot after that.
4. Ubuntu partitions prevent Windows CD from starting so as to be able to repair XP installation.
5. Install Smart Boot Manager as work around.
6. SBM removes ability to boot to anything other than normal ubuntu startup.
7. During the course of dozens of reboots, one is interrupted (by me, because I hit ctl-alt-del during the course of one of these ubuntu bootups because I didn't want to wait until it booted up just to shut it down)
8.  That did it--couldn't boot to anything, including the CD; ubuntu now drops into some kind of indecipherable shell that only Mr. Ubuntu himself might recognize.
9.  Today, for whatever reason, can boot to the Live CD.
10. No idea as to how to repair, other than wipe hdd and start over.  I prefer to buy a new hdd and reinstall, but the effect is not much different.

So there you have it: How to F--- yourself in 10 easy steps.

---

### Post by meierfra. on 2008-09-14
Try

```

sudo fsck -y /dev/sda4

sudo fsck -y /dev/sda3

```

---

### Post by cp1969 on 2008-09-14
> **meierfra. said:**
> Try

```

sudo fsck -y /dev/sda4

sudo fsck -y /dev/sda3

```

Here's what I get:
ubuntu@ubuntu:~$ sudo fsck -y /dev/sda4
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext2: No such file or directory while trying to open /dev/sda4

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo fsck -y /dev/sda3
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext2: No such file or directory while trying to open /dev/sda3

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$

---

### Post by meierfra. on 2008-09-14
Lets see whether testdisk can see your ubuntu files and/or find the locations of the superblocks:

Enable "universe" repositories:
Systems-> Administration->Software Sources"
Click on the Box next to "Community-maintained Open Source Software (universe)

then install and run  testdisk via:

```
sudo apt-get install testdisk
sudo testdisk /dev/sda 
```


Choose "proceed" on the first screen.
Choose "intel" at the second screen.
Choose "analyse"  at the third  screen.
Choose "proceed" on the fourthed screen.
Select your ubuntu partition and press "p". This should let you browse the folders of your ubuntu partition.
Press "esc" to get back to the list of your partition
You might try the same for  you windows partition.

Back at the list of partition, press "enter" to continue.

If the partition table looks correct, you can choose "write" to rewrite
the partition table. Or you can choose "search"  to initialize a longer search. 

Go back to the main testdisk menu and choose "advanced". Select your ubuntu partition and press "enter". This will list all the superblocks. Write down the numbers (not the blocksize, just the first number in each row).
(if you are not sure which one is your ubuntu partion, to the same for any partition which might be your ubuntu partition)

Quit testdisk.
Using the numbers you can try the  file system check again:

```
sudo e2fsck -b  number_from_testdisk -yv /dev/sda3
```

Try various of the numbers. Also try sda3 in place of sda4.
Report any error messages.

---

### Post by cp1969 on 2008-09-14
I haven't gotten all the way thru it but can see that my files are still there.  Thanks.

---

### Post by cp1969 on 2008-09-14
I was at the point of writing the partition table after doing a search to find more partitions.

Then, it just slowed to an absolute, mind-numbing crawl.  Either I don't have enough memory to run all the applications I had open, or the CD drive had reached its limit as it had been booted to the cd for several hours.  Maybe I'll try again later when things (including myself) have cooled off.

I don't know.  I honestly don't have the patience or time to fight this battle.  I think I am on at least my fourth or fifth day of screwing with this probably 40 or 50 hours worth.

It may be time for a new computer.

---

### Post by meierfra. on 2008-09-14
Searching for more partitions can be pretty slow. I suggested to continue with the rest of my post (use testdisk to find the locations of  the superblocks and then run  "e2fsck")

---

### Post by cp1969 on 2008-09-14
> **meierfra. said:**
> Searching for more partitions can be pretty slow. I suggested to continue with the rest of my post (use testdisk to find the locations of  the superblocks and then run  "e2fsck")
It got through that OK.  Then I was going to post a screenshot of the results for you to see and it just virtually ceased to function.  I noticed somewhere that ubuntu says it takes 380k of RAM to run off the CD; that is exactly what I've got.

I guess the good news is that, at least right now, the files are still there.

Hard telling what my next boot attempt will produce, though.

---

### Post by meierfra. on 2008-09-14
> Hard telling what my next boot attempt will produce, though

Yes. But you might as well try.  And if you are able to boot into Ubuntu, I  suggest to find some way to backup  you data (like: new hard drive, new computer ...)

---

### Post by cp1969 on 2008-09-14
The error messages from the e2fsck commands are:

No such file or directory while trying to open /dev/sda3 (I also tried sda1, 2, &4; same result)

The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it rally contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corupt, and you might try running e2fsck with an alternate superblock:  e2fsk -b 8193 <device>

---

### Post by meierfra. on 2008-09-14
I'll guess your  ubuntu partition is beyond repair. But you might be able to use  "photorec" to recover some of your  Data. Photorec is part of testdisk, so it got installed then you installed testdisk. See [ http://www.cgsecurity.org/wiki/PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") for instruction how to use photorec.

---

### Post by cp1969 on 2008-09-14
Beyond repair?  Amazing.  Further up in this thread is a screenshot of my partitions before I messed them up completely.  Can Gparted be used to reconstruct that?

---

### Post by meierfra. on 2008-09-14
> Can Gparted be used to reconstruct that?

No. Gparted can delete and create partitions.   Testdisk can fix  partition table and e2fsck can fix filesystems. Those two are really your best options.  

You  might use testdisk to rewrite your partition table and see whether it makes a difference.  Did you try all the superblock  numbers from testdisk for "e2fsck"? 

When you looked at the filenames with testdisk, were you able to determine whether Ubuntu is on sda3 or on sda4? (judging from your menu.lst it should be sda4)  What is  on the other linux partition?

I'm not sure that anything you or I did, caused your problems. It might just be  that your hard drive is failing.

---

### Post by cp1969 on 2008-09-14
I think I've reached the point where I give up.  I can't continue to pour hours into this thing.  If I have to start over on a fresh hdd, that means I'll have to reinstall all the crap I had installed, including the reliving the nightmare I went through to get the printer working.

I'm off work tomorrow so maybe I'll go computer shopping.  The laptop I'm using is pretty nice, even if it has Vista.  Microcenter has Dell Inspirons for $399.  Or Dell online has XP Inspirons for $279.

---

