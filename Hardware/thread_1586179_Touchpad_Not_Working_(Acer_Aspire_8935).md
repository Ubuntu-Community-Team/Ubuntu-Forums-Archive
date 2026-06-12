---
title: "Touchpad Not Working (Acer Aspire 8935)"
date: 2010-10-01
forum: Hardware
---

### Post by SavageWolf on 2010-10-01
I have tried the steps here: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

The buttons work, and the "Pointing Devices" thing recognises it. Sometimes the scrolling works (and rarely the pointer), but only if I press really hard. I have tried cat-ing /dev/input/event*, but only my (USB wireless) mouse and keyboard work, as I can tell.

---

### Post by SavageWolf on 2010-10-02
Anyone? Help?

---

### Post by Sda1986 on 2010-10-02
maybe can be this

gconftool --type bool --set /desktop/gnome/peripherals/touchpad/touchpad_enabled true

Today it was for one of my friends.

---

### Post by SavageWolf on 2010-10-02
No, that didn't work, I think it is a problem with it not being sensitive enough... (It'll probably turn out to be a thin layer of wrapping over the pad or something, knowing me...)

---

### Post by SavageWolf on 2010-10-11
Still need help...

---

### Post by SavageWolf on 2010-10-20
STILL not working... Hmm...

---

### Post by tophousetim on 2011-10-30
> **Sda1986 said:**
> maybe can be this

gconftool --type bool --set /desktop/gnome/peripherals/touchpad/touchpad_enabled true

Today it was for one of my friends.
Worked for me Sda1986.......well done and thanks

---

