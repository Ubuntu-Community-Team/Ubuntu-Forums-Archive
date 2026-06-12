---
title: "keyboard unresponsive until after grub -- usb problem?"
date: 2005-11-27
forum: Hardware &amp; Laptops
---

### Post by reuben on 2005-11-27
Hello,

As I stated in the subject, my keyboard is unresponsive until after grub has loaded the kernel. That is, I cannot get into the bios, and I cannot change anything in the grub menu. After the kernel loads, it complains about a USB device -- usb device 2-1 -- not responding. The keyboard plugs into the PS2 port.

I have usb at the back of the computer, and usb on top. The ones on back do not reliably work, I think...I have a usb mouse, and unless it is plugged in on top, it isn't recognized on bootup. (Although, if it is plugged in to the back, I can unplug it and replug it in once I'm in kde, and it will be recognized).

Also plugged into the top (2nd port) is the cord that connects to my digital camera. Usually my camera is not connected to it, but I leave it plugged in since it is more convenient that way. Is that bad??

I have, naturally, tried booting with one or both of the above unplugged, but it doesn't help.

Here is lsusb:
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 001 Device 001: ID 0000:0000  

Of course all the usb stuff could be a red herring. Anybody have any ideas as to what's going on? 

Thanks

---

### Post by reuben on 2005-11-28
*bump*

This also prevents me from using the livecd, since my keyboard is unresponsive when it first appears. Therefore there could be a number of new users who are put off ubuntu by a "dead" livecd...

Any ideas?

---

### Post by Patsoe on 2005-11-28
If your keyboard doesn't work even before Grub (that is in the BIOS screen), it seems there is a hardware problem. 
Also, all motherboard USB ports should usually be equally 'reliable'. 

I have had such problems on an old pc where the motherboard started to fail.
What type of motherboard is it?

---

### Post by reuben on 2005-11-28
Errr, I think a newish asus. It's running an AMD64 CPU. Is there any way to find out without taking the machine apart?

---

### Post by Patsoe on 2005-11-28
Well, if it is running an AMD64 cpu, at least it can't be an awfully old board. Often, you can tell from the BIOS (but that you can't access).

by 'usb on top' do you mean still on the back, but near the ps2 ports, or really on top of the case?
The fact that your mouse doesn't just work on all usb ports is sort of surprising.

Anyway, I'm quite sure that you're looking at a hardware problem. It could be something silly, like an internal usb connection cable (to the front/top ports) being loose. Or it could be a dieing motherboard or psu.

---

### Post by reuben on 2005-11-28
I've had the usb problems from the start (and yes, I do mean the usb port on top of the case), i.e. approx 1 year, so I don't think the motherboard is dying. I would have returned it for repair, but the vendor was such a bitch to deal with (cyberpower -- avoid!!!) and I was so happy to have my new toy that I kind of punted on the issue. 

Well, I'll open the box up later and double check for loose cables, and to see if I can see anything else obvious.

Thanks

---

### Post by reuben on 2005-12-10
Fixed. I opened up the box and looked for "USB 2" on the motherboard. There was a cable plugged into it, which I traced back to a USB flash card reader which I don't use anyway.

Removed, and everything now works.

---

### Post by Patsoe on 2005-12-12
happy to hear that. Crazy, what really peripheral hardware can do to system stability!

---

