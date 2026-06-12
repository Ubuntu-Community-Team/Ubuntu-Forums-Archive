---
title: "Breezy suspends all by itself"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by anando on 2005-10-14
Twice I had an issue where Breezy decided to suspend itself while I was listening to streaming media on realplayer. In fact I was enjoying myself - but that is quite besides the point. :|

I tried bringing it up by pressing the power button - but nothing happens - some lights flicker on the screen for a while and then everything shuts down.

So ... can someone explain what might be causing this random behavior ? I have  unhashed acpi_sleep=true in /etc/default/acpi-support. Do I need to do add the suspend=/dev/hda4 to /boot/grub/menu.lst as well ? So far everything works without making the changes to /boot/grub/menu.lst - I am not sure if it is mandatory. :-k

Will be grateful for your suggestions.

Thanks,
Anand.

---

### Post by mariux on 2005-10-14
I have the same problem. My (k)ubuntu suspends during kde-login. Kinda anoying!

(but props for getting suspend and hibernate working out of the box on my laptop!)

---

### Post by netsyd on 2005-10-15
[QUOTE=mariux]I have the same problem. My (k)ubuntu suspends during kde-login. Kinda anoying!

(but props for getting suspend and hibernate working out of the box on my laptop!)[/QUOTE]

Not having the issue on mine... But incase the devs read this - Nice work on getting suspend and hibernate working on my laptop too!

To answer part of the first question... I have touched absolutely nothing in my menu.lst nor have I touched ACPI at all. I don't think the resume= is necessary in all cases.

---

### Post by anando on 2005-10-15
[QUOTE=netsyd]Not having the issue on mine... But incase the devs read this - Nice work on getting suspend and hibernate working on my laptop too!

To answer part of the first question... I have touched absolutely nothing in my menu.lst nor have I touched ACPI at all. I don't think the resume= is necessary in all cases.[/QUOTE]

I don't understand - how can you possibly have suspend without unhashing acpi_sleep=true in /etc/defaults/acpi-support ?

As for me - it worked perfectly until the last update where acpi changed from 0.45 to 0.46 (just before the official release). I believe the kernel was also updated then. 

Understand that it works most of the time - but ever so often - it suspends by itself  and won't come up - or at times won't come up after a deliberate suspend.

Is there a way of going back to acpi 0.45 ? :sad: 

- Anando.

---

### Post by mariux on 2005-10-15
I didnt unhash that file either, but i DID configure it in kcontrol -> power options.

---

### Post by mariux on 2005-10-15
But are anyone else experiensing this? It is really anoying!

Seems klaptop_check is causing the problem. Filed a bug... [http://bugs.kde.org/show_bug.cgi?id=114453](http://bugs.kde.org/show_bug.cgi?id=114453) &#160; &#160; &#160; &#160;

---

### Post by mariux on 2005-10-20
Bump

Its really anoying :)

---

### Post by endura29 on 2005-10-27
Yeah, this definitely is annoying. I'm using Breezy Badger 5.10 on a Dell Inspiron 4000 and have tried all kinds of different ways to get around this. For awhile, I thought that it had to do with opening the lid and then pressing the On button (which would for some reason trigger the auto-shut down.) But, after a bit of testing, I found that wasn't the case.

I resume and have about 10 seconds before I drop out again.

I'll post any progress I make on if I figure out a way around it.

---

### Post by mlord on 2005-10-27
It's closing/opening the lid that does it for many of us -- I normally suspend by keystroke or menu, but if I do that and then close the lid, it will re-suspend in mid-stride when I attempt to resume.

The lid "event" handler doesn't seem to look much at the current lid state when deciding to suspend (again).

??

---

### Post by mariux on 2005-10-28
I deactivated suspend (in kcontrol) and only use hibernate now, so now i dont have the problem (only some flickering at the time when its trying to suspend but isnt allowed to).

Resuming from hibernate isnt as fast as i would wish though. Should i add a resume= to the grub-menu? Seems to complain about that when resuming....

---

