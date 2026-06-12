---
title: "asus eee pc 900 extremely slow"
date: 2011-12-31
forum: Hardware
---

### Post by noxified on 2011-12-31
i just bought an asus eee pc 900(900 mhz) ,from someone.i upgraded ram memory to 2gb ,and upgraded bios version(old bios did not let me to install linux on eee pc)
i tryed ubuntu(10.04,with gnome 2) and now i'm using lubunu 10.04(installed on 8gb ssd).Still very slow. terminal with apt-get update,and chomium with 2 tabs opened(ubuntu forums,and yahoo mail-login page) makes the cursor laggy.
i updated system,upgraded,installed intel video drivers..
what can i do?or,what system should i use for this machine ,to run flawless?(i dont really like openbox/fluxbox,but i tryed them ,and it's the same speed-installed from minimal cd)ofcourse,i dont expect same resoults as an quad core..
but,laggy cursour?!

---

### Post by 2F4U on 2011-12-31
I would suggest a lighter desktop environment such as XFCE or LXDE, available through Xubuntu or Lubuntu. If you want to stick to Ubuntu, first of all disable as many autostarted programs as possible. Then use top or htop to see what causes the heaviest load on the CPU. I would also suggest to turn off all desktop effects, if they are turned on.

---

### Post by noxified on 2011-12-31
> **noxified said:**
> now i'm using lubunu 10.04(
:confused:

---

### Post by snowpine on 2011-12-31
What is the SSD configuration on you machine? There were several models of EEE900 manufactured. Some of them have two SSDs: a slow one and a fast one. If that's the case for your computer, you want to make sure to install to the fast SSD (usually the smaller of the two)--it will make a big difference. :)

---

### Post by noxified on 2011-12-31
as far as i know,the small one,it's integrated in the motherboard.(i read something on the internet about that,i wasn't sure ,why i've got 2 hard drives)and the 2nd one it's ssd for sure.)
4gb for operating system,i'm not sure that would be enough.even i use minimal things installed...
so,that would be ONLY solution available ? install lubuntu on the 4gb chip memory?

---

### Post by KBD47 on 2011-12-31
Just a suggestion, I installed Lubuntu to an 8 gig usb stick once and it was terribly slow, just not enough memory even though it says it will install to less memory. But on a 16 gig usb stick with 1 gig swap Lubuntu will fly. An 8 gig hard drive is very small for most operating systems. I would get a 16-20 gig stick and do an ext4 partition for Lubuntu install to the stick with a swap partition of about a gig and that should run fast for you.
KBD47

---

### Post by Dennis N on 2011-12-31
For one thing, I suggest you install a newer version of Lubuntu for best results, preferably from a Lubuntu Live CD or USB instead of installing the Lubuntu desktop atop an existing Ubuntu. - suggested are Lubuntu 11.10 or 11.04. Improvements have been made since 10.04 was released. It may make a difference.

---

### Post by snowpine on 2011-12-31
> **noxified said:**
> as far as i know,the small one,it's integrated in the motherboard.(i read something on the internet about that,i wasn't sure ,why i've got 2 hard drives)and the 2nd one it's ssd for sure.)
4gb for operating system,i'm not sure that would be enough.even i use minimal things installed...
so,that would be ONLY solution available ? install lubuntu on the 4gb chip memory?

**If** your EEE 900 has a 4gb and an 8gb SSD, the 4gb is the fast one.

[http://liliputing.com/2008/05/eee-pc-900-solid-state-disk-not-as-fast.html](http://liliputing.com/2008/05/eee-pc-900-solid-state-disk-not-as-fast.html)
[http://www.jkkmobile.com/2008/05/asus-eee-pc-ssd-read-and-write-tests-4g.html](http://www.jkkmobile.com/2008/05/asus-eee-pc-ssd-read-and-write-tests-4g.html)

If this is the case then I recommend installing on the 4gb drive (4gb is plenty of space for Lubuntu) and using the 8gb for storage of documents and files.

Any way you slice it, this is not a fast computer... don't expect a miracle! :)

---

### Post by noxified on 2011-12-31
of course i don't expect miracles.but,having a cursor laggy,it's bugging. and playing youtube files,laggy...having more than one aplication up and running... it's not too much to ask,i think.i will install it on the 4gb chip and will come back with results. if there's any more opinions please post them,don't be shy. :D

---

### Post by snowpine on 2011-12-31
> **noxified said:**
> and playing youtube files,laggy...

Your computer does not meet the minimum hardware requirements for Adobe Flash Player according to:

[http://www.adobe.com/products/flashplayer/tech-specs.html](http://www.adobe.com/products/flashplayer/tech-specs.html)

I recommend using a flash downloader or browser media plugin if you want to watch Youtube videos.

---

### Post by noxified on 2011-12-31
ok,about flash player,i will use that.what other settings? i installed it on 4gb chip,and now i'm installing updates.

---

### Post by snowpine on 2011-12-31
Is it running faster off the 4gb drive?

---

### Post by noxified on 2011-12-31
there are some speed improvements,but i will test it tomorrow,and i will come back with a response.

---

### Post by Sobooban on 2012-07-12
guess that helped sins its been half a year
will try it on my 900 but i switched the disk for an 30gb hdd zif disk with converter, hope lubuntu 12.04 understand asus strange "battery life" gauge.

---

### Post by noxified on 2012-07-12
yes.the 4 gb inside memory did the trick.works better now :popcorn:

---

### Post by OldAdamUser2 on 2012-08-11
I recently installed Ubuntu 11.10 to an 8 GB SDHC card on my Eee 900. After a number of tweaks, it is now running beautifully. In particular, Youtube videos and Amazon Prime videos run perfectly in full screen mode. Suspend and resume work in a matter of seconds. The touchpad functions as expected. All basic software runs well. The system is a bit slow to boot from a complete shutdown, but that is the only drawback I can see, and it is a very minor one.

I wrote a detailed blog about how I installed and tweaked Ubuntu on my blog at --

[http://lakenorforkadventures.blogspot.com/](http://lakenorforkadventures.blogspot.com/)

---

