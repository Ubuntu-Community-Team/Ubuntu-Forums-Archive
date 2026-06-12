---
title: "IBM 600x, blank brown screen"
date: 2005-11-05
forum: Hardware &amp; Laptops
---

### Post by koppit on 2005-11-05
I decided to post this in the correct forum this time, Instead of 5.04...
Here's a rundown, seems I'm not the only one with the problem.

[QUOTE=crandol]I am running an IBM ThinkPad 600x and when I run the Live CD all seems to progress well. Until . . . I finally get to the GUI.

The Live boot process seems to be teasing me . . . I get a mouse pointer and a blank light-brown screen . . . and nothing else. I have tried to back out of this by pressing Ctrl+Alt+Backspace and this leads me to an apparently functional login screen.

I have tried every option from the login screen (yes, I tried "failsafe" options - no help - same brown screen) and the result is a return to the same "plain brown empty screen" with a mouse pointer in the middle.

-snip-
[/QUOTE]

etc etc. I can switch to bash, but nothing shows up in xwindows. This is the LiveCD, not an install, I want to see if I can get this working before i install. Someone suggested this:

[QUOTE=madcro]I had same problem and this is what I did to fix it :

You need to edit the /boot/grub/menu.lst and add this to the kernel you want to boot.

kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro acpi=off quiet splash pnpbios=off

so add acpi=off and pnpbios=off

reboot and it should work . 
[/QUOTE]

The only problem with this fix .. is it's for the installed version. Any suggestions guys?

BTW, love ubuntu, it's awesome :)

---

### Post by poptones on 2005-11-05
One of the options for booting the live cd is to "pass messages to the kernel." If you choose that and type the above commands at boot it should work.

BTW, you should have zero problems with an actual install. I ran a 600x for months on ubuntu before selling the laptop on ebay (yes, with ubuntu installed).

---

### Post by koppit on 2005-11-06
Good to know, I've run other distros but haven't done anything other than a livecd with ubuntu. Thank you.

edit: works like a charm. instead of hitting enter at boot prompt, type:

*live pnpbios=off acpi=off*

---

