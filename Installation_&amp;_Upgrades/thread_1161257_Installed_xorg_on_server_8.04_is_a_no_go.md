---
title: "Installed xorg on server 8.04 is a no go"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by rugbert on 2009-05-16
So Ive decided I wanted a desktop on my server. installed the desktop environment, xserver,  and xorg but trying to run startx I get a blank screen.

Im using a nvidia card for output but since the terminal works just fine Im guess its not a driver issue. any thoughts?

---

### Post by erixoltan on 2009-05-16
Have you tried booting the server from a Live CD of Ubuntu Desktop?  If that works, it will rule out the possibility that it is the system itself and you can focus on which packages you have and how they are configured.

---

### Post by rugbert on 2009-05-16
> **erixoltan said:**
> Have you tried booting the server from a Live CD of Ubuntu Desktop?  If that works, it will rule out the possibility that it is the system itself and you can focus on which packages you have and how they are configured.

well i wanted to do a fresh install anyway, but for some reason my system wont let me boot to a cd.. Its a frankencomputer and even tho my motherboard's BIOS sees the dvd drive, it refuses to boot to it. like, when I power on, the mobo splash screen hangs and then it just boots to my harddrive.

---

### Post by rugbert on 2009-05-16
> **erixoltan said:**
> Have you tried booting the server from a Live CD of Ubuntu Desktop?  If that works, it will rule out the possibility that it is the system itself and you can focus on which packages you have and how they are configured.

effer. i was able to get a bootable USB to boot but yea...after the ubuntu load screen finishes loading it goes black. maybe its the video card?

edit - no, tried two different video cards. but hitting alt-ctrl-f2 opens terminal.... why wont it work>??

---

### Post by erixoltan on 2009-05-16
I totally hear you.  On my ancient server, I have to insert the CD when I power up, select the boot device, but wait about 3 minutes for the CD drive light to stop flashing before I press Enter.  If I'm not paying attention and wait more than a few seconds after it stops flashing, then it won't find the boot track on the CD and it boots from the HD instead.  I only discovered this after trying it over and over again in frustration.  

Here's one more thought, it was next on my list when I discovered the above trick.

[https://help.ubuntu.com/community/BootFromUSB#Booting%20via%20grub](https://help.ubuntu.com/community/BootFromUSB#Booting%20via%20grub)

---

### Post by rugbert on 2009-05-16
well i got it to boot from USB but i still get a black screen. i can open a terminal and have that display tho...whats the deal? the video would be dependent on the card right? Ive tried to separate cards!

---

### Post by rugbert on 2009-05-17
Annnnnnnd Im an idiot!

I neglected to mention that in lieu of using a normal monitor I plugged my server into my TV...so the resolution was too high! UGH!

CASE CLOSED!

also - now that I can get into gnome, I cant login. root isnt allowed to login and my normal user name doesnt seem to work. do I have to create a new user from terminal? or how can I get my normal one to work?

---

