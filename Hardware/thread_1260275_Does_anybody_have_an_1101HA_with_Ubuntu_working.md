---
title: "Does anybody have an 1101HA with Ubuntu working?"
date: 2009-09-07
forum: Hardware
---

### Post by Adavur on 2009-09-07
Hi everybody.

I know there are several posts out there about this pc and others alike, but I never see if people really got those problems solved...

So now I am asking: Has anybody got an Asus Eee Pc 1101HA (the one with 11,6" screen and Z520 CPU) with Ubuntu working on it.
I mean:

[LIST]
[*]Using wireless and wired network with no problems
[*]Using the 1366x1024 screen resolution WITH compiz/desktop effects working (I know it's not a fast PC, but some of the effects should work)
[/LIST]

Please write if you succeeded, if you have had any other problems and how you did solve them (link to guide etc.)

Thank you very much :)

/Mathias

---

### Post by asedas on 2009-09-12
Hi,

 I have 1101ha with xubuntu 9.04. everything working but not out of the box. First of all you'll have to compile the ethernet module fro lan card. after that you can add package with backports drivers for wifi. after that the only thing is the graphic driver. intel gma500 is a ****, but you can get even the compiz effects ;) of course, this is on very low details and without speed. I use cpu politic set to "performance" all the time - that's mean use the all power to cpu: 1,33. it's necessary to use eee 1101ha normal. even with all power set up to max this "computer" is a little bit slow and "muddy" during the work.
you will have to gewmt use to it but that's the price of mobility :) [4-5h with std battery still with cpu @ 1.33 - i can't wait for extended batteries!!!].

so... almost everything is here: [http://forum.ubuntuusers.de/topic/ubuntu-auf-dem-eee-1101-ha/2/](http://forum.ubuntuusers.de/topic/ubuntu-auf-dem-eee-1101-ha/2/) and you can read more on this forum. to get the compiz working you need to edit compiz in /usr/bin - can find on this forum.

I got used to this and have everything working. I reported that sometime my wlan is disconnecting after long thime connected with one network, and I have to restart it [turn the wifi down and turn on]. it will be fixed propably in next kernel update [but it's a minor issue].

greetings from poland ;)

---

### Post by rob-ward on 2009-09-12
If you are looking at getting a portable netbook as well considering the 1101ha you may want to look at the 1005ha. I looked at both and after having a play with both bought a 1005ha, it has better battery and the processor keeps up better than that of the 1101. Unless you despritly need the higher res screen I would suggest the 1005ha. However both are nice laptops and I know that you can get the 1101 working if you decided on that.

---

### Post by Spock112 on 2009-09-16
Hi,
I run the 1101HA with UNR 9.04.
Most things work just fine. But some of my Hotkeys don't work or do something else.
Does anyone else have this problem?

---

### Post by asedas on 2009-10-02
yes, some hotkeys doesn't work [eg. brightness keys, touchpad, etc]. it's "normal" [hope new kernel will fix it in future].

---

### Post by Adavur on 2009-10-06
I'm very happy to know that somebody made it.

I got LAN and WLAN working, but every time I try to figure out the screen it gives me an error message.

Does anybody have a link to a guide to get the right screen resolution and compiz? I have read the GMA 500 thread in this forum, but I can't find anything for this specific computer.

Thanks from a Danish newbie ;)

---

### Post by khessels on 2009-11-24
this may solve some problems...
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by Scottworld on 2009-12-10
> **asedas said:**
> Hi,

 I have 1101ha with xubuntu 9.04. everything working but not out of the box. First of all you'll have to compile the ethernet module fro lan card. after that you can add package with backports drivers for wifi. after that the only thing is the graphic driver. intel gma500 is a ****, but you can get even the compiz effects ;) of course, this is on very low details and without speed. I use cpu politic set to "performance" all the time - that's mean use the all power to cpu: 1,33. it's necessary to use eee 1101ha normal. even with all power set up to max this "computer" is a little bit slow and "muddy" during the work.
you will have to gewmt use to it but that's the price of mobility :) [4-5h with std battery still with cpu @ 1.33 - i can't wait for extended batteries!!!].

so... almost everything is here: [http://forum.ubuntuusers.de/topic/ubuntu-auf-dem-eee-1101-ha/2/](http://forum.ubuntuusers.de/topic/ubuntu-auf-dem-eee-1101-ha/2/) and you can read more on this forum. to get the compiz working you need to edit compiz in /usr/bin - can find on this forum.

I got used to this and have everything working. I reported that sometime my wlan is disconnecting after long thime connected with one network, and I have to restart it [turn the wifi down and turn on]. it will be fixed propably in next kernel update [but it's a minor issue].

greetings from poland ;)


So did you manage to get the internal Mic to work ?

---

### Post by scicode on 2010-05-20
typing here on a 1101ha on lucid (10.04) UNE with working wlan and nice screen res

fn keys, multituch and eee-control are still not working but I guess this is all just a matter of time

---

### Post by gsedej on 2011-02-22
Hi!

I have sucessfully enabled 3D drivers and Compiz. Performance is not really great but I don't know if hardware is actually fast.

In this thread you can find guide:
[http://ubuntuforums.org/showthread.php?t=1229345]("http://ubuntuforums.org/showthread.php?t=1229345")

---

### Post by rigiantking on 2011-04-14
getting compiz to work on 10.10 is actually very easy now
takes about 2 minutes to get it up and running by doing the following steps:
1. sudo add-apt-repository ppa:gma500/ppa && sudo apt-get update
2. sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d poulsbo-config
3. reboot and see it working :)

very easy and works perfectly. but do not even try to upgrade to latest version of 11.04, absolutely no support for unity what so ever and trying to get gnome3 working will also result in failure. tried it yesterday. but on 10.10 it works just fine :)

---

