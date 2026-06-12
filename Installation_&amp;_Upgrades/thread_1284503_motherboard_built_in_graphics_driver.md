---
title: "motherboard built in graphics driver"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by brain frog on 2009-10-06
Hello

I am still getting used to linux and if i am correct in linux it is called kernel not drivers, i am sure someone will tell me if i am wrong.

I am trying out linux using an old pc and sofar i am very much liking linux and am still learning, my latest issue is graphics i am currently using this motherboard [http://www.e4allupgraders.info/dir1/motherboards/socket754/msi6741.shtml](http://www.e4allupgraders.info/dir1/motherboards/socket754/msi6741.shtml) the system consists of that motherboard 1 gb of ram can run at 400 but only seems to be at 333, might need bios update its a good time to try pulling one off for the first time a amd 64 single core 3400+ and a very old 40gb hard drive.

I have not added any hardware drivers/kernel  i clearly need some for its visuals as its very poor at times, i cant find any sign of any linux support for this mobo.

Can anyone help me out or is my system already using it to its full graphics potential?

Thanks

---

### Post by lindsay7 on 2009-10-06
Have you look at System/Administration/Hardware Drivers?  This is where you would find out what drivers you may setup for your system.

You may want to look for a cheap video pci or agp card to add to this system. You could try ebay or newegg or tiger direct.

---

### Post by ghostborg on 2009-10-06
After "Hardware Drivers" as above check Preferences>Appearance>Visual Effects tab click on normal or Extra effects. Then install through synaptic package manager, compizconfig-settings-manager to tweak your compiz desktop.:guitar:

---

### Post by brain frog on 2009-10-08
Hardware Drivers was empty no options and nothing in there.

I also attempted slotting in an old ati 9250 with a passive heatsink, it seemed faster but it was evident that drivers were needed but still Hardware Drivers had nothing in it.

What would be the best way to proceed?

Thanks

---

### Post by Mark Phelps on 2009-10-10
Your ATI card didn't help because it's too old for the ATI drivers that run with Ubuntu 9.04 and newer.  As afar as I know, the only restricted video drivers are for ATI and Nividia cards.  Since your mobo uses integrated Via graphics, you are stuck with the graphics driver installed by default.

---

