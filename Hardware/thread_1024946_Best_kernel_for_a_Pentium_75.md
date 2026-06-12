---
title: "Best kernel for a Pentium 75?"
date: 2008-12-29
forum: Hardware
---

### Post by linuxisevolution on 2008-12-29
I have an old Pentium 75mhz laptop and have gotten wclp Linux to install. The 2.4.27-3-386 kernel gives panics, so what is the best, or oldest kernel that will work with Debian Sarge? It has 16mb of ram, which shouldn't  be a problem because I've gotten it to boot before. Thanks.

---

### Post by albinootje on 2008-12-29
> **linuxisevolution said:**
> I have an old Pentium 75mhz laptop and have gotten wclp Linux to install. 

There's also Debian potato and woody to be tried (potato is older than woody) :
[http://mirror.klabs.be/debian-cd/](http://mirror.klabs.be/debian-cd/)

---

### Post by linuxisevolution on 2008-12-29
Well , even Freedos won't install on this thing, so I would like to get another kernel if I can. What kernel does potato use? hehe, high in protien.

---

### Post by Kobalt on 2008-12-29
Potato shiped with kernel 2.2.19 by the time of its release I think..

---

### Post by linuxisevolution on 2008-12-29
Where do I download this kernel image? I would need the dependencies too, since the laptop does not have an internet connection.

---

### Post by albinootje on 2008-12-29
> **linuxisevolution said:**
> Where do I download this kernel image? I would need the dependencies too, since the laptop does not have an internet connection.

Get the Debian potato iso image, I've looked up a download mirror for you.
Install it on your other machine, and put the hard disk in the laptop again after installation.

I remember reading howtos about installing with 4 or 8 Mb or RAM years ago, in the time that Slackware, Debian and RedHat were the only well-known Linux distributions.

That's why I recommended something like Slackware 3.0

Some months ago I gave away my ancient InfoMagic cdroms with several of those mentioned Linux distributions on it.

Perhaps you should be lucky having 16 Mb of RAM :)

GL!

---

### Post by linuxisevolution on 2008-12-30
Well debian potato installed just fine, and works just fine+ it's pretty snappy, but I can't get a gui installed.  I would like to have some wm that is light as possible and easy to setup, like openbox. Could you direct me how to setup dhcp or install openbox and an X server without internet? Thanks!

---

### Post by albinootje on 2008-12-30
> **linuxisevolution said:**
> Well debian potato installed just fine, and works just fine+ it's pretty snappy, 

Cool! :)
> 
but I can't get a gui installed.  I would like to have some wm that is light as possible and easy to setup, like openbox. Could you direct me how to setup dhcp or install openbox and an X server without internet? Thanks!

For the dhcp part, you can edit /etc/network/interfaces and Debian Potato probably came already with dhclient included. 
Otherwise there's perhaps the pump command for it.

I don't remember, at that time I found Debian annoying because I didn't know how to skip that horrendous dselect (...shiver). :| :)

---

### Post by linuxisevolution on 2008-12-30
What is dselect? BTW, it tells me I have no eth0 ( device not found ). ARGE!

---

### Post by albinootje on 2008-12-30
> **linuxisevolution said:**
> What is dselect? BTW, it tells me I have no eth0 ( device not found ). ARGE!

You probably have to load the right kernel module for your NIC, the ancient Debian didn't have that good hardware detection. (Later Progeny Linux used discover, and RedHat came with kudzu for hardware detection).

---

### Post by linuxisevolution on 2008-12-30
I just got angry at Potato. I might take my anger out on it by making smashed potatos later lol.... man -k doesn't even exist! No wonder lots of people didn't use Linux a while ago... I am going to use my Debian Etch xfce disk to install a base system and then install the nessesities later. Then I will install the potato kernel if needed. Would this work? Can I just download the potato.deb kernel and that's that? ( i have the download location if you want it ). Would this work?

---

### Post by albinootje on 2008-12-30
> **linuxisevolution said:**
> I just got angry at Potato. I might take my anger out on it by making smashed potatos later lol.... man -k doesn't even exist! No wonder lots of people didn't use Linux a while ago... I am going to use my Debian Etch xfce disk to install a base system and then install the nessesities later. Then I will install the potato kernel if needed. Would this work? Can I just download the potato.deb kernel and that's that? ( i have the download location if you want it ). Would this work?

Sarge with the Potato kernel ? I think that's not gonna work, but of course you can try.
What I don't understand however, is.. why don't you put the laptop hard disk in the other machine, use the internet there to install more software like dhclient or pump.

If your NIC on that other machine is too new, and Potato doesn't have a kernel module for that, you can use the "chroot" command.

But then you would need either :
1) an IDE 2.5" usb-casing to have your laptop disk in temporarily
2) an normal IDE to laptop IDE interface converter, I have such a 
   converter, I bought two of them in Asia for about 4 euros, but I think
   it's not so easy to find them in normal shops.

In either case you would use another machine with Linux installed, attach the laptop disk, mount the / partition of the laptop disk to e.g. /mnt
Then use "chroot /mnt" as root (sudo in Ubuntu, or root in another Linux distribution).
Then make sure the Potato install has a proper /etc/resolv.conf (no need for /etc/network/interfaces at this point), and then you should have internet inside that temporarily chrooted Potato installation, which should enable you to install more software.
Not sure whether apt-get existed at that time, it's more likely that you need to use the [....] dselect to install software.

And if you're really interested, I gave my ancient InfoMagic cdroms to a friend of mine (who was happy with it), I can ask for a copy of an old Slackware installation if you want.

---

### Post by linuxisevolution on 2008-12-31
No, I have plenty of cd-roms burt lol. ( around 40 by now ). Attaching the laptop's harddrive to my pc is the only way I can install. I have the results on another thread, which is here:

[http://ubuntuforums.org/showthread.php?p=6470737&posted=1#post6470737](http://ubuntuforums.org/showthread.php?p=6470737&posted=1#post6470737)


Thanks for everyone's help! Happy new year! I won't miss 08 hehe.

---

