---
title: "Continuous have to Flash BIOS to boot"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by PhilTechLV on 2009-03-03
I recently installed Ubtunu 8.04 on a home built PC my dad and I created about 3 years ago. 
Specs:
Pentium 4 Processor
2 Gigs of FBDimms
Soyo SY-P4VTE Motherboard
Verto GeFore4 MX/Ti VGA card


For some reason every time that I shutoff the computer I have to flash the BIOS and select a BOOT device to get it to boot into Ubuntu.

I don't have a floppy drive on this computer but that is what the first boot device is set to, apparently it won't allow me to set CD as the first boot drive.

I believe it has something to do with GRUB but I don't know how I would test that.

Any help would be greatly appreciated.

---

### Post by Perryg on 2009-03-03
> **PhilTechLV said:**
> I recently installed Ubtunu 8.04 on a home built PC my dad and I created about 3 years ago. 
Specs:
Pentium 4 Processor
2 Gigs of FBDimms
Soyo SY-P4VTE Motherboard
Verto GeFore4 MX/Ti VGA card


For some reason every time that I shutoff the computer I have to flash the BIOS and select a BOOT device to get it to boot into Ubuntu.

I don't have a floppy drive on this computer but that is what the first boot device is set to, apparently it won't allow me to set CD as the first boot drive.

I believe it has something to do with GRUB but I don't know how I would test that.

Any help would be greatly appreciated.

Sounds more like the battery has died on the motherboard.  Thus the reason to tell BIOS what it needs each time you turn it on.

---

### Post by PhilTechLV on 2009-03-03
That would make sense. I just reformatted the computer to Ubuntu from Windows 7 yesterday. It worked fine in Windows 7, so I need to go get a new battery for the motherboard to test that. Is there any way to find out without buying a new battery?

---

### Post by Perryg on 2009-03-03
> **PhilTechLV said:**
> That would make sense. I just reformatted the computer to Ubuntu from Windows 7 yesterday. It worked fine in Windows 7, so I need to go get a new battery for the motherboard to test that. Is there any way to find out without buying a new battery?

Sure!   If you turn it off and unplug it for a minute or so and turn it on and look at the BIOS.  See what the date and time say.  If they are wrong your battery is more than likely dead.  Or weak in which case it might take longer for it to fail.

---

### Post by PhilTechLV on 2009-03-03
Well, I just tested the battery (we have a battery tester downstairs apparently) the battery is in great condition. So, any other suggestions?

I'm trying to change the Boot order to see if that helps, I'm going to look around at other settings as well see if anything might affect it.

---

### Post by Perryg on 2009-03-03
> **PhilTechLV said:**
> Well, I just tested the battery (we have a battery tester downstairs apparently) the battery is in great condition. So, any other suggestions?

I'm trying to change the Boot order to see if that helps, I'm going to look around at other settings as well see if anything might affect it.

Did the time and date show the correct information?  Rememeber that if the battery were weak it may take longer than a few minutes.

Other causes: dirty connection with the battery, weak or dead battery, poor solder joint, Broker path on the board (at battery) or the worst case situation is faulty BIOS chip.

It all depends on the information you get when you turn it on after setting for a while (time and date are the indicators).

---

### Post by PhilTechLV on 2009-03-03
Actually I don't think I can get to a screen with the time on it, I've tried, but nothing sits for any length of time, and I continuously have to run setup. The part that holds the battery does wiggle quite a bit, I'm assuming that all fo these issues would require replacing the motherboard?

p.s. My motherboard in setup believes that it is April 15, 2004 00:03:10

I think that's how long the computer has been on. this last time.

---

### Post by Perryg on 2009-03-03
> **PhilTechLV said:**
> Actually I don't think I can get to a screen with the time on it, I've tried, but nothing sits for any length of time, and I continuously have to run setup. The part that holds the battery does wiggle quite a bit, I'm assuming that all fo these issues would require replacing the motherboard?

