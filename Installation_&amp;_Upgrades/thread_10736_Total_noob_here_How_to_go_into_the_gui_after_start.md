---
title: "Total noob here: How to go into the gui after start up?"
date: 2005-01-10
forum: Installation &amp; Upgrades
---

### Post by brensim on 2005-01-10
Hi guys,

Im a total noob in linux (juz tried out linux a week ago), and have decided to try out ubuntu after much positive reviews about it (did try mandrake 10.1 juz prior to this but had quite alot of hardware problems with it).

I've just installed the warty release (normal boot from cd and follow instruction and did an updated when prompted to) however, when i start it i just go into the shell mode (plain text). How do I directly boot into the gui (as in like mandrake when it starts up it goes into kde) ? or rather how do i even start the gui from the shell mode?

Also i did have some error when it is booting hotplug subsystem - hw_random.ko , said it was not found or somthing. Is that to be a major problem too ?

Thanks!
Brendan

---

### Post by sas on 2005-01-11
Type startx to move into X (gui mode) from the shell.

To get X to start at boot you must edit your /etc/inittab file.
Look for the line "id:3:initdefault:" and replace the 3 with a 5 (I'm only assuming this works with ubuntu, it might require a different number, however most linux distros use 5)

---

### Post by CompShrink on 2005-01-11
I'm not sure why your gui isn't starting automatically, does it give you any errors other than the hw_random.ko?

BTW, hw_random.ko is not something to worry about. It's a hardware random number generator module for the kernel. It's on the P4 and some other chips, but the error is harmless, you just don't have that type of hardware. Just ignore it, or add it to the /etc/hotplug/blacklist file.

---

### Post by balajij on 2005-01-11
I'm having similar problems.. I edited the inittab to set it to 5.. However i still do not get the GUI.. 

I'm seeing the some errors related to modprobe.. It reports FATAL failures for pciehp.ko and shpchp.ko

What do these mean and how do I get rid of these errors to get a GUI login? 

I replaced a working windows installation with ubuntu and am seeing these failures. So I'm not sure if it has anything to do with faulty hw. 

pls help..

thanks

---

### Post by wallijonn on 2005-01-11
bren,

You could try just issuing a [COLOR=Red]startx[/COLOR] command. Chances are though that since it faulted to init default runlevel 1 that there is something wrong with your video subsystem. You could try issuing a [COLOR=Red]init 2[/COLOR] command and then a [COLOR=Red]startx[/COLOR] command. 

 Runlevel 0 is halt.
 Runlevel 1 is single-user.
 Runlevels 2-5 are multi-user.
 Runlevel 6 is reboot.

Chances are you will have to redo your XServer configuration. After logging in, issue 
[COLOR=Red]/usr/X11R6/xf86config[/COLOR] (text) or [COLOR=Red]/usr/X11R6/xf86cfg[/COLOR] (gui) to try to re-configure XServer.

---

### Post by wallijonn on 2005-01-11
[QUOTE=balajij]I'm seeing the some [sic] errors related to modprobe.. It reports FATAL failures for pciehp.ko and shpchp.ko[/QUOTE]

This has to do with the hotplug system. You'll need to use the search function (above) to give you pointers on how to resolve your problem(s). Try doing a search for "[COLOR=Blue]pciehp[/COLOR]". My pointing you to /etc/hotplug may serve no purpose. Here's an example of a search for 'pciehp': [http://www.ubuntuforums.org/showthread.php?t=7979&highlight=pciehp](http://www.ubuntuforums.org/showthread.php?t=7979&highlight=pciehp)

---

### Post by CompShrink on 2005-01-11
When I firsted installed i ahd the shpchp and pciehp errors as well. Similar to the hw_random, it's hardware modules that you don't actually need, they're just there for extra features that not everyone has (although a lot of people do).

As I said above, these are harmless, just add them to the blacklist( /etc/hotplug/blacklist ),

This is a debian issue, not ubuntu, and one already filed in the bug trackers, so next kernel hopefully won't have these scary messages.

---

