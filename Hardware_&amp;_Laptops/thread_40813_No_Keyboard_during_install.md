---
title: "No Keyboard during install"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by jca27 on 2005-06-10
I'm trying to install Ubnutu for the first time.   I downloaded version 5.04 and booted to the install program.   At the first prompt I am able to use the keyboard.  However, once the install starts I lose all control of my keyboard.  The LED's freeze.

I'm using a normal PS2 keyboard, that I know is functional.  Plus it works when I originally boot to the CD.  I can't even see error messages since I can't scroll.  Anyone have this problem before?

thanks,
Joe

---

### Post by Thunderguy on 2005-06-24
Yep, I have the exact same problem you have.  I just tried Ubuntu today.
I have the same problem on many other distro's, I just can't figure it out, It is a PS/2 Keyboard, Was Curious what motherboard do you have? Maybe we have the same one.  I tried another PS/2 Keyboard and that didn't help. I believe the PS/2 Could be wired to the USB headers on the motherboard, but I don't know if that would cause a problem. It's got me beat. Could anyone help the both of us?

---

### Post by Thunderguy on 2005-06-25
:???: I figured out what the problem is.  I have good news and bad news, First I'm not sure whether your problem is the same as mine so use your judgement if it doesn't work, sry.  I'm on an Emachines W3050. Now It has a type of Native Support for USB keyboards, It seems to be a little wierd but I have a very good guess.  The keyboard controller is on the PS/2 and the USB port, it also seems to have a lockup feature incase things go wrong.  This means if you have a USB keyboard, it should work in Dos just fine.  What seems to me the problem is, When an OS say, Windows boots up It finds the PS2 keyboard and initializes it just fine, Linux finds both ports, the USB and the PS2, although it goes by too fast to auctually tell, I would not be suprised to hear it loads the keyboard on both ports thinking they are two different keyboards, This would cause the keyboard controller to activate the keyboard lock ( NUMlock is lit ) but nothing works.  I found that by Disabling USB from the Bios, Will cause Ubuntu to work just fine with the keyboard on Install. ( Good News ). But You wont be able to use any USB Devices ( Bad News ). I'm going to disable USB and install Ubuntu, then I shall see if there is a way to configure the keyboard after it is installed. Maybe I could work it out so you only have to worry about it while installing it, then you can configure it, Maybe my plan will fail  :mad: . Well See ya later, Ill reply back if it works or not.  ](*,)

---

### Post by Sendervictorius on 2005-06-27
Maybe the cheapest, easiest thing thing to do is go buy a USB keyboard? :)  What is your own time worth?

---

