---
title: "Error when &quot;Loading hotplug subsystems&quot;"
date: 2006-01-01
forum: Installation &amp; Upgrades
---

### Post by Abyssal on 2006-01-01
When I use a LiveCD to boot up, it works great until it starts to load the hotplug subsystems. Then it just sits there. I let it sit for about 1 hour, and nothing happaned.

If someone could please help me with this, I would be forever grateful.

Thanks!

---

### Post by kaamos on 2006-01-01
Try pressing control+c when it starts loading the hotplug subsystem. This could work.

---

### Post by Abyssal on 2006-01-01
K, I'll try that, What does it do tho?

BRB, I'll check back with here in 10 minutes.

---

### Post by Abyssal on 2006-01-01
Nope, didn't work.

---

### Post by Jeff12088 on 2006-01-01
Do an error check on your live CD to find out if the CD is faulty burned or not.

---

### Post by Abyssal on 2006-01-01
How do I do an error check?

Sorry, I'm completely new to Linux and LiveCD's -.-

---

### Post by Jeff12088 on 2006-01-01
I'm not exactly sure how to get to the live cd menu, but an easy way to do it is restart your system and boot in the live cd again. Whenever you have the chance to choose "go back", do it and you should see a list of options.

You might not even have access to the menu. Did you get to select your keyboard, location, etc? If you did, you should be fine.

---

### Post by Abyssal on 2006-01-01
Yes, I selected my keyboard, country and stuff, but thats before the loading hotplug subsystem.

---

### Post by Jeff12088 on 2006-01-01
Try what I said, reload the live cd and choose "go back" to return to the list of options. In the list, you should be able to see something like "CD error check".

---

### Post by Abyssal on 2006-01-01
Nope, no errors. Still the same thing :mad:

---

### Post by William_in_Kanata on 2006-01-01
There is a bug report in Bugzilla, reported in early December, but I can't see that there has been any action to fix the problem. It was suggested at one point to try the Dapper Flight-2 release, to see if that fixes the problem, but I can't get that to even install at the moment. 

It seems to be associated with Video and PCI (reading between the lines in Bugzilla) but no one seems to know why. In my case, I am using the Video control that is on board the motherboard (ATI Radeon Xpress 200) so no card in a PCI slot, but presumably it communicates by some sort of PCI bus integrated into the motherboard itself.

Sure hope someone with some knowledge is reading this forum. Maybe they can suggest options.

---

### Post by Eddos on 2006-01-04
I am experiencing the same problem on my Asus A6Va with a Live CD from Ubuntu(5.10)

---

### Post by CzarAlex on 2006-01-04
I had the same prob. For me, its the onboard sound card. I had to disable it in the bios for the hotplug system to start. However, you`ll have no sound then. I hadda install a $5 sound card I had. 

If you didnt wanna fiddle with the bios, you can hit Ctrl-C right as the hotplug initialization message comes up but you have to do it REAL fast, else it gets stucks on the onboard sound.

---

