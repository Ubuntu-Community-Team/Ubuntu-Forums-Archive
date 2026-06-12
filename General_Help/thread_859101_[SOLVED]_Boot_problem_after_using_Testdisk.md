---
title: "[SOLVED] Boot problem after using Testdisk"
date: 2008-07-14
forum: General Help
---

### Post by Zatzum on 2008-07-14
Okay, I admit, I accidentally deleted the partition table from my Ubuntu. I used Testdisk and recovered it, and now I can access all files when using the livecd. (After some hours of trying to mount it...)

I can rescue my data now, but still it won't boot from hard drive. I tried some modifications to fstab file and after that I let testdisk make a new MBR file and wrote it. Now it stops loading and shows 1234F. When I press 1, 2 and so on, it just shows another line of 1234F.

I have only one hard drive with one partition. It is set as bootable from testdisk, and I have no idea where the problem could be. Reinstalling just seems so pointless, as everything is fine except the boot-up bit.

---

### Post by ajgreeny on 2008-07-14
At which point of the boot up does everything go wrong?  Do you get to the usplash screen, ie where the growing orange bar appears, or do you get to a grub menu, or is it just a no movement situation after BIOS does the post?

---

### Post by Zatzum on 2008-07-14
Just the no movement situation after BIOS. I'm not sure if I have grub in it... Anyway, there's no command line where you could write anything.

---

### Post by ajgreeny on 2008-07-14
Perhaps try restoring grub, as a first measure, to see if you can at least get to Starting grub prompt, or even a grub menu, if you're lucky.

Boot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

If you don't have windows it will not make much difference to this way as you will still put grub onto the start of the disk at teh "setup (hd0) command.  After doing this there may still be some changes to be made to either one or both of the /etc/fstab and /boot/grub/menu.lst files but they will have to wait for the moment, lets go one jump at a time.

So try restoring grub, then rebooting and let us know where that leaves you.

---

### Post by Zatzum on 2008-07-14
Hmmm... Should I be worried about "root (hd0,0)" says that filesystem is ext2fs and partition type 0x83? I have had the idea that I have ext3 type.

I don't have windows on this machine. So would setup hda1 be fine?

---

### Post by Zatzum on 2008-07-14
Setup (hda1) didn't work, gave error while parsing number, so I tried hd0, reboot and...

woo-hoo, IT'S ALIVE! Everything is perfect again! Thank you :) :D thank you thank you! That would be last time I ever click multiple times on "Are you sure"- notifications before double-checking WHICH device/disk I'm editing.
([http://ubuntuforums.org/showthread.php?t=857432](http://ubuntuforums.org/showthread.php?t=857432))

---

### Post by Cfossy2 on 2010-04-02
> **ajgreeny said:**
> Perhaps try restoring grub, as a first measure, to see if you can at least get to Starting grub prompt, or even a grub menu, if you're lucky.

Boot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

If you don't have windows it will not make much difference to this way as you will still put grub onto the start of the disk at teh "setup (hd0) command.  After doing this there may still be some changes to be made to either one or both of the /etc/fstab and /boot/grub/menu.lst files but they will have to wait for the moment, lets go one jump at a time.

So try restoring grub, then rebooting and let us know where that leaves you.

I also have tried using testdisk to regain a HDD usage but have run into the same problem as ZatZum, but whereas he could get his system up and running, mine does not , even after following the guide to the letter. When I try to sudo grub the error comes back" command not found." When I reboot, all I get is 1234F: repeatedly whenever I type in a letter or a number. I have tried several mothods to reinstall grub2 to no avail, but I know that on my HDD there exists /boot/grub in hd0,1.
Any further advice would be appreciated. I tried to reconfigure grub and all seemed ok but there was another problem as it wanted to know what modules to load.

---

