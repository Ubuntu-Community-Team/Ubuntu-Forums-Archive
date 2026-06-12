---
title: "How resource heavy is ubuntu on older machines?"
date: 2009-04-19
forum: Hardware
---

### Post by stevh0 on 2009-04-19
I have an old acer laptop. 

850mhz, 256mb blah blah blah.


What distro of ubuntu would run easier on the machine without hogging too much of its little proccessing power.

I dont really want to use the laptop as a doorstop yet. I think the laptop could be a nice little project.


Im running gutsy on a 2ghz desktop and with some of the visual effects turned on, I can see it hogging some power... 

Any other recommendations?

List of distros currently available

Ubuntu 8.04
Ubuntu 7.10
Mandrake 6
Knoppix 5
Linspire
Gentoo
Very old redhat and slackware disks too.

---

### Post by ajgreeny on 2009-04-19
Just about all that you list really need more than the 256MB ram available, but if you could up it to 512 then you are more likely to get a worthwhile experience with those.  You could, however, try other linux distros which don't need so much ram or processing power, such as DSL, Puppy, or look at Crunchbang, though that may still be a bit heavy, depending on the applications you choose for it.

---

### Post by snowpine on 2009-04-19
> **stevh0 said:**
> I have an old acer laptop. 

850mhz, 256mb blah blah blah.


What distro of ubuntu would run easier on the machine without hogging too much of its little proccessing power.

I have successfully run CrunchBang linux on a laptop with similar specs. If you are looking for an Ubuntu-based distro, that would be my suggestion. Good luck!

---

### Post by stevh0 on 2009-04-19
Ive just downloaded puppy ... ill drop that on there and see how it goes... if at all :) 

I just like ubuntu, as im not really much of a techie when it comes to troubleshooting and hardware in Linux.

Linux is so user friendly too

---

### Post by ecorley on 2009-04-19
You may want to try Xubuntu as well; should run pretty good.  Puppy should fly on those specs though! :)

---

### Post by Tobywuk on 2009-04-19
I am currently in a very similer situation as you. 

I hear Xubuntu was good for lower end machines but I had problems, not with running it but with using the notebook in a closed position while attached to my monitor.

I now have Damn small Linux on it, and I dont like it. works fine and is very light weight but im familiar with ubuntu (apt etc..). 

I would be interested to hear your opinions on puppy linux :)

---

### Post by sideaway on 2009-04-19
Download the minimal install disk, and then install drivers  accordingly and probably the XFCE interface and you should be good to go. If you like Ubuntu, stick with it. It's suprisingly lightweight, just don't install Compiz :)

DSL is based on Knoppix, and I believe you can install sudo for it. ...and doesn't it utilise apt-get as debian/ubuntu does?

---

### Post by RedSquirrel on 2009-04-19
As sideaway has suggested, install a minimal, command-line system and build up from there. For example:

  [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by stevh0 on 2009-04-23
I installed puppy, it even detected a wifi usb stick.. really impressed with the functionality, but from an overall package, it could have been better.

repro's out of the box arent available and this makes updating a pain if you dont know much about compiling. 

Right now the most important thing to me is the functionality of it.

---

### Post by shel-hall on 2009-04-23
> **stevh0 said:**
> I have an old acer laptop. 

850mhz, 256mb blah blah blah.


What distro of ubuntu would run easier on the machine without hogging too much of its little proccessing power.
I'm running Ubuntu 8.10 on a nameless Taiwanese 10-year-old P-III/750 laptop with 256 MB RAM.  Works fine.

However, I did strip out a few things.  I ditched Compiz (no need for "effects"), Pulseaudio (to get the sound working), and all the Bluetooth stuff, mainly.  I started with the "normal" 8.10 ISO and worked down, rather than a minimal ISO and working up, but I think the latter might be a better, if slightly more difficult, approach.

Everything works well enough, and it's not slow at all.  It's about like Windows XP on my 1.7GH/1.5GB laptop.

-Shel

---

### Post by stevh0 on 2009-04-23
my biggest problem is the lack of usb booting and the faulty cdrom. it reads every now and then. the 100mb was really Godsent .. 

If i could somehow upgrade the bios or install ubuntu via terminal of puppy I would be set!

---

