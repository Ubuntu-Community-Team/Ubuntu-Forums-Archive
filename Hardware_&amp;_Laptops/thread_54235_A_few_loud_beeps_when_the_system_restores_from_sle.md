---
title: "A few loud beeps when the system restores from sleep"
date: 2005-08-03
forum: Hardware &amp; Laptops
---

### Post by Asher on 2005-08-03
I've got 5.04 installed on my ThinkPad T40...I can use FN-F4 to make it suspend to RAM/sleep, and it works fine for the most part.

When it restores from RAM, the screen has some weird lines for a second and makes a few loud beeps with the system bell (from the motherboard), even though I have the system bell turned off in the Sound preferences.  This is quite annoying if I'm opening up my laptop to use in the middle of a lecture at school, as it distracts people.

Is there any way to get rid of that?  I don't mind the screen corruption, because it goes away very quickly to be replaced with the unlock-screen.

As a sidenote, does anyone know how to make the ThinkPad suspend to RAM/sleep automatically when I close the laptop?

Thanks in advance! :)

---

### Post by Rinnan on 2005-08-03
[QUOTE=Asher]I've got 5.04 installed on my ThinkPad T40...I can use FN-F4 to make it suspend to RAM/sleep, and it works fine for the most part.

When it restores from RAM, the screen has some weird lines for a second and makes a few loud beeps with the system bell (from the motherboard), even though I have the system bell turned off in the Sound preferences.  This is quite annoying if I'm opening up my laptop to use in the middle of a lecture at school, as it distracts people.

Is there any way to get rid of that?  I don't mind the screen corruption, because it goes away very quickly to be replaced with the unlock-screen.

As a sidenote, does anyone know how to make the ThinkPad suspend to RAM/sleep automatically when I close the laptop?

Thanks in advance! :)[/QUOTE]
 Are those beeps coming from cardservices (the part of the OS that handles PCMCIA cards?  Try changing the number of PCMCIA cards in your laptop (if it has them) and see if that changes the number of beeps.

---

### Post by Asher on 2005-08-04
[QUOTE=Rinnan]Are those beeps coming from cardservices (the part of the OS that handles PCMCIA cards?  Try changing the number of PCMCIA cards in your laptop (if it has them) and see if that changes the number of beeps.[/QUOTE]
I have 2 PCMCIA slots, but I don't have any PCMCIA cards in them (and never have).  I'm not sure if that's where the beep is originating from, I just know it's definitely not coming from the speaker.

The beeps exist while resuming from a suspend-to-disk/hibernate state as well.

---

### Post by Kitty on 2005-08-04
I have the same problem with a Toshiba M30 laptop.

---

### Post by Jingo on 2005-08-04
Also here on T42!

---

### Post by Lambert on 2005-08-04
I don't have a direct answer for your questions but hopefully this helps.

[I]Experimental: ACPI sounds - /proc/acpi/ibm/beep
-----------------------------------------------

The BEEP method is used internally by the ACPI firmware to provide
audible alerts in various situtation. This feature allows the same
sounds to be triggered manually.[/I]


I'm not sure how to turn this off or identify what the beep indicates. I don't even know if it can be turned off but you might want to google some of these along with ibm-acpi and do some reading.

As for the lid closing and going to suspend there is a way to do this but I can't remember where I found it. There is an acpi/events folder somewhere I believe. Search for it maybe in /etc or under /usr. In that file you have to enter something like

event=button/lid
action=/etc/proc/sleep.sh %e

these are not accurate commands as I'm going off memory. I couldn't get them to work on my tp a31 but I found the a31 and ibm-acpi driver doesn't work that well. T40 showed better compatability. I can't get fn-f4 to suspend to ram for me. Just fn-f12 to hibernate and that's buggy. try to google 'acpi events'

Couple links for you.

[www.thinkwiki.org](www.thinkwiki.org) site dedicated to thinkpad users and linux
[http://ibm-acpi.sourceforge.net/](http://ibm-acpi.sourceforge.net/)

---

