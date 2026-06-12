---
title: "Logitech DiNovo Laser"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by LadFromWales85 on 2006-12-03
Just a few days ago installed Ubuntu on my main machine, after using Windows due to hardware incompatibilities, which have been sorted for the most part.

Now comes my Logitech DiNovo laser, which is working fine as a basic keyboard and mouse.  I have configured X to load the 'mouse' driver for the so called MX1000, and set my buttons to all work (except the little button between the back and forward keys, which xev registers as button 1 for some reason).

All attempts at using evdev instead of mouse have failed, resulting in X dying.  I have tried referring to the mouse by its name and event ID, failing with both.

```

I: Bus=0003 Vendor=046d Product=c70b Version=4003
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:02.0-5.2/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c70c Version=4003
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:02.0-5.3/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd mouse0 event3 ts0
B: EV=f
B: KEY=c0002 400 0 0 fff0001 f80 78000 6639fa d841d7ad 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0

```

The mouse device appears have handles for both a keyboard and a mouse, which probably contributes to the problem.

Once this is out of the way, I'd like to get the dongle working as a bluetooth device, so I can use it with my phone and PDA etc.  I've read at [http://linux.yes.nu/diNovo/](http://linux.yes.nu/diNovo/) that the dongle doesn't act like most, and requires bluez being patched to make it all work.

Anyone here have the same set and have got everything working under Linux.  I don't have any hope about the LCD, I only ever use it for the calculator anyway, heh.

Any ideas would be appreciated :)

---

### Post by dnns on 2007-01-30
I too have been searching for months for a viable solution (to no avail). 

(I've read [http://linux.yes.nu/diNovo](http://linux.yes.nu/diNovo) but it is absolutely no guide for beginners, wouldn't know where to start)

Keyboard works fine in Edgy in non-bluetooth mode but I miss being able to connect to other bluetooth devices. 
Recently there's been some excitement pertaining to the new Dinovo Edge k/b, and bluez being patched to support it. Will it also help the Laser model? Is there a solution coming up in Feisty?

---

### Post by alex_mayorga on 2007-02-03
I'd also like to know if anyone succeds on this endeavor. I'm also missing the bluetooth capabilities that my set has, at lest on XP.

Please keep us posted.

---

### Post by LadFromWales85 on 2007-02-23
Anyone got the DiNovo Laser working yet?  Since upgrading to feisty, I've not been able to use my keyboard or mouse unless I disable Bluetooth from starting, as when I pressed a key or moved the mouse, the bluetooth icon would pop up in the system tray and then disappear, but no input would be acknowledged.

Might go steal a standard keyboard from another PC so I can have a play with getting Bluetooth working finally!

Has anyone else managed already though?

---

### Post by LadFromWales85 on 2007-02-24
Bluetooth is working with my diNovo Desktop Laser on Feisty :D
There appears to be a bug with pairing though, I've so far been unsucessful getting a phone to pair with the pc, or the pc to pair with a phone (Sony Ericsson K800i)

The keyboard, mouse, and mediapad are paired fine though, I followed the guide at [http://www.ubuntuforums.org/showthread.php?t=227057](http://www.ubuntuforums.org/showthread.php?t=227057) so I'm happy with that...would be nice if I could use it with my phone, pda etc though.

---

