---
title: "scorpius - p20 wireless keyboard"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by Animvz on 2006-10-26
I recently got a scorpius - p20 wireless keyboard. I can not get it to work at all, though I think I have found a solution through googling [here]("http://lists-archives.org/linux-usb-users/02633-problem-with-scorpius-p20-keyboard-mouse-wireless-combo.html"). That post mentions a kernel patch that can be applied, though I have no idea how to do this.

---

### Post by tzompa on 2006-11-06
The scorpius worked for me when I booted the ubuntu 6.10 install cd but when I booted the installed system from the hardrive the keyboard refused to work. My guess is that the kernel is configured  in different ways in the two cases but in what way they differ is hard to tell.

---

### Post by tzompa on 2006-11-06
Found a temporary workaround that might work.

If I
1. Disable legacy usb support in the bios
2. Do not touch the kbd or stick wile in bios or grub.
3. When the kernel starts loading gently wiggles the stick. (I know what it sounds like but its no joke ;-)

Then in perhaps one out of five the kernel detects the keyboard.

Quite logical right. ;-)

When the Scorpius is correctly detected I get two "new low speed USB device using ohci_hcd and address" one for address 2 and one for 3 but when it is incorrectly detected I get only one for address 2.

---

### Post by tzompa on 2006-11-19
It seems that if I use usbkbd and usbmouse modules instead of the usbhid module the keyboard is detected.

---