p.s. My motherboard in setup believes that it is April 15, 2004 00:03:10

I think that's how long the computer has been on. this last time.

Most MB BIOS screens have the time and date indicated in the general tab.  When it boots up try hitting the delete key, or F1 to get into the BIOS and see.  If the battery is loose it may be that you can tighten it a little and prolong the replacement, unless you know how and have the tools to solder it back in tight.

---

### Post by PhilTechLV on 2009-03-03
> **Perryg said:**
> Most MB BIOS screens have the time and date indicated in the general tab.  When it boots up try hitting the delete key, or F1 to get into the BIOS and see.  If the battery is loose it may be that you can tighten it a little and prolong the replacement, unless you know how and have the tools to solder it back in tight.

I don't know how to solder, but both my mom and dad do, and I think they have the tools.

I can't get in to anything if I don't Flash the motherboard. It goes to a black screen I hear the cd drive try to read something (even though there's nothing in there) and it just sits there not doing anything.

---

### Post by Perryg on 2009-03-03
> **PhilTechLV said:**
> I don't know how to solder, but both my mom and dad do, and I think they have the tools.

I can't get in to anything if I don't Flash the motherboard. It goes to a black screen I hear the cd drive try to read something (even though there's nothing in there) and it just sits there not doing anything.

So I guess my next question is how are you flashing the BIOS?  Then I would need to know what exaclty does it do when you flash it?

---

### Post by PhilTechLV on 2009-03-04
I move the jumper from the two pins it's on during run time over one, like it says in the documentation. (maybe flash is the wrong term) It resets my settings (it doesn't allow me to start cause it says the BIOS settings are incorrect) I then can press F2 to do default BIOS settings and it will boot all the way, but if I change the BIOS settings at all I have to re"flash" it again.

---

### Post by Perryg on 2009-03-04
> **PhilTechLV said:**
> I move the jumper from the two pins it's on during run time over one, like it says in the documentation. (maybe flash is the wrong term) It resets my settings (it doesn't allow me to start cause it says the BIOS settings are incorrect) I then can press F2 to do default BIOS settings and it will boot all the way, but if I change the BIOS settings at all I have to re"flash" it again.

OK we are getting somewhere.  What you are doing is actually a BIOS reset.  This wipes out all data and puts it back to factory default.  The next thing is to go ahead and let the BIOS do its thing.  You should not need to do any adjusting if it is fully automatic.  I will look at the first of this and see what you are using.   Now I need to ask why do you or are you changing the settings?  Does it not see the right drives?  Give me some more information on exactly what you do and why to get this to boot.

Below is how to setup your BIOS.  Follow and you should not need to do this again.

Step 1. Select [STANDARD CMOS SETUP]
Set [Date/Time] and [Floppy drive type], then set [Hard Disk Type] to &#8220;Auto&#8221;.

Step 2. Select [LOAD Optimal Settings]
Select the &#8220;LOAD Optimal Settings&#8221; menu and type &#8220;Y&#8221; at the prompt to load the BIOS
optimal setup.

Step 3. Select [Exit]

Press <Enter> to save the new configuration to the CMOS memory, and continue the boot
sequence.

---

### Post by PhilTechLV on 2009-03-04
Ok, so here are the exact steps I go through when I change anything:

reset CMOS
plug in computer
turn on computer
press F1 (enter CMOS setup)
change the boot order to IDE-0, CD/DVD-0, none
save and exit.

it restarts and goes to the standard black screen that tells me it's not working again.


When it works:
reset cmos
plug in computer
turn on computer
press F2 (Use default settings for CMOS and continue).
It succesfully boots to the login screen for Ubuntu 8.04


I believe you're right that the connections for the MB battery are faulty, cause it appears to be working intermittently, It has booted up twice now without having to reset the CMOS.

---

### Post by cariboo on 2009-03-05
A bad CMOS battery will not necessarily read low, it may read over 3 volts.

Jim

---

