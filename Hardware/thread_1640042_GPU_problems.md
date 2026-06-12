---
title: "GPU problems"
date: 2010-12-07
forum: Hardware
---

### Post by minigilani on 2010-12-07
Hi

I realize this problem isn't so much OS related, as it is hardware related, but i'm sure someone over here could help me.
.
I'm running a Dell Optiplex GX260 with an Nvidia Geforce4 MX 440 as my graphics card. I was on BIOS revision A03, but it didn't support USB booting so i upgraded to revision A09. My problem is this, whenever i try to boot into a Linux based OS, my monitor shuts off and the light beside my monitor starts blinking brown (contrary to the constant green when on, and constant brown when the the rest of the system is off). I realize this is more a fault with my graphics card because whenever i install Windows, the same thing happens, i have to remove the card, to install Windows. However, once Windows is installed, i plugged the card back in and it works like a charm.
.
I'm booting into Backtrack 4 r1 (it's based on Kubuntu) from a portable USB hard disk via [Katana]("http://www.hackfromacave.com/katana.html"). The Katana menu opens up and offers to boot into any OS i select, however, when i select Backtrack, the monitor shuts off. I'm sure it'll work if i remove the Graphics Card, but i really want to fix this. Is there a BIOS setting i'm missing?
.
.
ps- If you haven't already guessed it, i'm still a bit of a noob, though a mildly educated one.

---

### Post by Fafler on 2010-12-07
There might be some boot options you can pass to the kernel to fix it. You can find some help in the boot menu. Stuff like acpi=off and noapic can often fix these kind of issues.

Another thing, does your machine have a onboard graphics chip? Maybe the kernel detects it and uses that instead. Maybe you can turn it off completely in the BIOS or maybe theres a jumper or switch on your motherboard to disable it. Or another solution is to install Linux using the onboard chip and then make a configurationfile that explicitly uses the Geforce.

---

### Post by minigilani on 2010-12-08
I found [this.]("http://www.noesisinc.com/links/DellDocs/OptiGX260/UserGuide/advfeat.htm#1101564") But the thing is, i've changed all the graphics related settings already, i set my primary video card to AGP, and i enabled Video DAC Snoop (whatever that is).
.
The problem's only started getting worse. Now when i start the system, it doesn't even show the starting DELL splash screen, the monitor starts blinking. I have to reboot again, and again, until it finally starts up properly.
.
There's nothing wrong with the motherboard, before i fried my last one on the same system, it had the same issues with this card, only that was worse, i had to unplug the card and put it away because it wouldn't work at all. The current one is a replacement.

---

### Post by Fafler on 2010-12-08
Try removing the CMOS battery from the motherboard. Or look for a nearby jumper to clear the CMOS memory.

Video DAC snoop is a old hack for something i can't even remember any more. It has nothing to do with this.

Or maybe is it just time to get a new graphics card?

---

### Post by minigilani on 2011-09-04
I've decided that this entire rig is hopeless. Thanks, though!

---

