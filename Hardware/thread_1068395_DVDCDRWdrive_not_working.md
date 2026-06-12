---
title: "DVD\CDRWdrive not working"
date: 2009-02-12
forum: Hardware
---

### Post by sailthesea on 2009-02-12
HI Guys
  I've been having a great night getting to know Ubuntu 8.10 which I installed on a really old Dell C640 I got and am really impressed with the performance I'm seeing, but I've run into my first real problem now. My DVD\CDRW drive isn't working, it won't even open I assume I'll have to find and install a driver for it but I haven't got a clue where to start with that If it helps its got Dell P/N:6P811-A00 on it, I'm used to the giblets in a desktop but laptops are a bit of a mystery to me.

 Cheers

---

### Post by jou770d on 2009-02-13
I'm having similar issues and read almost every thread here about cdrom issues. So I'll try to help.

First of all make sure it's not hardware, if you're dual-booting try it in your other OS. If not dual-booting try booting from some CD like the Ubuntu Live CD.

Then try ```
sudo eject
``` from terminal, see if that works.

If it didn't work:
Try changing your bios settings, look for "SATA operation mode", if it's set to "Enhanced" put it on "Compatible". This is usually found under IDE configuration.
If you're dual-booting with Windows you'll have to change it back before booting windows. This is the only workaround I found for my cdrom but I'm on an Asus.

I hope some of this helps.

---

