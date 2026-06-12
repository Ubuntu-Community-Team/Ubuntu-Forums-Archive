---
title: "Can't Use Logitech Wireless Keyboard"
date: 2011-06-05
forum: Hardware
---

### Post by brantpadams on 2011-06-05
I'm not sure if this is a Linux problem or a Logitech problem, but basically I can no longer use my wireless keyboard on my laptop. I believe the model is the MK530 Logitech wireless mouse and keyboard. I've been using it for several months now with absolutely no problems. The keyboard simply stopped responding right while I was in mid-type, but the mouse continues to work fine. The batteries are charged and I tried using different USB ports, but I still can't use the keyboard. 

Most of the fixes I've found online are only for windows computers, so I was hoping I could find some help on this problem around here.

---

### Post by Mark_in_Hollywood on 2011-06-05
Open a terminal. Stretch it a little wider (for easier reading). type:


lsusb

Do you see your Logitech device listed? Here is my lsusb in relevant part:


mark@Lexington-19:~$ sudo lsusb

Bus 001 Device 027: ID 046d:c52e Logitech, Inc. 
Bus 001 Device 002: ID 046d:0807 Logitech, Inc. Webcam B500

My Logitech MK320 is working. May I suggest what will seem like a dumb idea? Uncork (remove) the Logitech USB dongle. Reboot, by which I mean power down and reboot. Power down again, re-insert the USB dongle and power back up. Let me know, please, how it goes.

---

### Post by walt.smith1960 on 2011-06-05
If your batteries are good, you might try re-pairing them.  Push the 'connect' button on the receiver then then push the 'connect' button on the keyboard.(I'm pretty sure that's the sequence)  SWMBO has a wireless keyboard and it has "lost lock" with its receiver before.

---

### Post by brantpadams on 2011-06-06
This is what I get after entering lsusb:

Bus 006 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser

Again, the mouse is working fine but the keyboard is still non-responsive. I've tried powering down and re-pairing several times now to no avail. I've also used each available USB port available on my laptop, being 4. 

My computer is a Dell Inspiron 1525 if that helps at all, and I'm also still running 10.10. 

Thanks for all of your help thus far.

---

### Post by Mark_in_Hollywood on 2011-06-06
This is from 2 years ago. Please be careful with this info:


[http://ubuntuforums.org/showthread.php?t=1190925](http://ubuntuforums.org/showthread.php?t=1190925)

---

### Post by walt.smith1960 on 2011-06-06
Any chance of plugging your receiver into another computer? If you have the same problem on another machine, I'd suspect a premature demise.   I had a wireless Logitech trackball that worked great-most comfortable pointing device I've used. It didn't live all that long though.

---

### Post by M1ttenz11 on 2011-07-23
> **Mark_in_Hollywood said:**
> Open a terminal. Stretch it a little wider (for easier reading). type:


lsusb

Do you see your Logitech device listed? Here is my lsusb in relevant part:

mark@Lexington-19:~$ sudo lsusb

My Logitech MK320 is working. May I suggest what will seem like a dumb idea? Uncork (remove) the Logitech USB dongle. Reboot, by which I mean power down and reboot. Power down again, re-insert the USB dongle and power back up. Let me know, please, how it goes.

With out this, i wouldnt have been able to fix my mouse. Thanks!

---

### Post by rykel on 2011-09-12
Hello, I have a Prolink PML303 2.4G Wireless Mouse and need to re-pair it with a different dongle.

I was told to find a software called "RF Desktop" for Windows.

However, I am 100% Ubuntu 10.10 and wonder if there is a similar solution in our Linux software center?

---

### Post by walt.smith1960 on 2011-09-12
I don't know about that particular model but Logitech has a button on the device and a button on the receiver.  Generally press the button on the receiver then press the button on the device - mouse or keyboard - within so many seconds.  It's hard for me to see how this could be done via software unless the device were always "looking" for a new receiver.

---

### Post by gakon77 on 2011-10-06
Mine is working now too!!! :P

Thanks.

---

