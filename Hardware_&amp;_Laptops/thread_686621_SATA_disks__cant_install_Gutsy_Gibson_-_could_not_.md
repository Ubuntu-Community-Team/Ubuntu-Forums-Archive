---
title: "SATA disks / cant install Gutsy Gibson - could not create SWAP"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by rado1100 on 2008-02-03
my Ubuntu 7.10 cant install - it shows that the SATA disk is on, but it cant create swap , .
( Windows XP cant install, it does not see any hard disk )
I dont know, i will try Feisty Fawn, can it help???
I am now running Fedora 8, but almost no program i want runs there... :(
I WANT UBUNTU BACK!!!!!! :mad::mad::mad:

---

### Post by rado1100 on 2008-02-03
bump? Please people help, my father gave me a notebook but i cant use it :((((((
i am sad - i got a great gift but it is useless to me :((((

---

### Post by hyperair on 2008-02-03
Strange, I was pretty sure many apps were common to both Ubuntu and Fedora (among other Linux distros). 

Try waiting for Hardy to come out.. it's in another 2 months. =P Or you could grab the Alpha and install it. Highly unadvisable though, it's still development stage and unstable.

---

### Post by rado1100 on 2008-02-03
Hardy is new release of Ubuntu? Be sure I will wait for it...

Yeah there is Skype for fedora - a bug in some component disables install...
Yeah there is [TORIBASH]("http://www.toribash.com/") for Fedora - does not work...
Yeah, there is Java for Fedora - it helps the same thing as on Debian : holy sh*t
Do I really have to continue???

---

### Post by Yellow Pasque on 2008-02-03
Technically, you don't even need to create a swap partition to install. I did an installation of Hardy on a spare disk that I set up without swap since I already have a swap partition on my main disk (which wasn't hooked up at the time I did the install because I didn't want to bork GRUB).

So do you think you can give a little more info so we can troubleshoot your problem?
First, does the LiveCD start/run?
If so, let's run a command so that we can see how your disk is layed out.
```
fdisk -l
```

Also, do you think you can be a bit more specific about any error messages you get during install?

---

