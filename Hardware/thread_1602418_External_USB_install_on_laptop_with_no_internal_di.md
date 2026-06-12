---
title: "External USB install on laptop with no internal disk"
date: 2010-10-21
forum: Hardware
---

### Post by John 94306 on 2010-10-21
Hello,

I apologize if this has been answered.   I couldn't find anything in a search...

I have an HP laptop with a dead internal hard drive controller.  I believe that it is otherwise fully functional. I am trying to install ubuntu server on an external USB drive.  The installation works fine, but the machine then boots to grub, which seems to be a sign of trouble.  Attempts to hand boot from grub fail, possibly due to user ignorance.

I created an installer on a USB stick using the Windows install creator.  When I power up the laptop, it runs the installer with no complaints.  After that, I remove the stick and cycle the power.  At that point, I end up in grub as already mentioned.  I don't mind having to boot manually from grub, if that is the best way to proceed, but I can't even make that work.

Thank you in advance for any answers.

Regards,
John

---

### Post by P4man on 2010-10-21
If you install to an USB stick or drive, make sure you also put grub on that same stick/drive. IN the installer in the last step there is an "advanced" menu that lets you do that. If you dont change it there, you may will end up with grub on the internal drive and not on the USB one.

---

### Post by John 94306 on 2010-10-21
Thank you for the tip, P4man.  Since there is no internal drive and grub is running ,I am quite sure it was installed on the external USB drive.

> **P4man said:**
> If you install to an USB stick or drive, make sure you also put grub on that same stick/drive. IN the installer in the last step there is an "advanced" menu that lets you do that. If you dont change it there, you may will end up with grub on the internal drive and not on the USB one.

---

### Post by C.S.Cameron on 2010-10-21
Have you checked the isos MD5SUM?
You might also check the USBs grub.cfg file to confirm the path to the install is correct, ie that installing from flash drive did not screw it up.

---

### Post by spello on 2012-04-02
Hi everybody. I am having exact the same trouble as the user, who created this thread.

Notebook without internal disk (dead disk). So I decided to install Ubuntu 11 on an external data disk. Which had an old Ubuntu 9 (I guess), which wasn't functioning long ago.

/dev/sda1 - 450GB NTFS
/dev/sda2 - 25 GB ext3 
/dev/sda3 - Swap

Booting up the burned ISO, chose install, chose "other action", clicked the ext3 to link as root dir  aka " / " with format to ext3, chose swap as swap. Set to install the grub into the /dev/sda. Finished with no trouble at all, after "Please remove the install media and Enter" I was all shiny "This was really easy, wasn't it" ... it went to:

Unknown filesystem.
grub rescue >

With shiny feeling gone, I rebooted, started up the burned image again. My data partition (NTFS /dev/sda1) was intact, /dev/sda2 was looking good with all the directories You would expect from a root dir " / ".

checked with that original file tool ... fdisk, that the /dev/sda2 partition with fresh Ubuntu 11 was the active partition (with the star sign *)

So ... wanted to use grub to install it again ... I mounted --bind /dev/... and those really important directories and then called chroot.

I ran grub-probe -d /dev/sda, which gived me exact the error with the filesystem.
so I did grub-install to /dev/sda ... and it did say all went ok.
grub-probe again and the problem prevailed. After reboot, the problem was still unresolved.

Any hints, what could be the problem ?
I might even take an advice like grub rescue sequence of commands, which could bring it to start ...

Thanks for Your time!

---

### Post by Bill Z on 2012-04-02
Have either of you guys gone into the BIOS and deleted the HDs?  It occurred to me that the OS does talk to the BIOS and even though the HD controller is bad, the OS may be still trying to access it.  

Just a thought.

---

### Post by spello on 2012-04-02
I took out the internal disk before installing the Ubuntu on the usb external one.

Or did You mean that I should disable the disk detection in bios ?
I hope disabling all what has something to do with an internal disk in bios options won't be necessary.

---

### Post by oldfred on 2012-04-02
Run this from liveUSB to get boot info script. 

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by spello on 2012-04-03
Hi there,

I have inserted a temporary internal disk, which won't be staying there (one partition 500GB) just to see if it helps, ... it didn't.

