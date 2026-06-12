---
title: "Intel Board Problems"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by gwoodard on 2007-11-18
Okay I just got a USB Keyboard and tested it on my computer, it didn't work in any of the USB Slots, But I tested it on another computer and it works fine... do I need to go into BIOS and set defaults or did I do something stupid?

BTW the mouse I use works and it's a USB but only in one slot

---

### Post by gwoodard on 2007-11-20
Update...the keyboard only works if a PS/2 Keyboard is plugged and if XP or Ubuntu are running...the keyboard will work buy itself after a OS has been started (since I dual boot it won't go to the OS of my choosing...)

---

### Post by dabl on 2007-11-20
Plug in your USB keyboard, boot your computer, and when logged in, open a console window and run ```
lsusb
```

Does your system see the keyboard?

---

### Post by bingoUV on 2007-11-20
> **gwoodard said:**
> Update...the keyboard only works if a PS/2 Keyboard is plugged and if XP or Ubuntu are running...the keyboard will work buy itself after a OS has been started (since I dual boot it won't go to the OS of my choosing...)

I do not quite understand.
1. You are booting the system, and you are at grub prompt. Here if you only have USB keyboard it does not work? But if you have a PS/2 keyboard too, then the USB keyboard works? Or the PS/2 keyboard works, using which you choose which OS to boot into?

2. Once you have booted into ubuntu, do you still need the PS/2 keyboard to be plugged in for USB keyboard to work?

---

### Post by gwoodard on 2007-11-20
Never mind...all I had to do I plug in the USB keyboard before plugging in the power so it works

I'm using it right now to type... :)

---

