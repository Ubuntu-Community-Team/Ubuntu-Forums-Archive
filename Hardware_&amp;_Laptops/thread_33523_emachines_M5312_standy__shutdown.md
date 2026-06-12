---
title: "emachines M5312 standy / shutdown"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by Zelut on 2005-05-11
I'm having an issue with my M5312 notebook by emachines.  Everything is working great, including the wireless (I'm so pumped!) but if I close the display it'll go into a 'standy' mode that doesn't recover.

Here are the steps...

Close the display - LEDs continue to flash as if everything is still grindin' away

Open display - gnome interface is still displaying... for two seconds

Goes into blank screen (which I'm only guessing is some standy mode effort)

I can't get any responds (thru keyboard, mouse, etc) unless I push the power button.

This results in a shutdown process & the unit powers off.


Has anyone been able to bypass this?  I dont want my notebook to shutdown, standy, reboot, etc.  I would like to be able to close the lid though!

---

### Post by freedomfries on 2005-05-23
I have a M5313 and I am having the same problem. I haven't solved it yet but right now I'm looking into disabling ACPI. ACPI is the daemon that handles the suspend/resume power stuff. I've heard that ACPI is very buggy as the specifications for this stuff is kept very secret so there's a lot of reverse engineering/guess work in this stuff. 

I'll let you know how I make out.

---

### Post by freedomfries on 2005-05-23
Okay, I did a few searches and I figured out how to disable acpi. But the down side is that you loose CPU throttling and hence the cpu gets hotter, the fan gets louder, and if you haven't cleaned out your heatsink, your computer will overheat and shotdown. Do a google search for "emachines unoffical forums" to learn about the overheating problems emachines laptops have. 

In any event, here's how to disable acpi in ubuntu:

edit the file /boot/grub/menu.lst 

look for line: 
 
 kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash

add acpi=off to the end after splash.

I'll keep searching for how to disable just the lid power management stuff...

---

### Post by freedomfries on 2005-05-23
Success. I just commented out the scripts called when the lid close button is activated. ie I added a # to the beggining of each line of these files:

/etc/acpi/lid.sh
/usr/share/acpi-support/screenblank

(I think the first one was the one that mattered though).

---

