---
title: "USB Keyboard in Grub"
date: 2006-02-01
forum: Hardware &amp; Laptops
---

### Post by Fergal1982 on 2006-02-01
I have a USB wireless optical desktop (mouse and keyboard connected through a single USB connector). This is also run through a KVM (but i dont think this is an issue).

With the KVM set to the PC, the keyboard is recognised fine in BIOS, and once ubuntu loads to the login screen and beyond.

It isnt however, recognised by GRUB. meaning i cant select a different option. Can anyone suggest how this can be resolved?

(My laptop - the other unit on the KVM - seems to pick it up fine, although its using LILO to boot.)

---

### Post by nemesa on 2006-02-20
Hi!

I have exactly the same problem. 

Please help! Is there any solution?:confused:

---

### Post by mjwood0 on 2006-02-21
Try finding a setting in your BIOS that says something like "Enable Legacy USB Support".  I believe this should be turned on for it to work.  (I could be wrong, but you can always toggle it and see).

---

### Post by nemesa on 2006-02-22
Finally I've found it...
Thank you!

---

### Post by mjwood0 on 2006-02-22
Glad I could help!

---

### Post by pinballkid on 2006-02-26
I've got the same problem, but I'm afraid that enabling legacy usb support doesnt seem to help. Has anyone else experienced this?

---

### Post by christhemonkey on 2006-02-26
In my BIOS there was an `enable USB keyboard` option that did the trick on my laptop.

---

### Post by coolguy2k on 2006-03-23
hey hey

i just had to get a new keyboard - picked up an usb flavor, and have run into this problem as well.  keyboard works in bios, works in ubuntu, works in windows, not in grub.  In bios there is an option to enable legacy usb devices, three options: no mice, all, and (of course) disabled.  When i enable no mice or all grub "loads" for... well forever - just freezes saying something along the lines of: GRUB 1.5 (or whatever - then next line as follows): GRUB loading _

ps/2 adapter doesn't work w/ my new keyboard so i've been using my roommate's ps/2 keyboard for GRUB navigating purposes.

thanks for the help

---

### Post by coolguy2k on 2006-03-25
bump

---

### Post by coolguy2k on 2006-03-25
one more bump

---

### Post by coolguy2k on 2006-03-27
last, desperation bump

---

### Post by Jose Catre-Vandis on 2006-08-27
Thank you, enabling Legacy USB Support in my bios helped me to resolve the same problem

---

### Post by rhombicosidodecahedron on 2007-10-11
Hi,

I have the same problem as mentioned above with my Logitech NewTouch 200 usb keyboard ( GRUB won't detect the keyboard on boot) except that in my case, after I edit the BIOS settings and enabled legacy support, GRUB displays a message: 

NTLDR missing
Please try and solve the problem yourself, etc, etc.

Press CTRL-ALT-DEL to reboot.

After I set the BIOS settings back, it goes away, but GRUB still can't detect the keyboard. No one else on the forum seems to have this problem. Please help...

---

