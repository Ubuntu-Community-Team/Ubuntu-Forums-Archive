---
title: "Won't boot into windows installation"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by kernel89 on 2009-04-02
Hey, I have only Ubuntu installed into my hard drive. With the help of the gnome partition editor, I resized the total partition so that I can leave some room to install windows XP in order to dual boot.
Unfortunately, after the windows CD reformats the unallocated space, makes a C:/ partition and copies the files, it is scheduled to a restart. After the restart, usually it should boot into the C drive in order to continue the installation, well for me the boot.ini is probably corrupted and it seems like I'm destined to keep booting into the CD which is no good...

Any help? How to I boot into the C drive to resume the windows installation???

-Thanks!

---

### Post by kernel89 on 2009-04-02
Ok, I was able to fix the mbr, by installing grub on it, with this guide: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Still I need to know how to install Windows on a partition.

Thank You

---

### Post by upchucky on 2009-04-02
first the good news, you got grub working.

look here to install xp after ubuntu

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

if you do a bios selectable boot, you can install either os with one drive disconnected, then switch the drives and install the other os with only one drive connected. then connect both drives, this way you can select which drive/os to boot from the bios.

if you have a borked windows that will not boot, you can fix the windows MBR using the win recovery cd and a utility on it called fixmbr. google for instruction on how to do this.

remember that when you fix windows MBR, it messes up ubuntu if both os's are on the same drive but different partitions.

because windows is so poorly built you need fix the grub bootloader again.

---

### Post by kernel89 on 2009-04-03
I actually did all of that before even checking the article, but I just can't see to continu after the XP files get copied. I even moved the unallocated space to the beginning of the Hard Drive, still no luck. I just don't see why it's so hard to install this damn windows!

WOULD SOMEONE TELL ME WHAT IS THE COMMAND TO BOOT INTO A PARTITION. that way I can resume my installation, that's all I need. 
From the windows recovery console or even Grub.

I need to boot into the partition with the copied files so I can resume the download.

---

### Post by Mark Phelps on 2009-04-03
You can't "boot into a partition"; you can only boot into an OS that is installed on a partition. So basically, if you have two partitions, with an OS installed in the first, and you rig GRUB to boot into the second, it will not find an OS and you will either get a blank screen, or some message like "No Operating System", or something else -- you will not get anything useful.

You said that the machine keeps booting the Windows CD over and over.  What should happen is that you get a message like "press any key to boot from the CD" and if you do NOTHING, it will NOT boot from the CD but will attempt to boot from the partition identified in the MBR on the hard drive.

Are you NOT getting the message and it's booting into the CD every time?

---

### Post by kernel89 on 2009-04-03
I don't even get that message, only when I delete the partition containing the copied winXP files, I get the message "press any key to boot from CD" and if I don't hit anything, nothing happens, for the MBR is probably broken. So then I pop in the ubuntu live CD, add the grub to the mbr, and boot into Ubuntu to give you my updates :D

But yeah, not much luck on the installation. I even tried another XP cd I had, same results.

I just don't understand why...

[IMG]http://i41.tinypic.com/2w3yfck.jpg[/IMG]

---

### Post by kernel89 on 2009-04-03
This was after the windows installation copied the files into that 30G partition, as you can see the flag is set as "boot"; I don't know what it means exactly but I think that if I could somehow manage to boot into that partition, I will thereby be able to resume the installation.

[IMG]http://i40.tinypic.com/29ypggp.jpg[/IMG]

---

### Post by ronparent on 2009-04-03
It seems that the windowsm installation so far wouldhave rewritten the mbr. But if that is not the case, you might have to do a windows repair to fix it. If successfule, you of course will have to reconfigure grub using the live cd to getback into the grub bootloader.

---

### Post by kernel89 on 2009-04-03
Al right, well how do I attempt to do a windows repair?
But please note that the windows is not yet installed, only the files are copied to the partition

---

### Post by kernel89 on 2009-04-03
I think I know what to do, but I don't know how to do it.

Basically I want to make the Linux partition inactive so that the only active partition would be the soon to be windows one. That way, after the files get copied I would be redirected to that partition to continu installation.

---

### Post by meierfra. on 2009-04-03
Try this:

Open  a terminal in Ubuntu and open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```

Change

"timeout 3"   to "timeout 10"

and

"hiddenmenu" to  "#hiddenmenu"

add this to the very end of the file:


title Windows XP
rootnoverify (hd0,0)
chainloader +1

Save the file and reboot. The Grub menu should appear. Pick "Window XP"  and see whether you can  boot into XP.

---

