---
title: "Getting A31p to work from dock?"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by senor_jt on 2007-01-10
Greetings forum,

I have an IBM/Lenovo Thinkpad A31p and a few days ago I decided to install a new dual boot configuration of Windows 2000 Pro and Ubuntu 6.06(Dapper).  The Ubuntu install went flawlessly!  I haven't tested everything(like Bluetooth support) but I was quite happy about the easy install(vs all the tweaking I've had to engage in on hardware and distributions of years past).

Well, nothing can be that easy it seems.  At least for me.  I performed the install on the laptop sans the dock I often use.  When plugged into the dock, my problems begin...

Per my new googled friend Paul, I discovered what MAY be a functional workaround to the problem cited here, [http://ubuntuforums.org/showthread.php?p=1257154](http://ubuntuforums.org/showthread.php?p=1257154).  In short, my boot partition is /dev/hda2 outside of the dock, but for reasons suggested at in the MULTIPLE threads around the issue, it becomes /dev/hde2 when I boot from the dock.  At the moment, I've just added another boot option to GRUB and will be happy with this...

But that led me to my next problem -- the A31p won't display on my external Dell 2005FPW monitor plugged in through the docks VGA and DVI connectors(yes I use them both.. sometimes switching between VGA and DVI when running Windows.  I can explain if you're curious.)  Anyways, I KNOW there is no shortage of modifying-your-xorg threads but I'm worried that Ubuntu isn't even seeing the monitor connected to the dock and I've tried a few different mods already without success.

So... is there anyone else out there that has gotten your A31p and Ubuntu to work from a docking station?  I've blown inordinate amounts of time already and really want reassurance at this point...

Thanks for "listening" and any pointers you might have.

---

### Post by mk_schmidt on 2007-02-08
I am using my A31p with the ThinkPad Dock ([http://www.thinkwiki.org/wiki/ThinkPad_Dock](http://www.thinkwiki.org/wiki/ThinkPad_Dock)) and the ThinkPad Port Replicator ([http://www.thinkwiki.org/wiki/ThinkPad_Port_Replicator](http://www.thinkwiki.org/wiki/ThinkPad_Port_Replicator)) at work and at home hooked to a 20"-TFT without any problems (via VGA). I am running Edgy and not Dapper though. What´s your screen resolution? My A31 model runs at 1600x1200 (using the 915res package).

---

