---
title: "no GUI after alternative install on X201"
date: 2010-04-18
forum: Hardware
---

### Post by gregnorc on 2010-04-18
So I had been having problems getting unetbootin to create a working USB drive that I could install Ubuntu from. It would get as far as startup, I'd hear the african noises, then get a black screen.

Someone suggested I use the alternative install cd, so I used unetbootin to put that iso onto my usb drive. This worked. 

However, I only have command line access to ubuntu right now... how would I go about adding the various graphical elements? I have a [**Thinkpad X201**]("http://www.thinkwiki.org/wiki/Category:X201"), with the following hardware specs:

Intel® Core™ i5-520M
500GB 7200RPM 2.5" SATA 
4GB PC3-8500 RAM
[Intel HD graphics]("http://www.thinkwiki.org/wiki/Intel_HD_Graphics")

Any help is greatly appreciated, I'm pretty proficient with the command line, but this is pretty major and I have no clue where to begin. 

Thanks!

---

### Post by vtcat on 2010-04-18
Not positive on this, but I think it's
```
sudo apt-get install ubuntu-desktop
```

---

### Post by gregnorc on 2010-04-18
> **vtcat said:**
> Not positive on this, but I think it's
```
sudo apt-get install ubuntu-desktop
```

Success! I've got a GUI now, wired ethernet works, just gotta get the wifi up and running and I'll be set (right now network manager doesn't even list any networks available or anything...)

---

