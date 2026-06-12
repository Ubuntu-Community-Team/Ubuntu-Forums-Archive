---
title: "GRUB and MX5000"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by strikeback03 on 2007-03-10
I'm posting this over here, since I originally posted in Absolute Beginner and it was not getting any answers.  More Googling shows the problem might not be a beginner problem.

The main problem right now is that I cannot use the keyboard in GRUB.  With "USB Keyboard" disabled in BIOS the keyboard does not work in GRUB but Ubuntu boots. If I enable "USB Keyboard" in the BIOS, I can use the BT keyboard in GRUB, but then Ubuntu won't boot, it goes to "Starting up" with the blinking cursor and stays there. How do I get USB keyboard support in GRUB and still allow the system to boot?

Second problem is that I can't use the BT dongle in the USB hub in my monitor.  If I boot with the BT dongle in a USB port on the back of the computer, the BT receiver shows up in Device manager under USB UHCI controller and the keyboard works, along with hcitool finding devices, etc. If I boot with the dongle plugged into the monitor hub, the BT receiver shows up in Device Manager under a USB EHCI controller, and the keyboard will not work unless I remove and reinsert the dongle. This causes the keyboard to work, but hcitool does not find anything.

---

### Post by slambrick on 2007-03-10
I,m sorry to say I can't help but when you figure it out let me know. I have a mx 5000 as well and can't make it go at all. I got it to work for a little while but when I wanted to use it back in windows it was completely screwed and it took me another day to get it to repair. It's made me a bit cautious.

---

### Post by strikeback03 on 2007-03-10
do you have the Logitech software installed in Windows?  We found with our MX5000 set at work that Windows complains if you use the MX5000 in Ubuntu then reboot back to XP.  I just have not installed Setpoint in Windows on my computer.

The one at work does work in GRUB though, so it is possible...

---

### Post by strikeback03 on 2007-03-10
Bump.  Somebody must have an idea how to get a USB keyboard to work in GRUB.

---

### Post by strikeback03 on 2007-03-13
:bump:

---

### Post by Timtro on 2007-03-14
This is probably stupid, but since nobody else is saying anything, have you considered reinstalling ubuntu using the keyboard?

I say I think this is stupid, because there is probably some simple thing to change and make everything alright, but since I don't know what it is, it seems that having the ubuntu install do it for you may work.

I still think its a dumb Idea, but if you're hard up for options...


Good luck,


Tim.

---

### Post by strikeback03 on 2007-03-24
the first time I tried installing Ubuntu and it made it into the actual installation, it quit at 90% when doing something with USB.  I realized I had not unplugged my keyboard and mouse, so I did so and tried installing again, and that time it finished the installation.

---

