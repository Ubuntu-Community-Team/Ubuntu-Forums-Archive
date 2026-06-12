---
title: "HP dv7 IR receiver and fingerprint reader not recognized"
date: 2008-10-07
forum: Hardware
---

### Post by mbarak on 2008-10-07
My HP laptop comes with an IR Receiver and a media center remote that worked perfectly under Vista but doesn't seem to be recognized at all under Ubuntu
The same situation applies for the fingerprint reader

here is my lsusb:
```
mbarak@mbarak-laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 046d:09b8 Logitech, Inc. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 138a:0001  
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by yachoo on 2008-12-10
If you still have a problem: update your BIOS through Vista. Remote controll should start to work. Fingerprint is a problem with ubuntu. But you already know it... :)

---

### Post by mbarak on 2008-12-10
for the fingerprint reader that process is started - it turns out its a Validity device and the only thing needed to make it work are drivers :)
as for the remote - I flashed the BIOS with HP's utility and still no luck
/dev/lirc0 just isn't being created
in fact, the ir receiver doesn't even show up on lsusb nor lspci for that matter

I don't know if it's related - but at boot i've always gotten this message saying "unable to enumerate usb device on port 1"

---

### Post by genus_001 on 2009-03-12
Has anybody had any luck with this?  I've read that some other Pavilion's(dv4 dv5) IR ports work with no problem.  In fact, I'm having a hard time even identifying the make of the port.

---

### Post by rolandixor on 2009-05-09
any sucess?

---

### Post by genus_001 on 2009-05-09
I wish.  Pavillion dv7 is such a pain.  No remote or IR Port.  Microphone doesn't work. Just upgraded to 9.04 going to try everything again.  Not giving up!

---

### Post by mbarak on 2009-05-09
When i upgraded to Jaunty, i lost my microphone...

---

### Post by rolandixor on 2009-05-21
same for me. lost the internal mic with jaunty. trying to find a solution, though I kinda gave up.

---

### Post by mbarak on 2009-05-21
me too, kinda
although i do come back every once and a while to try to get it working again (usually when i need the microphone...)

---

### Post by mbarak on 2009-05-24
Microphone WORKS with new version of alsa :-)
use the alsa upgrade script here:
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by rolandixor on 2009-06-02
worked for me! :D

Now to conquer the remote. Any news on this? I'm busy working on a custom distro for educational purposes so I can't stop to do too much.

---

### Post by supernerd1991 on 2009-08-07
I just bought this system and the first thing I tried to do was install a copy of ubuntu on it. 64 bit was not working for some reason (it is a 64 bit system). The webcam has issues with flash and everytime I try to use it in Facebook, it just sits there. It does not say the webcam is not detected, like on my old computer. The microphones are not working. Everywhere I go says that the remote should work out of the box, then it said after the bios upgrade so i did that, and it still does not work. Finally the wi-fi button light remains in a disabled state, it works it is just orange, and the media smart program acts like a 'V'.

---

### Post by genus_001 on 2009-08-17
I'm glad to see other folk are putting GNU/Linux on this computer... I read on another forum that if you still had Vista installed (ie dual boot) you could uninstall the drivers for the IR port and remote(in Vista), and then it will magically work in Ubuntu. 

I have serious doubts that this will work, but am sickly interested, you never know.(This would mean that Vista is writing something to the firmware that incidentally makes it unrecognisable in other OS's, i guess if that were the case, the updating the BIOS could solve that problem...)
 
If anyone on this thread still has Vista installed on their computer, maybe we could try this and see of that will bring us closer to solving the problem.

As for the wireless light and Media Button, i never got mine to work properly either. Although touching the wireless button does toggle the card on and off, just not the light.

My card reader acts funny also. It will only read a card if it is present at boot. If I put an SDHC card in after the system has loaded, it wont see it...

---

### Post by rolandixor on 2009-08-20
I uninstalled the receiver, and no results so far. Anyone have info on setting up a remote in ubuntu that could help with this?

---

