---
title: "Unable to boot to anything"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by Dangrab34 on 2009-10-22
My system is a 1T drive with C: Vista, D: XP, and D:, E:, F: G: and H: all data drives.  I first tried to install Ubuntu 9.04 on half fo H: that I unallocated.  I was unable to set up a /, home and swap ( because it was at the end of a 1T drive?? ).  I then installed an old PATA 20G drive that I partitioned as 9.5G home, 9G / and 2G swap and installed Ubuntu.  The installation seemed to go great, but when I rebooted at the end after the post it tried to load grub and stopped with grub error 22.  Since I was unable to open the cd drive due to the stop I powered down and manually opened it to put the live installation disk back. 

When I run grub> find /boot/grub/stage1 it returns (hd1,5).  I think the original boot sector was on (hd0,0), the original 1T drive, but I am not sure

I then deleted the partitions, repartitioned and reinstalled Ubuntu.  It is exactly the same situation.  When loading grub everything stops on error 22..

I cannot run anything.  Can someone get me back running?

Thanks,

Dan

---

### Post by Mark Phelps on 2009-10-22
> **Dangrab34 said:**
> ... Can someone get me back running? ... 

Not without some details, we can't.  Run the command "sudo fdisk -lu" (that's a lowercase L, not a one) in a terminal and post the results back here.

Also, post the contents of your menu.lst file so we can see your boot stanzas.

---

### Post by oldfred on 2009-10-22
If you added a pata drive, many BIOS make it the first to boot. Check your BIOS to see if you have settings on which drive boots first. If you can change boot order try that.

If you cannot change boot order post Mark Phelps requests.

---

### Post by Dangrab34 on 2009-10-22
The main problem with complying with your request is the title of my message, that is, I am unable to boot the computer.  I can't get in.   Nothing.  Nada.

I finally gave up and restored an image of my vista disk and even then, I had to repair the vista installation since bootmgr was missing.

In addition somehow my partition with XP on it also disappeared.

So right now I only have vista working and I will have to give a good deal of thought before I start this mess again

Dan



> **Mark Phelps said:**
> Not without some details, we can't.  Run the command "sudo fdisk -lu" (that's a lowercase L, not a one) in a terminal and post the results back here.

Also, post the contents of your menu.lst file so we can see your boot stanzas.

---

### Post by Dangrab34 on 2009-10-22
your point about the pata drive is well taken since now that I am back in vista, disk manager shows the 20G pata as disk 0 and the 1000G sata as disk 1

see my reply to mark to see why I can't post his requests

Dan

> **oldfred said:**
> If you added a pata drive, many BIOS make it the first to boot. Check your BIOS to see if you have settings on which drive boots first. If you can change boot order try that.

If you cannot change boot order post Mark Phelps requests.

---

### Post by oldfred on 2009-10-22
As long as you have a CD or a bootable USB that you installed Ubuntu from you can run all the commands from the liveCD. 

I guess we assumed that. I will be sure to mention that for those with boot issues.

---

