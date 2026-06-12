---
title: "Keyboard stops working duruing loadup"
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by T3h_Dohtem on 2006-11-12
My Logitech G15 Keyboard just suddenly stopped working for me. :confused:  When I turn on my computer it functions just fine, until Ubuntu loads, then it wont do anything. I have tried a PS/2 keyboard and it does fine, but cant get any response from my USB keyboard. I used my computer last night, everything was fine, Ive been running 6.10 since the day it came out with no keyboard problems, and had Dapper before then for a long time with no keyboard issues, I dont know why all of a sudden it would stop working like this. ](*,)  Thanks in advance for any suggestions.

---

### Post by sunshine02 on 2006-11-12
Until I enabled the USB keyboard in the system BIOS, my machine would do the same thing. I can't imagine the BIOS changing on its own so if you haven't made any changes in it, this won't help any. Just the same, you might check to see if it's enabled.

---

### Post by T3h_Dohtem on 2006-11-12
I checked my BIOS out and all is well there, but it seems to get worse...my PS2 mouse is not working for me either. I can only get a non-usb keyboard to work by the time I hit Gnome Display Manager. USB Keyboard and PS2 mouse will not work. However, I can use my keyboard at the boot loader and try to start up in recovery mode, but once I get to the prompt, the keyboard is non-functional again. What is happening here?! Im totally confused, especially at why this would all of a sudden be happening. Im going to try the Live CD and see what happens with my USB Keyboard and mouse and PRAY that it is just a software issue.


UPDATE: From the LiveCD on my problem PC, things are working fine. Was there a USB driver update that went out? It seems like I recently installed some updated packages from synaptic. Im pretty sure that I've booted a couple times since then though, and I cant be the only person having this problem if thats the case.

---

### Post by sunshine02 on 2006-11-12
I couldn't say for certain about an update... I use a wireless MS mouse and keyboard and have not had any recent issues with it. Did your mouse/keyboard driver get corrupted somehow?

---

### Post by atarianer on 2006-11-13
Have the same problem, during bootup keyb and mouse working fine, afterwards both are dead.
But i have both devices on PS2, only the keyboard is connected via an usb/ps2 adapter.
Even if booted in safe mode both devices won't work.

With knoppix no problems so far ...

---

### Post by n0th1n6 on 2006-11-14
Same thing happens here, my keyboard and mouse are still working untill I install ubuntu-desktop package. The motherboard is an ECS 865G-M8. I've tested both Dapper and Edgy on this machine but with no luck. I am going to boot a livecd and see what happens.

If anyone has already figured this problem, please let us know.

Thanks

---

### Post by n0th1n6 on 2006-11-14
Ok Ill reply to my own post. I figured you need to disable USB keyboard and mouse support if you are using ps2 keyboard and mouse. Hope it also work to those experienceing the same problem :).

---

### Post by corefile on 2006-11-30
I have this same problem, disable it where? In the BIOS or in Ubuntu? I have a ps2 keyboard and USB mouse, the keyboard stops working after the last update

---

### Post by wakingrufus on 2006-12-07
this just happened to me. my g15 stopped working after a restart. my mx1000 mouse still works. a ps2 keyboad is still working. any solutions?

---

### Post by Scio on 2006-12-18
I have the same problem. My wireless USB keyboard does work during boot, but stops working when kdm starts. However, sometimes it works when I press several keys when Kubuntu loads. Keyboard's receiver has status led indicating when it receives input, and it stops blinking during Kubuntu splash screen. Any ideas why?

Edit: Ok, I found the lines where it stops working, it goes something like this:

new usb low speed device using ohci_hcd and address 2
configuration #1 selected from 1 choice

So, could somebody point a direction where to go now?

---

### Post by dawlane on 2006-12-29
I know this could be a silly question but could the problem lay with the X server configuration

---

### Post by dawlane on 2006-12-30
Did a bit of digging on the forum this could be related. [http://ubuntuforums.org/showthread.php?t=279626](http://ubuntuforums.org/showthread.php?t=279626)

---

