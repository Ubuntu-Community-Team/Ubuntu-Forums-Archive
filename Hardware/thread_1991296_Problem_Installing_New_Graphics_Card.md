---
title: "Problem Installing New Graphics Card"
date: 2012-05-30
forum: Hardware
---

### Post by tiureti on 2012-05-30
Hi,

I have a fairly new system in which I'm trying to install a new NVIDIA GTX 580 graphics card.  Problems occur when Ubuntu (12.04) loads.  If anyone can provide any help, it would be greatly appreciated.

When I put the new card in I notice the following symptoms: 
 - After grub loads, the screen turns dark purple for 30 seconds; it then turns black with some purple and multi-colored horizontal lines.
 - The normal login screen starts to load slowly, with the screen flickering every 5 or 10 seconds.
 - For about a minute the pointer will barely move when the mouse is moved.
 - Eventually the mouse starts moving normally, but there will be no response to mouse clicks or input from the keyboard.

The system was previously working without any obvious problems.  I'm using the following hardware:
 - Motherboard: Supermicro X8SAX, with the latest BIOS firmware
 - CPU: Intel Xeon E5620
 - Memory: 12 GB
 - HD: 1TB, SATA
 - Power supply: 1200W, plugged into the graphics card correctly

I can boot the computer with the new card into rescue mode, and everything seems to work fine booting to Windows.  I tried installing the NVIDIA linux drivers by downloading them from the NVIDIA website and installing them in rescue mode, but it doesn't appear to have made any difference.  The previous graphics card was some AMD card for which I had never installed proprietary drivers.

Thanks,
tiureti

---

### Post by 2F4U on 2012-05-30
Try booting with the nomodeset grub kernel parameter. It may allow you to get to the desktop. Since this is only a temporary solution, either install the proprietary drivers or add nomodeset to your grub configuration.

---

### Post by tiureti on 2012-05-30
This worked perfectly.  Thank you!

---