So I tried this, I have to say nice tool, You've suggested.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Booted the Ubuntu LiveCD. apt-get as the page says, without trouble, started Boot-Repair.
Firstly just the "default" action. Then with the advanced options: install on the /dev/sdb, purge and install Grub2, without reset extra space after mbr, without ata-disk out-of-disk option. (I guess I didn't mount --bind /boot ..., when it asked me to apt-get purge and install ... if this still can be the cause ?)
Procedure didn't help. Still he unknown filesystem message remains.
Actual setup is: [http://paste.ubuntu.com/912266/](http://paste.ubuntu.com/912266/)

So I digged more and tried this out, with no results:
[http://forums.techarena.in/operating-systems/1414423.htm](http://forums.techarena.in/operating-systems/1414423.htm)

I digged even more, because it became a real challenge I want/need to overcome!
[http://sazeit.com/articles/boot-ubuntu-from-grub-prompt](http://sazeit.com/articles/boot-ubuntu-from-grub-prompt)

_ls command:_
according which disk I choose to boot it changes, never the less ... booting from the external disk is prio, so I press ESC to boot menu (BIOS) and let the external media to boot.

ls results to: (hd0) (hd0, msdos3) (hd0,msdos2) (hd0,msdos1) (hd0) (hd0,msdos1)
which is fine. The partition with Ubuntu is (hd0,msdos2)

_ Proceeding with next step set command:_
set prefix=(hd0,msdos2)/boot/grub
set root=hd0,2  (or msdos2 ... tried both 2 and msdos2)

insmod ext2  (without error - ok) - ext2 should be able to handle ext3,4 as well
insmod part_msdos (without error - ok)

_ next step, show content of /boot to determine vmlinuz and initrd.img:_
ls -l /boot    -> results in unkown filesystem !!!!  ... why is this still here ?
so I did:  ls -l (hd0,msdos2)/boot   ... and ls -l (hd0, 2)/boot ... still unknown ...
I even tryied all of the combinations the `ls` wrote, without the partitionless descriptor (hd0) (hd1)

next step would be use of commands like linux, initrd and root,
but this is not possible without the /boot/grub directory -> command not found

_Boot files are there:_
ls -l /boot/
total 21812
-rw-r--r-- 1 root root   730503 2011-10-07 22:02 abi-3.0.0-12-generic
-rw-r--r-- 1 root root   134754 2011-10-07 22:02 config-3.0.0-12-generic
drwxr-xr-x 3 root root    12288 2012-04-03 01:53 grub
-rw-r--r-- 1 root root 13731702 2012-04-02 20:17 initrd.img-3.0.0-12-generic
-rw-r--r-- 1 root root   176764 2011-05-03 01:07 memtest86+.bin
-rw-r--r-- 1 root root   178944 2011-05-03 01:07 memtest86+_multiboot.bin
-rw------- 1 root root  2694177 2011-10-07 22:02 System.map-3.0.0-12-generic
-rw------- 1 root root     1367 2011-10-07 22:08 vmcoreinfo-3.0.0-12-generic
-rw-r--r-- 1 root root  4658096 2011-10-12 16:34 vmlinuz-3.0.0-12-generic


grub-probe -d /dev/sdb2  -> says "ext2"
(info, /dev/sdb2 is the external drive address after I boot the LiveCD)

```
root@ubuntu:/usr/lib/grub# apt-get install grub2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 357 not upgraded.
root@ubuntu:/usr/lib/grub# 

root@ubuntu:/usr/lib/grub# grub-install /dev/sdb
Installation finished. No error reported.
root@ubuntu:/usr/lib/grub# 

root@ubuntu:/usr/lib/grub# grub-mkconfig -o /boot/grub/grub.cfg 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/usr/lib/grub# 
```Should I reinstall the grub2 with ussage of mount --bind ... am I missing something ?
Reinstalled via the Boot-Repair, but I couldn't start it or apt-get it after doing chroot.
```
Boot successfully repaired.
Please note the following URL:
   http://paste.ubuntu.com/912266/
   In case you still experience boot problem, indicate this URL to:
           boot.repair@gmail.com 
or to your favorite support forum.
You can now reboot your computer.

```

---

### Post by oldfred on 2012-04-03
I do not see an issue in boot script. Are you booting from sdb. But both installs of grub to MBRs look like they should work.

There used to be an issue with old BIOS and newer hard drive that would boot only from partitions fully inside the first 137GB. We have seen a similar issue and it seems to be BIOS settings that may be set to legacy or the old 137GB limit. 

Some quotes from others:
> 
It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 


---

### Post by spello on 2012-04-03
It was a good hint with that AHCI. Unfortunatelly the "Sata mode" is / was set to "enhanced".
As my notebook doesn't have IDE ports ... enabling anything would be hard :)

Upgrading BIOS scares me out a bit.
Do You think upgrading BIOS would be usefull in this matter
for an Asus N61Vn 2.5-3 years old mobo? (ment no sarcasm here)
[http://www.asus.com/Notebooks/Multimedia_Entertainment/N61Vn/](http://www.asus.com/Notebooks/Multimedia_Entertainment/N61Vn/)

After spending 3 evenings I am no longer amused by searching for the reason,
which shouldn't present such a problem. It is "just" a bootloader, isn't it :)

I feel like there is a small brick missing in the big puzzle.
The whole puzzle looks good on the wall, but the brick is still missing :)

I will try to solve this riddle, as I know that something like disk errors, data corruption
and the need to reinstall system has happened and will happen again.
Happy to hear about any ideas, keep them coming.

Thank You for Your effort.

---

### Post by oldfred on 2012-04-03
When you did this set root=hd0,2 was the other drive plugged in so it was sdb2? If so then it may be hd1,2? Normally the drive you boot from is hd0, but if you booted from sda's MBR then it may be hd1.

This sometimes bypasses grub & gets you to boot:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

---

### Post by spello on 2012-04-04
Gosh I wrote it wrong, all hd's here are hd0 ... eh ...
> ls results to: (hd0) (hd0, msdos3) (hd0,msdos2) (hd0,msdos1) (hd0) (hd0,msdos1)Both drives were plugged in yesterday, alltime ... because I was too lazy and didn't want to screw drive it back out again :)

If booting from the external disk (prefered) - 3 partitions (ntfs data, ext4 ubu, swap swap)
ls writes (hd0) (hd0, msdos3) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos1)

When booting from the internal - 1 partition (ntfs data)
ls writes (hd0) (hd0,msdos1) (hd1) (hd1, msdos3) (hd1,msdos2) (hd1,msdos1)

I am pretty sure I wrote the "x,msdos2", where X is the one mentioned above with the msdos2 partition. Never the less, as it didn't work out, I tried all of them ;)

This makes me worried, becuase it looks like directly relevant to the "unknown filesystem" message.
I just might try to reinstall it again on the ext2 FS.
> grub-probe -d /dev/sdb2  -> says "ext2"
(info, /dev/sdb2 is the external drive address after I boot the LiveCD)I will read more about this super grub and try it laterz, after coming back from work.
Thank You very much.

---

