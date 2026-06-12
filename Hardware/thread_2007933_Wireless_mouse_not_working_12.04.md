---
title: "Wireless mouse not working 12.04"
date: 2012-06-21
forum: Hardware
---

### Post by Zeus1987 on 2012-06-21
Hello,

I have issues with my newly bought Canyon Stealth wireless mouse (CNL-MBMSOW02). The pointer doesn't move, the clicks don't work, nothing. The receiver is getting picked up, though, I think (see below)

I have searched through a lot of threads on this forum and other forums, but no solution as of yet.

Some basic info:
Motherboard AsRock 939N68PV-GLAN
AMD Athlon 64 3500+
1 GB RAM

Things I have tried:
- The mouse of course has good batteries, it's new
- I tried plugging the dongle into every USB port
- I ran lsusb, got this:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c317 Logitech, Inc. Wave Corded Keyboard
Bus 004 Device 002: ID 1d57:0001 
```
The "1d57:0001" is obviously the receiver, as it disappears if I remove it and run lsusb again

- I ran xinput --list, got this:
```
jernej@trtnik-ubuntu:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Logitech USB Multimedia Keyboard        	id=8	[slave  keyboard (3)]
    &#8627; Logitech USB Multimedia Keyboard        	id=9	[slave  keyboard (3)]
    &#8627; 2.4G KB 2.4G Mouse                      	id=10	[slave  keyboard (3)]

```

I also tried re-enabling it via xinput set-int-prop 10 "Device Enabled" 8 0, as suggested by one of the threads in this forum.


- It works just fine in Windows 7
- Oddly enough, it also worked fine during a live ubuntu session and also during the reinstallation of the ubuntu OS

Please understand that I am a complete newbie and this is my first linux-operated pc.


Any help will be much appreciated.



Thank you

---

### Post by Zeus1987 on 2012-06-25
Bump.

---

### Post by cecilx22 on 2012-08-20
I'm having a very similar problem. Sometimes I an get the mouse to work by unplugging/replugging the USB dongle a few times.

Have you found a resolution?

---

### Post by Tach on 2012-08-20
> **Zeus1987 said:**
> 
- It works just fine in Windows 7
- Oddly enough, it also worked fine during a live ubuntu session and also during the reinstallation of the ubuntu OS


I was considering making a thread about this, but I have the same exact problem. The mouse was working during installation and then a reboot and now it won't move, but it is detected with lusb. hmm. A bug?

Edit: My laptop is a Y570 with a Logitech M705 mouse, by the way, for anyone that may find that useful.

---

### Post by Zeus1987 on 2012-08-21
I haven't found a solution yet. I'm still waiting for any helpful information from my friends or this forum. For now i use the old PS/2 mouse, which, of course, works flawlessly. The wireless mouse is only being used in Windows for now. 

I'm being optimistic and hoping that canyon will come up with linux drivers for it...

---

### Post by cboschmans on 2012-09-24
Having the same problem with a generic it.works wireless mouse.
Worked like a charm in 11.10 till upgrade to 12.04. lsusb shows vendor and produkt id

---

