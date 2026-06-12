---
title: "Keyboard not working while Grub boot choice"
date: 2008-08-06
forum: Hardware
---

### Post by 1002285 on 2008-08-06
I've installed a Windows and a Linux Mint and my keyboard - Logitech wireless (in a set with a mouse) - works well in both of them, but not at the time when I have to choose between Mint and Windows. Which means I cannot run Windows unless I first change Grub settings from Mint.
I have had a wireless keyboard before, and it worked, so it cannot be just that.
Where can the problem be - in BIOS? But where, then?

---

### Post by matt.taylor on 2008-08-06
Yes, if it has worked befor there shouldnt be a problem with the BIOS but its always worth a check.:)

Does the Num Lock etc appear to flash test during boot up?

---

### Post by hermes0710 on 2008-08-06
The receiver is usb or ps/2?

---

### Post by 1002285 on 2008-08-06
The same keyboard has worked at some points, for example I can enter the BIOS setup with it, and I was able to see System Rescue CD's settings before the booting of its LiveCD - though this did not work with some other Linux LiveCDs.

The receiver is linked via USB, but it has a PS2 cable, too.

Where in the BIOS would the problem be?

---

### Post by matt.taylor on 2008-08-07
Most BIOS's will vary but there should be an option in there somewhere to enable USB during boot up.

---

### Post by markoloka on 2008-08-14
I have same problem. It started yesterday after i had restarted my pc. Before that it worked well.
Ps2 logitech keyboard. After grub keyboard starts to work and numlock light goes on. Can't go to bios either.

---

### Post by 1002285 on 2008-08-14
> **markoloka said:**
> I have same problem. It started yesterday after i had restarted my pc. Before that it worked well.
Ps2 logitech keyboard. After grub keyboard starts to work and numlock light goes on. Can't go to bios either.
In my case, it *was* in BIOS. I think it was in the USB settings, and, in this BIOS, the setting to be activated was sth called Legacy USB. I'' check that later and if I remembered wrongly, I'll come back and tell. But anyway, BIOSes are different.
Why can't you get to BIOS? Does pushing F2 during startup not work at all?

---

### Post by markoloka on 2008-08-14
Keyboard starts to work AFTER grub starts to load kubuntu 8.04.
Before that it's dead. No numlock, nothing. Not even ctrl+alt+del.

Note... my keyboard is not USB connected.

---

### Post by ajarmoniuk on 2010-03-27
workaround: turn on LEGACY USB SUPPORT in your BIOS

---

### Post by Ubuk2008 on 2010-10-13
> **ajarmoniuk said:**
> workaround: turn on LEGACY USB SUPPORT in your BIOS

Thanks a lot! Also, sometimes you won't exactly see the words 'LEGACY USB SUPPORT'. Rather, you might see something similar such as, 'USB SUPPORT'. You do need to go into the bios, which can be done by pressing DEL, F8, or another key as soon as you restart your computer and you see the first symbols appearing on your screen.

Hope this helps!

---

