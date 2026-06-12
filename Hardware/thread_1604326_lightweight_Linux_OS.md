---
title: "lightweight Linux OS"
date: 2010-10-23
forum: Hardware
---

### Post by Joe Awsome on 2010-10-23
I have an old laptop from the late 90's that my school IT guy gave to me a while back, it's an HP Pavillion N3390. Needless to say that I am looking for a linux OS to put on the old thing. System specs are: An Intel Pentium three at 600Mhz, 128Mb SODIMM RAM, and an IBM 10gig HDD. I'm not looking for wonder-ware to help revive this old thing, but I just need something that will run reasonably well and has compatibility with ndis-gtk and usb flash drives. I would prefer something debian or ubuntu based just because I'm familiar with the bash syntax. The only reason I'm even trying to revive this thing is so that I have something to use on my trip to Colorado this weekend. I have tried lubuntu and vector linux with little to no success. Any sugestions?

---

### Post by slooksterpsv on 2010-10-23
I think if you did Crunchbang Lite Edition that may work well.

---

### Post by krazyd on 2010-10-23
That's a pretty low-powered machine.. but a fun challenge! :D

If you really want to go the Ubuntu route, I think you'll have to do a CLI install and build up a lightweight X stack yourself:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

There are a couple of other options which might be worth checking out - Puppy Linux, and Tiny Core Linux:
[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)
[http://tinycorelinux.com/](http://tinycorelinux.com/)

Whatever way you go, it might take a bit of tinkering to get running. Good Luck!

---

### Post by slooksterpsv on 2010-10-23
> **krazyd said:**
> That's a pretty low-powered machine.. but a fun challenge! :D

If you really want to go the Ubuntu route, I think you'll have to do a CLI install and build up a lightweight X stack yourself:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

There are a couple of other options which might be worth checking out - Puppy Linux, and Tiny Core Linux:
[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)
[http://tinycorelinux.com/](http://tinycorelinux.com/)

Whatever way you go, it might take a bit of tinkering to get running. Good Luck!

Haha i just tried TinyCore... and well its.... AMAZING!!! I installed firefox and flash and watched video's didn't have sound turned on (it was in a VM) so I dunno if that worked, but 11MB ISO + whatever you download, flash + firefox = 30mb - installation of flash was odd /usr/share/bin/getFlash10.sh - but other than that it was great!

So yeah otherwise Puppy, I like Puppy too... hmm (off to dl the iso for Puppy).

---

### Post by mr clark25 on 2010-10-24
you might also try damn small linux, although it is very basic and it is not debian based. (i dont think it is debian based...)

let us know how tinycore linux goes-- i might want to try it myself.

i wouldn't call that laptop* that* old. i have a p3 laptop that runs at 1ghz and has 512mb ram with a 30gb hard drive. (if you think about it, there really isnt that much difference...) it runs Ubuntu 8.04 just fine. (but the 512mb ram really helps...)

---

### Post by Joe Awsome on 2010-10-24
> **mr clark25 said:**
> you might also try damn small linux, although it is very basic and it is not debian based. (i dont think it is debian based...)

let us know how tinycore linux goes-- i might want to try it myself.

i wouldn't call that laptop* that* old. i have a p3 laptop that runs at 1ghz and has 512mb ram with a 30gb hard drive. (if you think about it, there really isnt that much difference...) it runs Ubuntu 8.04 just fine. (but the 512mb ram really helps...)

I'll bet that extra ram does help, I had a 128mb stick, but that died on me. So now I'm back to just two 64mb sticks in the lappy-486 (just for all you StrongBad fans out there). Tiny Core doesn't lsound bad, definately an option, and sounds like a viable one too. I'm a bash noob so I'll see how that works.

---

### Post by sidzen on 2010-10-24
Since "I would prefer something debian or ubuntu based. . .", I would recommend

antiX-M8.5-, either i486 for 128MB RAM or i686 for 256+
[http://www.mepis.org/node/10](http://www.mepis.org/node/10)
Good support, too!

---

### Post by ugm6hr on 2010-10-24
This appears a good summary of what's out there... Your 128MB may limit things somewhat though.
[http://www.tuxradar.com/content/whats-best-lightweight-linux-distro](http://www.tuxradar.com/content/whats-best-lightweight-linux-distro)
Slitaz is a nice option, and apparently runs in a "loram" mode on 80MB Ram.
I toyed with it briefly, but had 256MB on my old lappie.
Puppy may be worth trying - it certainly used to work on 128MB, but I haven't used it since v2 for any length of time. Puppy has always had a nice wifi configuration app... Not sure about Slitaz.

---

### Post by Joe Awsome on 2010-10-25
I tried SliTaz, and found it very slow and laggy on the old laptop. I only tried it once though. I am seriously considering Tiny Core as my best option right now simply because of ndiswrapper in the repos for it. mepis is another option i'll try when i get time, haven't had time for Tiny core yet either. high school senior year you know.

---

### Post by waynefoutz on 2010-10-25
Lucid Puppy is the way I would go on a machine like that.

[HTML]http://puppylinuxnews.org/releases/lucid-puppy-51-is-released/[/HTML]

---

### Post by Joe Awsome on 2010-10-26
well I'm halfway through the install for tiny core, and i love how fast and responsive the os is. If the installation onto the hard drive is sucessfull then I'll just use that, wifi suport for my usb card should good because of ndiswrapper. Wifi workd fine under ubuntu so right now everything tells me that it should work under tiny core. I'll keep you guys posted when I finish the install.

---

### Post by Joe Awsome on 2010-10-27
well I finaly got one of the two laptops working, I had another laptop of similar hardware but it was a gateway. The reason I was trying to get the HP working was so that I at least had a battery with some life left in it. Then I realized on an atempted install on Tiny Core that I only got around 50 min of battery life. So I just grabed the gateway and did a lubuntu 10.04 install on it. works great too, i even got the 128 stick to work in it. apparently the 128 stick didn't sit too well with the HP for some reason. So I at least have a working laptop to use in the room for wi-fi. posting right now from the gateway!

---

### Post by ssulaco on 2010-10-28
You could buy another stick of 128 and max it out to 256......its cheap enough
[http://www.memorystock.com/memory/HewlettPackardPavilionn3390.html](http://www.memorystock.com/memory/HewlettPackardPavilionn3390.html)

---

### Post by Joe Awsome on 2010-10-28
I actauly found out that another kid at school has an extra stick of 128 ram laying around, so I decided to trade him two 64mb sticks for it. He's bringing it over on friday, thanks for that sugestion anyways. I might just try Vector Linux after senior trip because lubuntu droped i386 compatibility on 10.10. I don't why, that was a large potencial market right there. So it's either Tiny Core (if I can ever get the install right), or Vector Linux if it'll boot right. Thanks for all the help guys! :)

---

