---
title: "Shutting laptop lid only turns off backlight"
date: 2008-08-19
forum: Hardware
---

### Post by icksa on 2008-08-19
Hi:
I have a weird problem that I can't find any information on. When I close my laptop lid, the backlight turns off, but the screen does not go black. So basically, the screen is not completely off, it is just really dark. 

To test whether ubuntu can completely turn off the screen I tried typing xset dpms force off

which seems to work, although the screen spontaneously turns back on after a short time...

Does anyone have any suggestions? Or can you suggest where I can go to get help?

I have an nc6220 laptop with intel 915 graphics with Hardy.

Thanks

---

### Post by lackoblacko on 2008-08-20
check your power options to see if they are correct.

---

### Post by kspncr on 2008-08-20
computer->preferences->power options

---

### Post by icksa on 2008-08-22
Hi:
I've gone to the gnome settings and made sure that the screen is set to blank when the button is pressed. 

I don't think that is the issue, however, because the screen does blank in the sense that the backlight does turn off and turns almost black, but the screen is still on. So, for example, if you move the mouse around and strain your eyes you can see it moving around the screen even though the backlight is off. 

What would be really nice, is if there were some way to just completely cut the power to the laptop display so it never turned on. I am going to start using my laptop at work with an external monitor and I would like to be sure the screen is completely off when I close it...

I did find a script that worked using the vbetool program, but that turns off all of the screens connected to the laptop, and I would like to still be able to use an external display...

Thanks

---

### Post by solitaire on 2008-08-22
Check the BIOS, sometimes there is a setting in there under "Power management", or something like that, concerning laptop lids and what to do when they close. 

It may be overriding Ubuntu's settings.

---

### Post by icksa on 2008-08-22
Hi:
I checked the BIOS but didn't find anything related to power settings. I went and updated the BIOS but still no success. Just to make sure there isn't some hardware problem, I booted into windows and things worked perfectly (screen completely turned off)...

Is there possibly somewhere in /proc I can go and muck around to turn off the screen?

I should mention that I just formatted my computer and reinstalled ubuntu. So I didn't mess with any of the default options...

Thanks

---

### Post by liquider on 2011-08-20
I have the same issue on Xubuntu.

Been playing around with /etc/acpi/lid.sh, but can't figure it all out.
However, if I run /usr/share/acpi-support/screenblank, it goes as blank as I want it.

edit: [s]I figured it out...[/s] disregard that, it doesn't do ****.

---

