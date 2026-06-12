---
title: "Suspend not working"
date: 2008-08-20
forum: General Help
---

### Post by Square on 2008-08-20
Hi all,

I'm a fairly recent convert (I left Windows two months ago) and I don't have any regrets!  I do however have a problem in that my suspend/standby function isn't working properly.  Since I've got a laptop, this is quite an inconvenience.

I believe I actually have two problems in one. Firstly, when I put my computer into suspend mode, the CPU fan never switches off. What's strange is that other than the fan, everything else suggests that the computer is really in suspend mode (for example, the power light flashes as it does when it's in standby with XP). The second issue is that upon exiting suspend mode, the video signal doesn't return, leaving me with a blank screen and no other option but to manually shutdown and lose all my unsaved data.

I have done a bit of googling on this issue to see if others have had the same problems.  I couldn't find anything like my first problem (with the fan not turning off).  On the second problem, there were a couple of similar cases, mostly related to using proprietary graphics drivers.  The solution in almost all cases was to update to the latest drivers.  I've got a Radeon Xpress card and at that stage I had the latest Catalyst drivers available through the Ubuntu repos. That didn't work.  I've since been running the latest Catalyst drivers available directly from AMD/ATI which haven't work.

If anyone has ideas, please let me know.

I'm running GNOME 2.22.3 (Ubuntu 2008-07-09) on Hardy with the 2.6.24-19-generic kernel.

BTW, I'm not sure if it's of any significance but I'm running Compiz as well.

Regards,
Pierre

---

### Post by rudy.elgato on 2008-08-20
Have a look at:

[http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/]("http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/")

I struggled for over a month trying to get my system to resume after a suspend, but as soon as I went through the 6 simple steps listed in Amit's message suspend and hibernate (and Switch User) has worked perfectly.

Hope it helps you.

Good Luck...

---

### Post by Square on 2008-08-20
Hi,

I've got a Radeon and that guide is for nvidia cards so unfortunately it isn't of much help. 

Thanks anyway,
Pierre

---

### Post by Square on 2008-08-20
My problem remains unsolved

---

### Post by Uchiha_madara on 2008-08-20
Check The Ram and the Swap partition

sometimes when the swap partition is very low the suspend and Hibernate don't work

and sometimes the Memory is higher than the Swap Partition 


In Both Cases you need to increase the Swap partition
and be sure it is Higher more than the ram
if the memory is 1G the swap at least must be 1.5GB or more

this is My Experiment in Suspend and Hibernate 

Try and tell me
:guitar:

---

### Post by Square on 2008-08-21
Hi,

My swap partition is around 5GB big and I only have 2GB of RAM.  For some reason though "Swap Total" shows up as "no swap" in SysInfo. Attached are screenshots of that SysInfo page and of GParted (to show the swap partition size).

Regards,
Pierre

---

### Post by Square on 2008-08-21
**Update**

I've thought of something else that might be interfering with my suspend/hibernate - my wireless card.

My laptop has a Broadcom 4318 Wifi card which didn't work out off the box. I eventually managed to get it working using a combination of methods.

Why I think that this might have something to do with it is that each time my computer boots up it displays a console-like screen just after displaying the splash screen and just before displaying the login screen.  A couple of the lines in that screen mention something about the network-manager.  Also, there are some extra modules that need to be loaded to get the wifi to work (I can't remember which ones exactly).

Another thing that pops up in that console screen is something about Parallels (I've installed Parallels which is fairly useless BTW).

If anyone could point me in the direction of the logs I should be looking at, that would be great.

---

### Post by Square on 2008-08-21
BTW, I've found the following modules which are running and are related to my wifi and could be playing a part in my suspend/hibernate problem:

b43
ssb
rfkill
fsaa1655g

---

