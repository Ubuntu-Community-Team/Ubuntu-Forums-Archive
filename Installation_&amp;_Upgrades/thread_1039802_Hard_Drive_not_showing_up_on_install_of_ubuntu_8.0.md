---
title: "Hard Drive not showing up on install of ubuntu 8.04/8.10"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by gm1987 on 2009-01-14
Trying to install ubuntu 8.04 or 8.10 on my desktop. When in the partitioning step of install there is no hard drive showing up to partition.

I have tried doing the wubi install but get a initramfs prompt showing up when booting into ubuntu and nothing after that. I have vista installed on the hard drive and reformatting the drive is not an option.

The hard drive i'm trying to install on is a western digital 500GB SATA drive.

I have tried setting drive to AHCI mode as read from other posts that might help.

Please help, new to linux.

---

### Post by cariboo on 2009-01-14
Have you created some empty space on the hard drive? You didn't specfy which version of Windows you sre using, so there are a couple of ways to create empty space. No matter which version of Windows you are using you shlould defrag your hard drive at least twice before making any modifications to your partitions. 

If you are running Vista you can use it's disk management tools to resize the partitions.

If the ACHI setting works you should be able to use the included LiveCD partition editor to create empty space .

Jim

---

### Post by gm1987 on 2009-01-14
I have vista installed and used vista's disk management to shrink the c volume to create 30 GB of empty space, and the AHCI setting did not work.

---

### Post by theozzlives on 2009-01-14
Vista has it's own re-sizing tool. You're supposed to use that.

---

### Post by agsansoo on 2009-01-15
I'm having the same problem. Windows XP install can see the sata disk just fine. Ubuntu can't. It just shows none. Not even gparted can see the disk. Please help !

---

### Post by kranny on 2009-01-15
This might be useful
[http://ubuntuforums.org/showthread.php?t=1039092](http://ubuntuforums.org/showthread.php?t=1039092)

---

### Post by gm1987 on 2009-01-15
I have checked out that thread, problem is neither gparted or fdisk show any partitions or drives at all. I run the commands from that post and the output is blank.

Please help!

---

### Post by zombieman2080 on 2009-01-15
im having the same problem here too, i have a wd 320gb sata, not showing up in any sort of way. have tried partitioning in every way and still nothing, my mobo and xp install can see it.

---

### Post by zombieman2080 on 2009-01-15
does anybody know how to fix this?

---

### Post by agsansoo on 2009-01-15
I solved my problem, maybe this will help others. In the BIOS change the SATA mode to AHCI. Save and exit your BIOS. Then Start linux install with other options (F6 - I think) and enter pci=nomsi at the end of the text line. Then hit enter. Linux now see the SATA drive and installed with no problems. :)

---

### Post by zombieman2080 on 2009-01-15
thanks, i will try this tonight and hopefully i can get better acquainted with ubuntu, the live cd alone is awesome and im sure with full functionality it will be flawless.

---

### Post by gm1987 on 2009-01-15
Thanks everyone for your help, have now successfully installed ubuntu on my vista hard drive and have dual booting setup.

agsansoo - your solution fixed my problem, just enabled ahci in bios and added pci=nomsi by hitting f6

For those that had this problem, after you enable ahci mode in bios make sure to enable ahci in vista so that vista will load with ahci mode enabled. Here is the link for the steps to do that:
[http://tenuouslink.net/blogs/gadgets/2008/01/enable-ahci-mode-after-installing.html]("http://tenuouslink.net/blogs/gadgets/2008/01/enable-ahci-mode-after-installing.html")

And for those that want to setup dual boot with vista, here is the link for that:
[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")


Please help,

Thanks.

---

