---
title: "webcam driver issue?"
date: 2013-01-01
forum: Hardware
---

### Post by faceshed on 2013-01-01
tldr: I want to have skype calls and skype will not use my web cam for some reason.

I checked a few guides, but I'm having a hard time understanding some of the linux 'jargen' so please excuse me if at the end of this all you have to do is describe what some button looks like or something.

specs:
asus Eee disney netpal P.O.S. with a cracked screen.
Ubuntu 12.04.1 LTS 32 bit
Multi-boots into a broken install of windows XP sp3 that can't connect to the internet
The webcam is built into the screen. Sorry I can't find any more info on it then that.
Also note that there's a very very small hard drive on this thing so I can't download anything bigger then a few hundred MB.

So if I go into Skype in the settings there is no webcam showing and no device to pick from. I don't know what kind of webcam it is other then it's internal. I suspect that it's a driver issue so I tried to get that sorted and got a "ov51x-jpeg" but when I try to "make" in the terminal it tells me  "make: *** No targets.  Stop." I guess it doesn't understand that I want it to make the file named Makefile but I have no idea what to do about it. Next I tried "lsusb" :
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```I guess the webcam is missing because it's not a usb cam?

It's important for me to have the ability to call people over the skype protocol, but I'm willing to use something other then the skype program if that helps make things go quicker/easier.

Thanks for any help.

---

### Post by faceshed on 2013-01-03
I have a feeling that the problem is one of the Fn keys turns off the webcam, but I don't know if they do even control the webcam or which one does.

Any ideas?

---

### Post by offgridguy on 2013-01-03
Hello and welcome to the forum, i had to go to the software center and install one
of the web cam apps. from there to get my integrated webcam working.
It is not a large download, i hope it works for you.

---

### Post by faceshed on 2013-01-03
> **offgridguy said:**
> Hello and welcome to the forum, i had to go to the software center and install one
of the web cam apps. from there to get my integrated webcam working.
It is not a large download, i hope it works for you.

Thanks offgridguy.
I got cheese and opened it, but it just says "no device found".

---

### Post by offgridguy on 2013-01-04
> **faceshed said:**
> I have a feeling that the problem is one of the Fn keys turns off the webcam, but I don't know if they do even control the webcam or which one does.

Any ideas?
Looking at my new laptop, I can't see an Fn F key that controls the webcam. I do know that on my older laptop there was one that did, I will check it out when I get back home, other than that I
am out of ideas, sorry.

---

### Post by Nevetsjc on 2013-01-12
Use sudo lshw to list all the hardware on your PC
Then look for the webcam, and it should have 4 digits/letters looking like 00:d1 - then use that to try and find a driver for the webcam (which I'd say is why Cheese and Skype can't pick it up)

---

