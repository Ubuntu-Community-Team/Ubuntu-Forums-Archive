---
title: "Interesting problem laptop running 9.04 server"
date: 2009-11-15
forum: Hardware
---

### Post by MI_Diver67 on 2009-11-15
Laptop Compaq 3045us
[LIST]
[*]managed to load Ubuntu 9.04 server without knowing it didn't have a GUI
[*]How do I upgrade to or just install a new OS possibly using network or USB drive?
[*]DVD ROM drive will not read disks (why? unknown)
[/LIST][/LIST]

Thanks!

---

### Post by MI_Diver67 on 2009-11-16
Really? 27 views and no replies? I can't say that I'm surprised. I don't know enough to know what to ask.

---

### Post by Mze on 2009-11-16
[Pen Drive Linux]("http://www.pendrivelinux.com/")

---

### Post by MI_Diver67 on 2009-11-18
> **Mze said:**
> [Pen Drive Linux]("http://www.pendrivelinux.com/")
Thanks for the idea! I would like to try this however the computer I have does not have a USB boot option. Is it possible to update the MBR or BIOS to have that option?

I see the option to make a USB boot CD for computers w/out the USB boot option. I hope I can get it to work. I've got some great posts/suggestions to work with.

---

### Post by teward on 2009-11-18
try updating your BIOS, then look for Removable devices on your BIOS boot list.  If it exists, move it to the top position, or before the hard drives.  THat should allow you to USB boot.

---

### Post by unamanic on 2009-11-18
To install all of the packages that ubuntu would have (includeing gui) just issue the following
```

sudo aptitude install ubuntu-desktop

```I'm not sure why your dvd-rom drive would not read disks on boot (i'm sure you checked to ensure it was first in boot order), but I don't think ubuntu server mounts them automatically so you have to mount them to read them.  Once you have the full ubuntu installed if your drive is working it should auto detect it.

---

### Post by MI_Diver67 on 2009-11-18
Thanks unamanic. I used the code and it said "couldn't find any package whose name or description matched "ubuntu-desktop".

TrekCaptain: How does one go about updating their BIOS?

I hope I don't sound dumb; I just don't know but am willing to learn!

---

### Post by unamanic on 2009-11-18
It the machine connected to the network?  If yes, I forgot to have you do an:
```

sudo aptitude update

```
before the
```

sudo aptitude install ubuntu-desktop

```

---

### Post by MI_Diver67 on 2009-11-18
There is no update for the BIOS on HP/Compaq site. There is however an option to do a network boot.

---

