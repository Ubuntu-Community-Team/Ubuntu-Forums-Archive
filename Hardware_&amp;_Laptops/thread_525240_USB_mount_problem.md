---
title: "USB mount problem"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by barisy on 2007-08-14
Hello everyone;
The thing is here that i think i am not sure that my USB ports are running on my desktop?!
I am checking that from the SYSTEM -> PREFERENCES -> HW INFORMATION but i can't see any obvious line about USB gadgets. Anyone can help me on this issue please.

Thank you :)

---

### Post by barisy on 2007-08-14
Should i quit ubuntu and back to windows :(

---

### Post by DirtDawg on 2007-08-14
If you want to go back to Windows, that's fine with us. People who help here are volunteers. Please wait more than 45 minutes before getting impatient about a response. If you want to speak to someone immediately, try the [Ubuntu IRC channel]("http://www.ubuntu.com/support/community/chatirc").

That said, your post is not clear. You can copy/paste this command into your terminal (Applications>Accesories>Terminal) and it will tell you how many USB ports are detected. 
```
 lspci | grep USB
```
For example, I have 4 USB ports, so the output on my computer looks like this:
```
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)

```
If you have 6 USB ports but only 4 are listed, for example, then not all your USB ports are being detected.

If you have a hard drive or some other hardware already plugged into a USB port but it's not being detected, then that is a different issue and you will need to give us more information.

---

### Post by barisy on 2007-08-14
Thank you for your help, since i am a newcomer i have to learn out these things. I wrote the line lspci but theres no output popped up, that means USB drivers doesn't installed right?

---

### Post by matburton on 2007-08-14
Hey,

Just to check that when you did:
```

lspci | grep USB

```
the "USB" part was in caps! I think that would be a common mistake. Otherwise it does look like no USB controllers are being detected.

---

### Post by barisy on 2007-08-14
Yeah :) Definitely in CAPS .. i think i have to find the exact USB drivers looking up for my main board right? If there's any site doing it automatically i would be the happiest man in the planet :lolflag:

---

### Post by DirtDawg on 2007-08-14
> **barisy said:**
> Yeah :) Definitely in CAPS .. i think i have to find the exact USB drivers looking up for my main board right? If there's any site doing it automatically i would be the happiest man in the planet :lolflag:

You shouldn't need to install any drivers. I've never heard of USB ports just flat out not being detected. Please post the output of this command:
```
 lsusb 
```

---

### Post by barisy on 2007-08-15
You know what? i wrote the command and it says
```

root@baris:/home/baris# lsusb
root@baris:/home/baris# 

```

means "never heard of it" :)

---

### Post by DirtDawg on 2007-08-15
> **barisy said:**
> You know what? i wrote the command and it says
```

root@baris:/home/baris# lsusb
root@baris:/home/baris# 

```

means "never heard of it" :)

Yes that's no good. Sorry, but I can't say I know what to tell you from here on. Maybe you should try starting another thread like "usb not detected" or whatever. Many people have trouble with devices not mounting correctly, but usb ports not being detected at all is unusual. Hopefully someone with some experience with this issue can help you out.

Good Luck.

---

### Post by barisy on 2007-08-15
Thank you for your consideration. I am engaging a new threat.

---

