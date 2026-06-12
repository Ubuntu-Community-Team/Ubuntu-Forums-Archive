---
title: "Is my laptop still good enough? For any?"
date: 2015-12-01
forum: Hardware
---

### Post by Higgins909 on 2015-12-01
I've got a dell inspiron 1440, 4gb ram, 250gb storage, pentium t4200.
I've had a on an off thing with using ubuntu or some linux with it.
I had windows 7 on it yesterday, firefox was feeling slow.
I put ubuntu 14.04.3 lts 64bit.  
It takes a bit longer to load then I would like but that may be my sata 1 hdd that has had plenty of use.
When I first had firefox going, it was really slow that it would take several seconds to open or close a tab.
Even now it feels right about where the windows 7 speed was, which was degraded from its brand new form.
(its about 7 years old)

Should I consider a different version of ubuntu?  The thing is I want things like "ubuntu software center" still.
There were a few other things I liked about it too, that arn't coming to mind....
I wanted to use this laptop for web, school, and maybe programming and I wanted it to be snappy at that.
As I'm typing this, its deciding to behave better, performance wise it seems....
I thought about maybe getting a used macbook of similar age and either using osx or ubuntu.
Or there was a dell latitude e4500 or similar that sounded nice.  Probably put a ssd in either if I get one.

Overall, what would be a good os for my laptop, with some nice features, like ubuntu software center?
(I want to check out all the apps it has, books, developer tools, graphics, etc.)

Thanks,
Higgins909

---

### Post by weatherman2 on 2015-12-01
Sounds like something is wrong with the laptop.  I am using regular Ubuntu (12.04) on a couple of Dell E1505 dual core (Core Duo) 1.83GHZ 2GB RAM laptops and they are quite usable - not exactly super fast but very usable.  One of my relatives uses one daily for basic web browsing.  They've got to be SATA I - these are 2006-era laptops, and the E1505 I bought new was the first new Dell I bought with SATA.

On a laptop that old, I would do some basic checks and maintenance:

1. Check the hard drive.  Check the S.M.A.R.T. health and run the extended S.M.A.R.T. test on it.  You can do this on a live USB boot of any version of Ubuntu, but I prefer to use the GSmartControl program.  You probably have to install it, and that means you should have the laptop on the internet (wifi supported when you boot?) to install.  You have to enable the "Universe" repository (open "Ubuntu Software Center" in the regular version of Ubuntu and change preferences) then install gsmartcontrol.

In GSmartControl, you can see any current Attributes that have failed if any - that would be any line highlighted in red/pink.  (Look for any line with "sectors" - a raw value greater than zero is usually bad.)  Also you can run the Extended S.M.A.R.T. test from one of the tabs - might take an hour or two

2. Clean out the CPU heat sink and fan.  When these get dirty (extremely common on older laptops), the CPU may overheat because it can't be cooled properly, and this can lead to reliability problems, freezes, and even "throttling" where the CPU gets slowed down to keep it cooler.  Taking the laptop apart to get to the CPU heat sink and fan can be a challenge depending on the design of the laptop.  Sometimes it's easy.  Look on line for a tear-down guide for your laptop or even a YouTube video showing you how to take it apart.  Dell may have a service manual too with step-by-step instructions.

---

### Post by weatherman2 on 2015-12-01
Also, in "regular Ubuntu" I prefer to use "Gnome Flashback" (not the default "Unity" interface) with Metacity on older laptops.  It is generally much faster than Unity:

[http://www.howtogeek.com/189912/how-to-install-the-gnome-classic-desktop-in-ubuntu-14.04/](http://www.howtogeek.com/189912/how-to-install-the-gnome-classic-desktop-in-ubuntu-14.04/)

---

### Post by Higgins909 on 2015-12-01
Thank you!
There was a nice wall of hair/dust bocking the vent...  The only way to get to it tho was to take the heatsink off.
I then found out that there was little thermal paste on the cpu, it had all fallen around out and on the other chip-
it was this weird rubber/sponge like thermal paste.  I cleared it out and put some cheap coolermaster paste i had lying-
around on.  Quite that difference that has made in heat and noise of the laptop.
I cleaned out the fan once before a few years ago and removed a hairball from the fan.

Guess I gotta take better care of where I run my laptop.
Might get the gnome flashback later on or may try to get openbox going.(failed at openbox so many times now)
I also found out that my bios battery is dead... I think.

---

### Post by weatherman2 on 2015-12-01
Yeah, it's amazing what cleaning out the heat sink can do on an old laptop!

Give Gnome Flashback a try - it feels "old school" for sure but for basic use on an old laptop it works great - and fast!  I use it every day.

You can probably live without a CMOS "BIOS" battery as long as you leave your main battery and/or leave it plugged in.  But if your CMOS battery is easy to get to, not soldered in, etc., I'd probably replace it.  Sometimes the battery is held in by an easy-to-break plastic holder (which I have broken on a Dell laptop before!) so be careful if you do.

---

### Post by sammiev on 2015-12-01
Ubuntu-mate is worth the trip as well. 

I use Ubuntu-gnome but on one old laptop, Ubuntu-mate does seem to rock.

---

### Post by sudodus on 2015-12-02
There are several light-weight flavours of Ubuntu, that work well in older computers. The desktop environments are different, but the engine under the hood is the same. Try first and then install what you like the best,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

