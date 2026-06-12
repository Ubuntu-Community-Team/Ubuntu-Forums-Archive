---
title: "Logitech wireless M510 mouse stuck sending key strokes to ASUS laptop"
date: 2014-01-19
forum: Hardware
---

### Post by azhar.basit on 2014-01-19
Hello All,

I have ASUS x201e DH01 with Ubuntu 12.04.  I tried to use a Logitech wireless mouse M510 which works fine in Windows 7.  

However as soon as I plug in the USB receiver, the terminal (or any other app like browser) repeatedly receives '+' and Return keyboard events. 

The mouse is responsive to motion and clicks but in addition it goes bonkers and sends these keyboard events.   

Anyone had this issue?

thanks!

---

### Post by varunendra on 2014-01-21
Have you checked your laptop's keyboard yet? Considering the problem you mentioned in your [other thread]("http://ubuntuforums.org/showthread.php?t=2200381"), it may be possible that one of your keyboard keys have stuck, causing all the wierdness.

I have personally used a wireless keyboard/mouse (2.4 GHz Wifi link) on my Asus X54C with Ubuntu 12.04 (kernel 3.2.0-36), and it worked flawlessly.

---

### Post by azhar.basit on 2014-01-22
Hi Varun,  My keyboard on laptop is fine.  I tried to use the wireless mouse when my touchpad was going bonkers.  

Apparently after connecting an external monitor after laptop has booted up, making some changes via CompizConfig settings manager and using Synaptiks to configure the synaptics driver settings I am now operational again.  

Even the wireless mouse is now working fine without sending keyevents.  Maybe it was some interplay between the CompizConfig settings? I am not sure. 

thanks

---

