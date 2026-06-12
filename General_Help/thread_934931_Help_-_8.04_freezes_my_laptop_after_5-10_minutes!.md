---
title: "Help - 8.04 freezes my laptop after 5-10 minutes!"
date: 2008-10-01
forum: General Help
---

### Post by Nazareth on 2008-10-01
Hi,

In some rage and frustration, I moved from Vista to Gutsy and all was well.

Unfortunately, ever since I upgraded to Hardy, my laptop seems to randomly freeze after 5-10 minutes of operation and I have to use a hard shutdown.

I have absolutely no idea what even causes it; it's not a new application or anything; it seems to happen like clockwork whether I'm browsing the Internet or my photos.

I really like Ubuntu and had no problems with 7.10, can anyone suggest a way of preventing my laptop from freezing?
I really don't want to go back to slow, buggy Vista but as it stands I have a fast, buggy Ubuntu!

I'm still very much a newbie, and all help would be gratefully received.

---

### Post by Peter09 on 2008-10-01
Might be your graphics card.

Can you post the output of

```
lshw -C display

```

---

### Post by Nazareth on 2008-10-01
Hi there, it's as below.

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: RC410 [Radeon Xpress 200M]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list
       configuration: latency=66 mingnt=8

---

### Post by Sycron on 2008-10-01
I had once this problem too. Try disabling the screensaver.

---

### Post by Nazareth on 2008-10-01
> **Sycron said:**
> I had once this problem too. Try disabling the screensaver.

Hi Sycron,

Unfortunately this was one of the first things I did, and it didn't help solve the problem... any further suggestions welcome!

---

### Post by Sycron on 2008-10-01
Can you watch you computer 5-10 mins and see exactly what happens ?

---

### Post by Nazareth on 2008-10-01
> **Sycron said:**
> Can you watch you computer 5-10 mins and see exactly what happens ?

Well, I start it up, and after 5-10 minutes it simply stops and doesn't respond.

mouse doesn't move, dynamic pointers freeze up, websites stop loading midway... basically a total freeze.

And for some bizarre reason now it's seizing up even faster - no more than 5 minutes after booting!

All help appreciated as I really hate having to return to Vista...

---

### Post by Peter09 on 2008-10-01
Not sure if it is anything to do with your problem but it might be worth getting envyng-core from the repositories and installing the ATI driver. It *should* give you better performance and *might* get over the display problem that you are having.

Once installed type 

```
envyng -t 
```

in a terminal and install the ATI driver.

---

### Post by Nazareth on 2008-10-01
> **Peter09 said:**
> Not sure if it is anything to do with your problem but it might be worth getting envyng-core from the repositories and installing the ATI driver. It *should* give you better performance and *might* get over the display problem that you are having.

Once installed type 

```
envyng -t 
```

in a terminal and install the ATI driver.

Hi Peter,

Thanks for the advice; I tried it but unfortunately, the laptop still crashes!

Any other ideas?

---

### Post by Peter09 on 2008-10-01
Ahh well - the best ideas of mice and men ---

Does it respond to <Ctrl><Alt><Backspace>

---

### Post by Nazareth on 2008-10-01
I'll give it a go next time it crashes.

Last time (2 mins ago, while watching YouTube), the sound looped for about half a second as well, so it can't be a pure graphics problem.

---

### Post by Nazareth on 2008-10-01
... And after yet another crash, I can confirm that ctrl+alt+backspace also doesn't work. It's a bona fide crash!

---

### Post by Peter09 on 2008-10-01
Does it crash if you just leave it alone, no applications running. Note that firefox + videos seem unstable at the moment.

---

### Post by AlexBellisBrown on 2008-10-01
Yep, give that a try, turn it on, but touch nothing... see if it crashes, after that, if it does, perhaps we should have a look at what starts running automatically when you boot up.

---

### Post by Nazareth on 2008-10-01
You guys are right - it was fine for over an hour; the moment I fired up Firefox, the whole thing crashed and burned...

What should I do?

---

### Post by llebegue on 2008-10-01
This seems related to that thread :

