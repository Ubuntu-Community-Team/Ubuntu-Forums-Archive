---
title: "Laptop crashing"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by clanky on 2008-03-23
I have a HP pavillion 8000 laptop, which I bought in Germany, was absolutely fine for about 18 months on windows XP (in German!) and then it died completely, took it to a computer repair place in the UK and it needed a new motherboard, I decided to give this a try as I love the machine and a new motherboard was still cheaper than a new laptop.

They fitted a new motherboard and re-installed XP (in English), after this the computer was crashing after about 5 minutes, it would then restart and run fine for hours, until it was switched off.  At first I suspected windows so I decided to give Ubuntu a try,  but although I am loving Ubuntu the laptop still crashes after about 5 minutes and then will run fine until switched off for any length of time and restarted.  

I am coming to the rather expensive conclusion that all is not well in the electronic insides of my beloved laptop, Does anyone have any ideas on what could be causing this?  Like I said above, it crashes completely after about 5 minutes (windows blue screen with error message which disappears and then windows restarts, Ubuntu total crash requiring pull the power lead) and then runs OK all day.

---

### Post by jimbob on 2008-03-23
Try removing the battery and running off the charger for a while and see if the problem persists.

---

### Post by clanky on 2008-03-23
Sorry, should have said, the problem happens whether it is on power or battery, I generally run on mains power with the battery removed.

---

### Post by jimbob on 2008-03-24
Try booting with the kernel parameter [COLOR="Blue"]acpi=off[/COLOR] and see if that makes a difference.

---

### Post by clanky on 2008-03-24
> **jimbob said:**
> Try booting with the kernel parameter [COLOR="Blue"]acpi=off[/COLOR] and see if that makes a difference.

Thanks, how do i do that?

This happens whether I boot in Ubuntu or Windows, i have even tried re-installing Ubuntu on a second hard drive and it still happens.  As soon as it has crashed once it restarts if tunning in Windows (Ubuntu freezes totally and requires the power cable to be pulled and a manual restart) and then runs fine until it is switched off for any length of time.

When it crashes in windows I get a blue screen with an error message which only stays for a second, but it has a message saying beginning dump of physical memory.

---

### Post by jimbob on 2008-03-26
At the bottom of the GRUB boot menu there are instructions for editing the boot parameters.  What you want to do is edit the line that starts with "kernel".  Use the right arrow to get to the end of that line and add a space followed by *[COLOR="Blue"]acpi=off[/COLOR]* 

You may want to also go into the bios and temporarily disable anything that has to do with power settings, auto shut-downs, etc and see if that helps.

---

### Post by clanky on 2008-04-01
Apologies for taking so long to reply, I have added the acpi=off and it has made no difference.

---

### Post by jimbob on 2008-04-01
Since the problem occurs with both ex pee and Ubuntu I would concentrate on the BIOS.  Did you
try anything with that?
  Take it back to the place that installed the new mobo and show them the problem.

---

