---
title: "Duel boot/ssd Question"
date: 2019-01-12
forum: Hardware
---

### Post by mitchlong on 2019-01-12
I have a CF-31 Panasonic Tough book that I would like to put Ubuntu on. I have experience with Ubuntu and Debian. There is one problem the ***_BIOS_*** is locked. I would like to Duel boot win 10 and Ubuntu/Linux. If I buy an SSD and can use a dock to install windows and linux on it? If so will it give me an option to at start up to boot into one or the other? Thank you I appreciate your time and help. Thank You

---

### Post by mikasu on 2019-01-12
If you cannot change the settings of your BIOS, it might not even work if you install a dual boot on an SSD from another computer to then put it in your laptop. Because you have to set the boot order or at least have a boot menu to load the grub. So if it is completely locked, I wouldn't try. It might just lock your laptop to unusable. Unless you can reinstall an OS on your laptop. But I wouldn't try. Though wait to see if someone knows more about locked BIOS because it's actually the first time I hear about a case like that.

---

### Post by CatKiller on 2019-01-12
There are 2 ways to clear the password for the BIOS if you don't know it:

There will be a Clear CMOS jumper; with the computer turned off you find the jumper and put in in the other position for 30 seconds or so, then put it back and turn the computer on again.

You can unplug it, disconnect the main battery and the small CMOS battery, and then wait 30 seconds or so, then put them back and turn the computer on again.

---

### Post by mitchlong on 2019-01-13
Yes I have tried unplugging the batterie. And I have yet to find a jumper or a location for one. It seems that on the tough books it was stored on flash memory or eprom vs cmos as it was more secure.

---

### Post by CatKiller on 2019-01-13
It wouldn't be just the main battery: there is a watch-style battery inside whose entire purpose is to retain the BIOS settings when there is no main power. That's what you'd need to remove, since that's exactly what you don't want.

If the settings are stored in something that doesn't need to be battery-backed, and they haven't included any other means of clearing it, then there's nothing you can do until you can remember the password.

---

### Post by mitchlong on 2019-01-13
Ok thank you . I have unplugged the motherboard batterie with the 2 little wires.

---

### Post by mikasu on 2019-01-13
Is your BIOS now accessible? If not, we could try the soft-flash with a BIOS update (even if the version is the same as the actual one).

---

### Post by mitchlong on 2019-01-13
No it isn’t. I have tried multiple times and even once for 24 hrs. I found an update on Panasonic’s website for BIOS but it says it’s for win 7 only. So I am looking how to revert my computer to win 7.

---

### Post by mikasu on 2019-01-13
it will not change anything. At the very least if you worry about that, launch the updating software with Windows 7 compatibility. Hopefully, the bios update will flash the password. Otherwise, you might have to extract the files inside the exe and look for a kind of configuration that says what it is going to flash. I had to do that when I sent my own laptop for a repair and upgrade. They did something that made the BIOS know there was a password but it didn't know what it was.

---

