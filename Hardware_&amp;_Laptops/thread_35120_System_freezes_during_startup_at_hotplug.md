---
title: "System freezes during startup at hotplug"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by ubuntuwow on 2005-05-17
Specs:
Dell 2300 Dimension (probably my problem right there)
ATI 9200 PCI graphics card

I just installed ubuntu today and love it. Just one problem, the only way I can get it to boot is to take out my ATI graphics card. I tried unplugging all of my usb devices, speakers, and etherent cable. 
I am somewhat experienced in Linux....not a complete newb, but not an expert either.
Any help would be greatly appreciated.

---

### Post by defkewl on 2005-05-17
What is the error message?
Try using :
$ dmesg

Then paste it here.

---

### Post by ubuntuwow on 2005-05-17
There is no error message. What happens is that when it gets to the line 
"Hotplug subsystem starting" during boot, my computer just stops accessing. But, taking out my graphics card fixes the problem.

---

### Post by zencoder on 2005-05-17
How long have you left it in this state?  I've noticed my Thinkpad T41 can seem to hang for a few minutes at the Hotplug and/or Network steps.  If I leave it be, it boots up within a minute or 3.

---

### Post by nad on 2005-05-18
In your bios setup, have you enabled an irq for the graphics adapter?

---

### Post by wiraone on 2005-05-18
[QUOTE=ubuntuwow]Specs:
Dell 2300 Dimension (probably my problem right there)
ATI 9200 PCI graphics card

I just installed ubuntu today and love it. Just one problem, the only way I can get it to boot is to take out my ATI graphics card. I tried unplugging all of my usb devices, speakers, and etherent cable. 
I am somewhat experienced in Linux....not a complete newb, but not an expert either.
Any help would be greatly appreciated.[/QUOTE]
 Edit the Grub kernel line and add NOAPIC at the end during the boot up time .. if this solve your problem, add it permanently in the /boot/grub/menu.lst .. Had problem with IRQs and this solved my problem ..

---

### Post by nocturn on 2005-05-18
I will try that too.

I have the exact same problem on my Lattitude CPiA

---

### Post by ubuntuwow on 2005-05-21
Update:

Still no luck on getting my comp to boot with my ati card in. Here are some more specs on my computer.

Dual boot with winxp
Dell Dimension 2300
1.80 ghz pentium 4
1 gb ram
1 pci etherent adapter
1 pci modem
1 pci ati 256mb 9250 
built in intel 845gl graphics card(could two graphics card be the problem?)

I tried noapic, acpi=off, pci=noacpi and other commands by themselves and together...no luck. I'm almost to the point of just going out and buying an nvidia like i probably should have in the first place, but i dont really have the money to waste right now.

Once again, any help on this would be greatly appreciated.

---

### Post by nad on 2005-05-21
See if there is a bios option to make the agp port the primary graphics adapter. And have you yet checked the bios irq options?

---

### Post by ubuntuwow on 2005-05-21
I've checked my bios, and unfortunately it is very limited. No options for setting irq on anything except for a few limited choices for serial and parralel ports, I wish that I could just remove the Intel 845 agp, but the stupid thing is built in on the motherboard. I also dont even have any real agp slots, so i can only use pci if i want to use a better video card than the crappy 32mb intel. The ati card works fine with windows, so it does work atleast. 

I was using hoary, but I decided to try breezy and I am getting error messages with that one atleast. "Fatal error syncing..X couldent start" or something like that.

I'm back to trying hoary again. I tried expert mode to see if I could choose to not install anything for the intel, but I could not find out which hardware module, if any, was for the intel.

I wonder if I could just boot up with my ati out so I could get in, and than blacklist the intel in hotplug. But, I'm not exactly sure how to do that, and what syntax I should put to block it.

This is not the only version of linux that I've had problems with this. Fedora, vidalinux, newest knoppix, and slax all don't work. Only one that does work is knoppix std.

---

### Post by xenblend on 2007-08-09
I know this thread is two years old, but I am having the same exact problem with a Dell Dimension 2350 (almost the same exact setup that was mentioned above).  I have a PCI ATI Radeon VE/7000 graphics card and if I try to boot up any version of linux (even Knoppix!) with the add-on ATI card, it freezes up during boot.  It worked fine when I didnt have the ATI card, and just used the Intel 845 chipset graphics.  Can anyone help me?  Did anyone ever fix this problem?

xb

---

### Post by detroit/zero on 2007-08-09
I had the same problem on an HP Pavillion with an Nvidia GeForce card and an Intel on-board graphics controller. 

You will, obviously, want to make backups of everything before you start. Don't hollar at me if you don't.

What you have to do is, while running without the video card enabled: 

-install your drivers
-edit *xorg.conf*
-create */etc/hotplug/blacklist*
-create */etc/modprobe.d/blacklist*

Installing drivers I will assume you know how to do.

Editing xorg.conf I will also assume you know how to do.

*/etc/hotplug/blacklist* is easy.  In terminal type
```
sudo gedit /etc/hotplug/blacklist
```It will, of course, be a blank file if you don't already have it. In it, write the following:
```
intel_agp
agpgart
```*/etc/modprobe.d/blacklist* is a little trickier. In terminal type
```
sudo gedit /etc/modprobe.d/blacklist
```Again, starting with a blank file (if not blank, go to the bottom of the listed items) and enter the following:
```
blacklist intel_agp
blacklist agpgart
```See the difference? I don't know why, but everything else in that file (on my pc, anyway) has "blacklist" written before it, so I just went with it..

After all those are done, close everything out and restart the system. When the time comes, hit F1 or whatever gets you into BIOS when you need to. Set the PCI as your primary display (or do whatever you have to do to select your video card). IRQs and all that should be assigned automatically.. don't monkey with it unless you have to and if you know what you're doing. 

Save changes and exit BIOS. I don't know if it's an option, but if you can, power the system down totally when exiting. If not, after it resets, hit the power button to power off the computer. Swap your cables and do whatever else to run your monitor off your video card.

Power on, and with some luck, all should be well.

Hope that works for you!

---

### Post by fearlex on 2007-10-25
I have EXACTLY the same problem, it sound like is something related to the Intel 845 chipset graphics and another video card. Yes !! blacklisting the intel_agp and the agpgart modules on /etc/modprobe.d/blacklist work, but for that i have to open my computer and remove my video card, install ubuntu and then do the blacklisting and put everything back. 

Have someone find out a way to blacklist those modules using the live CD the first time an installation is going to happen, and WITHOUT having to remove the video card ??

God, i havent switch totally to Linux 'cause of this, is quite annoying and really frustrating.help 

Please help !!!!

---

### Post by saphyrre on 2007-11-15
Needless to say, same crappy intel onboard memory was giving me a hard time... until i blacklisted it.
To do this with a live cd, go in bios, set up onboard intel as primary device, connect the monitor to the intel onboard video, and you should be able to boot from live cd. Install nvidia or ati drivers (i use envy for that), edit xorg.conf, blacklist intel modues, reboot, and in bios change the default video to pci.
That's it.

---