[http://ubuntuforums.org/showthread.php?t=765510&goto=newpost](http://ubuntuforums.org/showthread.php?t=765510&goto=newpost)

Befor you start jumping in to find a solution be advised that ther is non at this time (I watch this thread because my dad's computer keeps freezing)

---

### Post by iponeverything on 2008-10-01
> **Nazareth said:**
> You guys are right - it was fine for over an hour; the moment I fired up Firefox, the whole thing crashed and burned...

What should I do?

post the output of lspci just we can see if there is hardware that we know has issues.  also on the lockup, does the caps-lock blink?

---

### Post by Nazareth on 2008-10-01
Hi,

How do get lscpi to work? Very much a newbie I'm afraid...

---

### Post by iponeverything on 2008-10-02
just type "lspci" at the command line.

---

### Post by russo.mic on 2008-10-02
Try switching consoles when it crashes.  You could do this with ctrl + alt + F1.  then log in and issue this command :
sudo killall firefox 

This should end all instances of firefox.  from there, hit ctrl + alt + F7 to bring you back to your Gnome session.  see if that unlocks it!  

Also, I may suggest epihany as a good, lightweight browser that you can get flash to work in.  Good firefox alternitive.

Russo

---

### Post by Nazareth on 2008-10-02
> **iponeverything said:**
> just type "lspci" at the command line.

Et voila...

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

I had actually tried typing it before, but I think I mistyped :oops:

---

### Post by Nazareth on 2008-10-02
> **russo.mic said:**
> Try switching consoles when it crashes.  You could do this with ctrl + alt + F1.  then log in and issue this command :
sudo killall firefox 

This should end all instances of firefox.  from there, hit ctrl + alt + F7 to bring you back to your Gnome session.  see if that unlocks it!  

Also, I may suggest epihany as a good, lightweight browser that you can get flash to work in.  Good firefox alternitive.

Russo

Given that Ctrl+Alt+Backspace fails to work, I don't see how  Ctrl+Alt+F1 would (and indeed it doesn't - I tried!).

Epiphany also crashes, which seems to suggest it's somehow related to the way the system accesses the Internet... strange!

---

### Post by iponeverything on 2008-10-02
There are known issues with the RaLink RT2561/RT61 driver (rt61pci) that causes hard lockups on hardy 8.04.1 for some people.

Installing newer rt61pci module will fix it.

do:

sudo apt-get install linux-backports-modules-2.6.24-19-generic

and see if it solves your problem.

---

### Post by Sycron on 2008-10-02
Well I have to RaLink and I'm using it with no problems. That worked with Gutsy Gibbon, Hardy Heron and Intrepid Ibex.

---

### Post by iponeverything on 2008-10-02
> **Sycron said:**
> Well I have to RaLink and I'm using it with no problems. That worked with Gutsy Gibbon, Hardy Heron and Intrepid Ibex.

I am glad that it does not affect everyone. Is the rt61pci module that your using? It affects me and a few others -- check in launchpad for more info on the bug.

---

### Post by Nazareth on 2008-10-03
> **iponeverything said:**
> There are known issues with the RaLink RT2561/RT61 driver (rt61pci) that causes hard lockups on hardy 8.04.1 for some people.

Installing newer rt61pci module will fix it.

do:

sudo apt-get install linux-backports-modules-2.6.24-19-generic

and see if it solves your problem.

Wow, it certainly seems to have done the trick - thanks a ton! :D

---

### Post by Sycron on 2008-10-03
+1 people on these forums happy.

---

### Post by Nazareth on 2008-10-17
Hi guys,

I'm afraid I'm back... After yesterday's Ubuntu upgrades (including a new linux kernel), it looks like my laptop's back to crashing.

And unfortunately there don't seem to be any more recent drivers than 
linux-backports-modules-2.6.24-19-generic

Any idea what's going on and what else I can try? 

The unfortunate thing is that in Windows, updates just work. Even though it isn't free, from a user's perspective, the only way Ubuntu will break through is when it's just as simple to use.:(

---

### Post by Nazareth on 2008-10-17
Sorry guys, just realised the thread was marked as solved...

Basically, yesterday night there was a bunch of updates, I let them all download and execute, and shut down the computer. Upon starting it this morning, it resumed its freezing pattern... I tried updating the Ralink drivers as per last time and all it said was that there were no newer updates.

So my laptop keeps freezing as before - does anyone have any suggestions?

---

### Post by m1r0 on 2008-10-18
hello,

i have similar problems with freezing in last two days,

this card: 

05:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI

using:

8.04 - 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64

last thing i see on system log is somthing about wireless searching IPv6.

any tips to fix this ?

---

### Post by 2CV67 on 2008-10-19
> **m1r0 said:**
> hello,

i have similar problems with freezing in last two days,

this card: 

05:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI

If your freeze is the kernel-panic thing with flashing Caps Lock & Scroll Lock, you might also want to look at this parallel thread:
[http://ubuntuforums.org/showthread.php?t=832383](http://ubuntuforums.org/showthread.php?t=832383)

I have a RaLink RT2561/RT61 802.11g PCI card (Edimax EW-7128g) and had these freezes every few minutes after upgrading to Hardy.

As explained in post#108 in that thread, I updated rt61pci from version 2.0.10 to 2.1.4 via backports.
That fixed the problem 100% from 6 September till the next kernel update on 16 October.
That kernel update re-introduced the old rt61pci v 2.0.10 & my first freeze followed in only a few minutes.

Rather than re-open the backports, I have just gone back to the earlier kernel with v 2.1.4 for now.

I am not competent to suggest anybody should open backports, but I am SURE this fixed the freezing for me.

The method came from Bashar on the French Ubuntu Forum.

---

### Post by 2CV67 on 2008-10-20
This bug report covers how RT61 cards freeze in Hardy

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142)

Also describes the backports fix, but not in basic-enough language for me...

---

### Post by m1r0 on 2008-10-22
Card removed, working ok on usb wlan stick now without problems for few days.

3 lan cards not working - 2 removed out , one onobard. - REALTEK cards ?!
1 wlan card not working ,also removed out. Belkin !?

all this hardware as ussual worked perfectly on previous versions.

---

### Post by siva_s on 2008-10-22
**im also facing this problem**
i've installed ubuntu 8.04 two days back...on that day itself the computer started freezing like "print screen" image...(ctrl+alt+bspace not working)
so i decided to play a movie...but now also freezing with 'GRRR' sound..
my desktop pc has 512 RAM and having ATI graphics card with windows XP...i've updated the system upto the last minute..

pls help me guys to eliminate this problem...im new to linux..i really dont want to go XP again

---

