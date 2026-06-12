---
title: "Ubuntu 5.04 won't start"
date: 2005-04-30
forum: Hardware &amp; Laptops
---

### Post by themelvin on 2005-04-30
Hello, I have Kubuntu 5.04 on my other computer and now i wanted to install Ubuntu on my old Celeron 400, 196MB ram,  ATi Rage Pro, 5Gb disk,...  I also have a network adapter from Canyon it has a Realtek chip on it. The installation says that there is not ethernet card present... Ok, i installed it anyway, but have problems:

When it should boot into Linux it only changes these two lines:

HUB 1-0:1.0: Over-current change on port 1
HUB 1-0:1.0: Over-current change on port 2

And it goes to infinity, like this:
HUB 1-0:1.0: Over-current change on port 1
HUB 1-0:1.0: Over-current change on port 2
HUB 1-0:1.0: Over-current change on port 1
HUB 1-0:1.0: Over-current change on port 2
HUB 1-0:1.0: Over-current change on port 1
HUB 1-0:1.0: Over-current change on port 2
HUB 1-0:1.0: Over-current change on port 1
HUB 1-0:1.0: Over-current change on port 2
HUB 1-0:1.0: Over-current change on port 1
HUB 1-0:1.0: Over-current change on port 2
HUB 1-0:1.0: Over-current change on port 1
HUB 1-0:1.0: Over-current change on port 2
HUB 1-0:1.0: Over-current change on port 1
HUB 1-0:1.0: Over-current change on port 2
HUB 1-0:1.0: Over-current change on port 1


Does anybody know what' s wrong?

---

### Post by nad on 2005-04-30
Looks to possibly be a usb hardware issue. Unplug everything from the computer except your keyboard, monitor and mouse, disable usb in your bios and try again.

---

### Post by themelvin on 2005-04-30
Will try this, but my mouse is on USB and don't have the PS2 adapter. Tomorrow will try the friend's mouse on PS2 and post.

Thanks

---

### Post by themelvin on 2005-05-01
It was an IRQ problem. In BIOS i changed to Auto and now it works, but have one problem. I accidently disabled USB and have a USB mouse, now the mouse doesn't work. What shoul I do?
I am stuck, now i don't know how to turn my PC down to enable the USB in BIOS. And then, how could I cahnge the settings to enable the USB and the mouse?

Thanks

---

### Post by nad on 2005-05-01
Sorry about that. I think that there is a tab sequence to to tab through the login window options. Alt tab, shift tab, ctrl tab. I don't remember.

The power button always works also. Just reset. Your file system should recover without errors as there is nothing to synchronize after 5 (3?) seconds.

---

### Post by themelvin on 2005-05-01
will try or ctrl alt backspace and command shutdown -r

---

### Post by themelvin on 2005-05-01
OK, I restarted but there is a problem. When I log in it sayssomething about gnome not loading correctly and it just stays ther, when i hit ctrl+alt+backspace it writes these two lines:
HUB 1-0:1.0: Over-current change on port 1
HUB 1-0:1.0: Over-current change on port 2

And it repeats them... so maybe afterall it is a USB problem...

---

### Post by nad on 2005-05-01
Some older bios' can be a pain to configure. Try setting no irq for usb and yes for a pnp operating system. If that doesn't work, keep trying different settings.

---

### Post by themelvin on 2005-05-02
OK, I will try when I come home, thanks.

---

