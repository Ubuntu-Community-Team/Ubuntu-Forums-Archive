---
title: "Possible to make a current install into an Ubuntu Remix?"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by last1 on 2009-10-17
I'd like to create a custom ubuntu bootable usb drive that is an exact clone of the system I currently am running, right down to all the config files, basically a complete clone of the system I have, but bootable on another machine. What I need is some ideas as to how I could do this, as the only documentation I could find on the subject, the LiveCDCustomizationFromScratch page, has instructions only pertaining to building a new livecd from packages, which is not what I want to do. 

Is it possible?

---

### Post by beastrace91 on 2009-10-18
Why don't you just install Ubuntu to a flash drive? This way you can add/remove applications as you want and you can make changes when ever.

~Jeff

---

### Post by last1 on 2009-10-18
Because the system I would like to clone is already set up the way that I'd like the other machine to be, with dozens of applications, many installed through means other than a package manager, and heavily edited configurations and manually added toolsets. Only some  of which would be possible to easily replicate onto a new system through the method you suggest. I mean for the system to be part of a graphical render farm, and in the way i want to use it, it needs to be the exact same as the system I want to clone from. 

I realize there are other (inferior) methods to achieving my goals, but this thread is merely inquiring as to the possibility of doing it the way I would actually like to do it, in the way I feel would be most useful for my situation.

---

### Post by beastrace91 on 2009-10-18
Alrighty, well [this](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html) appears to be what you are looking for. Just create the custom .iso file and then use unetbootin to send it to a thumb drive.

I would still recommend installing straight up to a flash drive, this will give you much better load times on applications and allow you to make changes down the line. Depending on how big your install is if you have a flash drive big enough you should be able to clone your hard drive over to it.

~Jeff

---

### Post by earthpigg on 2009-10-18
+1 for remastersys.

---

### Post by last1 on 2009-10-18
Thanks guys. :)

---

