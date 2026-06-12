---
title: "Bluetooth-Keyboard working on console, not working in Xorg"
date: 2013-01-14
forum: Hardware
---

### Post by Pixman on 2013-01-14
Hi folks,

I have this peculiar problem, that my bluetooth-keyboard won't work in Xorg.
I can pair it perfectly with the GUI-tools in Cinnamon, but it won't work in Xorg.

I didn't find help on this regarding the Xorg.conf file in the search and I think a lot of people have the same problem. Solutions I found didn't work for me and were all kind of ugly anyway.

On the console, however, it just works perfectly fine.

With cat /dev/hidraw3 I can capture the input from the device.

How can I configure this in Xorg.conf?
Nothing I tried so far worked.
Is the configuration also possible graphically?

Thanks for your help.

---

### Post by matrix321 on 2013-01-16
.

---

### Post by Pixman on 2013-01-17
I think it's a keyboard-layout problem in Xorg.conf

In xterm the keyboard works but in a totally confusing way. For example, y gives me 4 and so on.

As said, on the console, everything works perfectly fine.

---

### Post by grahammechanical on 2013-01-17
This is just a wild guess but is the BIOS set to detect plug and play devices? Or is it set to allow the OS to detect plug and play devices?

On my motherboard BIOS the Plug and Play is set to NO. This means that the USB devices are detected by the BIOS and I guess that means that I can use the USB keyboard to make a selection on the Grub menu.

I am thinking that the same thing might apply to Bluetooth. The keyboard is not being detected by the BIOS but it is being detected by the OS. Just a guess.

Regards.

---

