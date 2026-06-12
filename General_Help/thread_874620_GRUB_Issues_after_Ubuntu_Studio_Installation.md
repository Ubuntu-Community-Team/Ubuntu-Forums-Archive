---
title: "GRUB Issues after Ubuntu Studio Installation"
date: 2008-07-30
forum: General Help
---

### Post by splatthecat on 2008-07-30
I have been using Ubuntu exclusively for around 8 months now (7.10 -> 8.04) and I am fairly happy with finding my way round (Advanced Newbie!?!?)

Last weekend I downloaded and installed the latest version of Ubuntu Studio on my second HD. On rebooting I discovered that Ubuntu Studio was now the default bootup and I have about 8-10 options (various kernel versions) for my main Ubuntu install. Unphased by this I tried to edit /boot/grub/menu.lst, expecting to see all the various options (the weren't there!) so that I would auto boot into my main install and have the option to boot into "Studio" if I wished. I have searched various Ubuntu/Ubuntu Studio forums, wikis, etc and tried several things without much success so I am asking here for help! Here is what I have tried so far...

Edit /boot/grub/menu.lst from Ubuntu
Edit /boot/grub/menu.lst from Ubuntu Studio
Tried StartupManager from within Ubuntu
Tried StartupManager from within Ubuntu Studio

...I have also tried to use QGRUBEditor in both installs too!

So, what am I left with? The GRUB menu shows Ubuntu Studio at the top of the list, the original installation is shown as "Other Operating Systems" and the default option that is highlighted is the original install but kernel version xxx.16 and not xxx.19 (which is at the top of the list!)

What am I after? My original install at the top of the list (with the most recent kernel version in place) and Ubuntu Studio shown as "other".

Any ideas?

Thanks!

---

### Post by Herman on 2008-07-30
Your computer's BIOS looks for a bootable device in the order you set in the boot sequence and if it doesn't find any other drives with bootable media, it tries to boot the first hard drive.
You should install GRUB to MBR in the first hard disk from whichever operating system you want to have as the main operating system, so you want to re-install GRUB to MBR from your Ubuntu 8.10 in your first hard disk.
While you're doing that, you might as well install your Ubuntu Studio's GRUB to MBR in the second hard disk.
Then, you can add an entry to your Ubuntu's /boot/grub/menu.lst to chainload the second hard disk's MBR.

The following commands assume that your Ubuntu 8.04 in your first hard disk is in partition number 1, and your Ubuntu Studio in your second hard disk is in the first partition also. If your partition numbers are something different, you can still use the followng commands as an example, but you must replace the (hd0,x) numbers in the 'root' commands with some other number which suits your particular set-up.
```
sudo grub
``````
root (hd0,0)
``````
setup (hd0)
``````
root (hd1,0)
``````
setup (hd1)
``````
quit
```Now, boot Ubuntu 8.04 in your first hard drive and,
```
gksudo gedit /boot/grub/menu.lst
```...and add an entry for chainloading your second hard disk,
```
title        Chainload Second Hard Disk's MBR
root        (hd1)
chainloader    +1
```You can copy the above entry and paste it to the bottom of your main Ubuntu's menu.lst file.
Now you should be able to boot either operating system. :)

 [Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")

Regards. Herman :)

---

### Post by splatthecat on 2008-08-04
Thanks Herman! That worked a treat!

:)

---

