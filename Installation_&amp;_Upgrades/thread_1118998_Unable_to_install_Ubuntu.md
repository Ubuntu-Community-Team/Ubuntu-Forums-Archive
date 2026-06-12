---
title: "Unable to install Ubuntu"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by rian4me on 2009-04-07
I had asked a question earlier

================================================================
I have win xp sp3 on my c drive
I tried installing ubuntu 8.04 on to my d drive by making
c drive as mount point "/windows"
and d drive as mount point "/" with ext3 format
and a small 2 gb e drive as swap space
the problem is it installs everything properly and then when it asks to restart and i do so
Windows xp just boots up directly to the progress bar screen

no grub loader is shown
i did this many times and it doesn't work
Help
Please don't direct me to a tutorial for step by step installation procedure, i have already read lots of those

just tell me what could be the possible problem and how to solve it
================================================================

The best answer i got was


=========================================================

OK -- no tutorials ...

Where'd you install GRUB. To the MBR? Or to the Ubuntu root partition?

To find out, boot from the LiveCD, open a terminal, and do the following:
1) enter "grub"
2) enter "find /boot/grub/stage1"

That will indicate where GRUB is installed.
=========================================================

but the replier didnt want me to PM him so i'll ask publicly what i PM ed him

Can someone tell me what i am ideally supposed to get when i execute the above mentioned command
Please specify in exact terms where during the installation procedure am i supposed to select the location to install this GRUB and which location should i choose to install it so that it is loaded when the system boots up

As i said, I request u to state in exact step by step procedure 
please.
No vague comments and opinions, BE TECHNICAL

---

### Post by upchucky on 2009-04-07
boot from the live cd then download this

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then do this

```
sudo bash ~/Desktop/boot_info_script*.sh

```

this shows exactly what is on the drives so post the results of the diagnostics here we can advise from there

I suspect that the grub bootloader must be set up on the second hard drive to be able to boot ubuntu, or if you do not want to bios boot one or the other os than grub must be set up on the first drive which sets up a dual boot. So indicate if you want and are able to boot from bios selectable device or want to dual boot from the grub menu.

eg: my bios lets me press F12 to have the option of booting from harddrive, usb, dvd, floppy, or network when the pc powers up. The boot options had to be enabled in my bios settings first though.

do not pm me, it is better that everyone sees so if they have same problem it helps them too to see the problem and possible solutions.

---

### Post by ronparent on 2009-04-07
You basically got what you asked for! To explain, the response to the find commands tells us where the grub files are located (only normaly in /boot/grub). For a presumably normal install you would configure grub by continuing from there as follows:

grub> root(?,?)    ##using the output of find
grub> setup (hd0)  ## writing the grub boot leader to the mbr, overwriting the windows mbr

with that done, a reboot should bring up a grub menu allowing you to boot either ubuntu or windows. Dependin on how d: was formatted there should be no d: per se.

---

