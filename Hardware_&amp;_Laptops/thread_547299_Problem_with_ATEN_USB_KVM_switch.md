---
title: "Problem with ATEN USB KVM switch"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by wcgoh on 2007-09-09
Hi,

I using a ATEN USB kvm switch (CS-62U) to switch between a XP and Ubuntu.
Currently i am facing the problem with Ubuntu not able to detect the mouse and the keyboard typing response is erratic. The keyboard typing is either not responsive or keep churning out the same letters.
I tried not using the kvm and it work perfectly well, is there any other way to solve this problem. I really need the kvm switch.
Thank you.

---

### Post by frith on 2007-09-09
Hmmm... I also use this kvn switch, with my toshiba m200 tablet pc and a windows xp desktop. I don't have any problems at the moment, but there were some issues I had to work through at the beginning:

1. It took me a while to realise the keyboard must be plugged into a specific slot. Obvious I know, but I didn't see the label...

2. The Aten KVM supports various different keyboard layout modes - check the manual or the website for info on how to change them, and make sure you have your keyboard in the right mode (there are only a few to choose from)

3. I had no end of trouble using a wireless keyboard and mouse with it - every time I plugged something into one of the pcs (eg a new usb device/memory stick or even plugging in the laptop power supply) it would cut the power to the wireless set. Then I would have to unplug the switch and plug it back in again. But I got a system eventually.

I also had an experience of the keyboard keys not working or being erratic, but I solved it by moving the keyboard closer to the wireless transmitter. Maybe give that a try...

On a side note, I seem to have fried the video switch by hot-plugging in the video to my laptop, so I might suggest you don't hot-plug the monitor while your lapop is running...

Frith.

---

### Post by wcgoh on 2007-09-10
Thanks for the advice.
I had checked that the keyboard and mouse was plugged to the correct port.
Tried change the keyboard layout to SUN, the keyboard still giving erratic behavior, mouse still not responding.
Changed the mouse (logitech cordless mouseman optical) to a normal wired usb optical mouse, and mouse started to work. It couldn't be the kvm not supplying enough power the controller as it worked well under windows xp.
Still can't figure out why the keyboard still giving erratic response.
Any other suggestions?

---

### Post by frith on 2007-09-10
Nothing else I can think of right now..

I'll outline my power issues in a bit more detail because it was a tricky problem that became rather frustrating..

My keyboard/mouse is a wireless combo, so they both share a transmitter. It has a little light on the front that indicates if its sending/receiving. What would happen is that everything would work fine, then all of a sudden it would stop working. Very annoying. It turned out that when I made some kind of change to the configuration of either system, it was switching off the transmitter (the light would go out) and the keyboard no longer worked. When I say change, I mean stuff like plugging a usb stick into either computer (not the KVM, just the PC) or plugging in the power supply for the laptop (I suspect - and this is pure speculation - that there is some kind of ground reference thing happening, so when something was plugged in it would change the ground potential and the device would switch off). My final solution was to plug everything in before starting the computers, and if I noticed the light going off (eg when plugging in a usb stick) I would just unplug the usb connectors of the switch - by unplugging them both it would switch off and I could just plug it straight back in and it would work.

I also had issues with my keyboard not working properly - sometimes some keys would work and not others, and it would type the same key dozens of times. As far as I can recall, the solution in my case was to move the transmitter closer to the keyboard, when they were right next to each other it seemed to work okay. Once the problem went away, it never came back, so I can't really say what caused it. Oh, and at that time I was using XP on both machines, then after I installed Ubuntu it continued to work fine.

Sorry I can't be more help,

Frith.

---

