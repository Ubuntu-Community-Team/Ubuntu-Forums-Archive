---
title: "IBM Think Pad 600X - Live gets me to a blank brown screen. ???"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by crandol on 2005-05-11
I am running an IBM ThinkPad 600x and when I run the Live CD all seems to progress well. Until . . . I finally get to the GUI.

The Live boot process seems to be teasing me . . . I get a mouse pointer and a blank light-brown screen . . . and nothing else. I have tried to back out of this by pressing Ctrl+Alt+Backspace and this leads me to an apparently functional login screen.

I have tried every option from the login screen (yes, I tried "failsafe" options - no help - same brown screen) and the result is a return to the same "plain brown empty screen" with a mouse pointer in the middle.

The system does not appear to be "locked up" since the mouse moves around the screen (clicking does not appear to do anything at all) and  Ctrl+Alt+Backspace does have the effect of returning me to the login screen.

So . . . something IS running, but something IS also wrong - I have no idea what to do from here. Any suggestions?

P.S. the only way to exit the system is to hit the power button which initiates a return to a text mode and tells me "The system is going down for a HALT now!" This seems to suggest that some of the OS is running in a functional manner.

---

### Post by callumd on 2005-05-12
hi crandol,

while not exactly providing a solution, let me add that  I have exactly the same problem.  I've done a default install of Hoary onto a IBM Thinkpad 600x (twice - to make sure it was not user error), and after the first boot, can navigate the GDM logon screen sucsessfully, only to end up in the same brown screen and cursor purgatory as you.

However, I can swap to one of the text consoles, and logon in and work normally, so it looks like the problem lies with Gnome and / or X.Org as Warty worked just fine on the 600x.

Basically I'm in the same boat as you, and just thought I'd add my 2c and ask, has anyone else experienced this problem and found a fix / workaround?   I'd be happy to post logs if anyone's prepared to lend a hand, and can let me know which ones are needed.

many thanks,
Callum

---

### Post by acrisios on 2005-05-16
[QUOTE=callumd]hi crandol,

while not exactly providing a solution, let me add that  I have exactly the same problem.  I've done a default install of Hoary onto a IBM Thinkpad 600x (twice - to make sure it was not user error), and after the first boot, can navigate the GDM logon screen sucsessfully, only to end up in the same brown screen and cursor purgatory as you.

However, I can swap to one of the text consoles, and logon in and work normally, so it looks like the problem lies with Gnome and / or X.Org as Warty worked just fine on the 600x.

Basically I'm in the same boat as you, and just thought I'd add my 2c and ask, has anyone else experienced this problem and found a fix / workaround?   I'd be happy to post logs if anyone's prepared to lend a hand, and can let me know which ones are needed.

many thanks,
Callum[/QUOTE]


Hi, I've exactly the same problem, my thinkpad 600x is 384 MB Ram. Strange that Kubuntu live cd starts fine.

Hope someone can help

---

### Post by madcro on 2005-05-16
I had same problem and this is what I did to fix it :

 You need to edit the /boot/grub/menu.lst and add this to the kernel you want to boot. 

kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro **acpi=off** quiet splash **pnpbios=off**


 so add acpi=off and pnpbios=off

reboot and it should work .  :smile:

---

### Post by callumd on 2005-05-17
hi madcro,

thanks for the help.  I added the two settings, and X works beautifully now.

Many thanks yet again
Callum

---

### Post by acrisios on 2005-05-21
[QUOTE=madcro]I had same problem and this is what I did to fix it :

 You need to edit the /boot/grub/menu.lst and add this to the kernel you want to boot. 

kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro **acpi=off** quiet splash **pnpbios=off**


 so add acpi=off and pnpbios=off

reboot and it should work .  :smile:[/QUOTE]


Great!!! It works fine now  Many thanks!!

---

### Post by koppit on 2005-11-05
Sorry to resurrect this topic, but it seems to be happening in breezy as well. I'm also using a 600x. This is booting with the LiveCd, not the install version. Any suggestions?

edit: see post in 5.10 forum. when booting, instead of just hitting enter, type

*live pnpbios=off acpi=off*

---

