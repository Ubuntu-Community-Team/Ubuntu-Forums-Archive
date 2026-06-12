---
title: "[SOLVED] Motherboard + SATA  issues."
date: 2008-05-06
forum: Hardware
---

### Post by joemacnz on 2008-05-06
G'day, I wonder if anyone can help.

I have an ASUS A8V-MX mobo (via chipset) and a SATA hard drive. I have had Ubuntu since Dapper and have had on-again off-again issues with these two not playing nicely. Originally I bought a SATA to IDE adapter and it worked ok, but the adapter is flimsy and not very well made and there have been connection issues.

 Somewhere down the track, I got rid of the adapter and everything worked fine. Until........ the latest upgrade to Hardy!

Now what it does is: When I boot up it does the usual start up thing, shows an ubuntu splash screen for a long time and then goes to what I think is an ASH command line. This is a little unhelpful and most of my commands return something along the lines of can't find hard-drive or can't find etc/.../fstab.

Now one obvious answer is that the HD is corrupted. However, when I bring back the SATA-IDE adapter, it all works fine (if I can position the adapter in just the right spot!) 

Any ideas would be most appreciated.

JM

---

### Post by joemacnz on 2008-05-08
Anyone? Please.

When I boot up now, I get the slash screen and then a busy box 1.something
and now I have a new error message:

(initramfs) [261.236471] /build/buildd/linux/drivers/hid/usbhid/hid-core.c:usb-submit-urb(ctrl) failed

Does that mean anything?

---

### Post by bonestonne on 2008-05-18
gosh i'd love it if i had bookmarked the page, the solution was posted here somewhere else. lucky for you, i have a habit of writing down millions of notecards with the solutions to this. would printing pages help?

here you go:

when you boot up and you're in Grub, highlight the main Hardy install (with a fresh install its the top one (the other two are a recovery and a memtest).

Press "e" when you highlight the entry on the list.

you'll get to another screen which has a list of 4 entries.
one looks sort of like this:
```
Kernel /boot/vmlinuz-2.6.24-16-generic root=BLAHBLAH
```
(BLAHBLAH is a lot of random stuff, don't worry about what it says exactly)

highlight that line (down arrow to highlight it).

Press "e" again.

you'll now get to a point where you're editing it.

you will see:
```
<b-09f2-4836-93ad-e5a70566438d ro quiet splash
```

now you're in a place where you're editing this. these chages are not permanent at this screen.

at the end, change "ro quiet splash" to "all_generic_ide"

exactly like that, underscores included, but not in quotes.

it should say:
```
<b-09f2-4836-93ad-e5a70566438d all_generic_ide
```
when you're done.

now, press "b". if you hit escape, you'll lose the changes.

you wont see the fancy Ubuntu splash screen, just lots of text. soon it'll get you to the login screen.

now, you need to make the change permanent.

open up terminal (Applications>Accessories>Terminal)

type: "gksu gedit /boot/grub/menu.lst"

this is your grub boot list and menu. you don't want to make a point of playing with this unless you're sure you know what you're doing.

In this file, you will find the same line you just edited:
```
<b-09f2-4836-93ad-e5a70566438d ro quiet splash
```

change that exactly as you did to:
```
<b-09f2-4836-93ad-e5a70566438d all_generic_ide
```

click the save button.

you have fixed your install.

this worked for me, and i wish i was able to find the original poster.

i hope you're able to follow easily, that's exactly how the original instructions had said it.

---

### Post by joemacnz on 2008-05-19
Sweet, that worked a charm.Wow, my sata DVD drive is working now too. Thanks!

---

