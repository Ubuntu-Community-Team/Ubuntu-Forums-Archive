---
title: "First time user on an HP nc8000"
date: 2011-06-20
forum: Hardware
---

### Post by PIDGINZ on 2011-06-20
Hello all :)

A while ago I decided I was sick of this old laptop just sitting around wasting space and collecting dust. So I put ubuntu 10.10 on it :D   The install went fine and everything worked straight after the install except for the wireless, which I will discuss later. BUT the laptop hung randomly, as in no response to keyboard, touchpad, or the numlock key. I was told this should not happen on linux, so I put it down to the laptop's hardware doing something it shouldn't. 

After 2 days of use, though, I was sick of these hangs and then remembered that my dad downloaded 10.04 the other day, so I reformatted and put that on instead.  This time there were no lockups, but the wireless still would not work. The driver loaded fine but it would not connect to my home network, it kept telling me bad password. After 2 days of googling, trying to use wicd, and avoiding ndiswrapper like moss on a sandwich, I figured out how to get madwifi-ng installed and running, which fixed the wireless just fine. The only issue I had with it was resuming from the suspend state, it would keep asking me for the wireless password even though I was sure it was correct. That I fixed with a little script that I have forgotten about already - it just unloaded and then loaded ath_pci when it resumed from suspend.  

I also read about recompiling the linux kernel with specific optimizations for the Pentium M processor that this laptop has, and decided I wanted to take a shot at that. I followed [this]("http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html") guide, and first used make localmodconfig and then make menuconfig to hopefully find stuff that I didn't need that I could take out and to select optimizations etc. Long story short it worked first time, but that first time I did it I didn't include sound drivers, the second time I didn't include usb mass storage drivers, and now today I realised I left out iso9660 support (or something like that, in other words CDs don't mount), so I recompiled again this evening. I'm quite proud to say that I haven't been using linux for a month yet and I've already compiled my own kernel 3 times :D  

This brings me to the main point of this thread: this evening when I recompiled I made sure iso9660 was included in the kernel config, but whenever I insert a cd into my drive I get this: 
```
Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only mount: wrong fs type, bad option, bad superblock on /dev/sr0,        missing codepage or helper program, or other error        In some cases useful info is found in syslog - try        dmesg | tail  or so 
```I don't know what to do now.  

The second thing that brings me here is that battery life is rather abysmal on this laptop, granted I don't use the main battery because it's dead and the secondary travel battery that I do use is several years old, but I'm quite sure windows XP lasted longer than ubuntu does. I get more or less 2 hours on the battery while doing nothing with it - just letting it sit there. My CPU governor is set to ondemand and it does scale down from the normal 1.7GHz to 600MHz just fine. I have disabled bluetooth on startup and can enable it as I wish, so it doesn't use power. I've removed lots of applications that I won't need. I have laptop-mode-tools installed, too, but I haven't seen any improvement with that. It's quite funny though, ubuntu tells me I have more or less an hour of life remaining at full charge, but when the reported charge is 0% I can still use the laptop for a good hour depending on what I do.

Another issue that I have, well it's less of an issue and more of annoyance, but whenever I boot I get a black screen with a blinking "_" cursor at the top left corner of my screen for about 15 seconds (after which it comes up with the ubuntu loading screen and then the login box), and the entire time the hard drive indicator is solidly lit. According to another forum where I posted my boot.log after booting up something is happening on /dev/sda5 for those 15 seconds, and sda5 is the swap partition that got put there when I installed ubuntu, but they then redirected me here as apparently you guys might have more knowledge on this.  I also seem to have a bit of an issue with gnome-system-monitor. On the processes tab it eats a steady 20% CPU, and on the resources tab it takes 40-50% CPU, and that's with the interval set to 5 seconds. I did some googling and I found a bugreport on it, and I'm wondering if any conclusion has been made about it or if there is anything I can do to avoid getting my CPU munched. Rythmbox also seems to like using up a good 5-7% CPU which seems a little high for such a small media player, and I'm only playing MP3s. pulse-audio also takes up about 10% at the same time as rythmbox.

The last thing I came here for is to ask whether it's possible to use fglrx for the radeon 9600 in this laptop with ubuntu 10.04. I did sudo apt-get install fglrx and that installed fine but it told me no compatible hardware was detected, and then I found that the last release to support the 9600 was catalyst 9.4 or 8.4 or something like that. I also heard that that release doesn't support the version of X.org that 10.04 uses, is this correct? Or is there a way of getting that driver on here?  Otherwise I am seriously enjoying ubuntu, I love having the freedom of looking through all the free software I can download and I love how I can do pretty much whatever I want on here. It's also given me an excuse to stay up at night talking to people on pidgin :D

OH! I didn't mention specs: 1.7GHz Pentium M, 1GB ram, radeon 9600 (I think 64mb), and the wireless card is a atheros 5000 series chip (can't remember the exact model).

---

### Post by PIDGINZ on 2011-06-21
Bump.

If this is a case of TL;DR, then:

[LIST]
[*]I'm loving ubuntu
[*]CDs won't mount
[*]ath5k kept asking me for my wireless password, madwifi fixed it
[*]Battery life kinda sucks
[*]On boot there is a 15 second long black screen with a blinking cursor at the top left corner of the screen
[*]Gnome system monitor uses ~40% CPU depending on the tab I'm viewing.
[/LIST]
I did some reading up on fglrx, and I see that I can't use it with my 9600 because the last version that supports the 9600 isn't compatible with the current kernel. So nevermind that part.

---

### Post by jerrrys on 2011-06-21
#1, 5 and 6 are normal reactions :)

---

### Post by PIDGINZ on 2011-06-21
> **jerrrys said:**
> #1, 5 and 6 are normal reactions :)

So even the 15 second wait is normal? In my VM on my windows 7 desktop it doesn't take nearly as long. Granted that is a far more powerful machine, but still.

So then the last thing I really need to fix is CDs not working, maybe I'll just download the latest kernel source and compile a generic one then localmodconfig with a CD in along with all the other stuff too, then go back in and take stuff out.

---

### Post by dFlyer on 2011-06-21
If it's an old computer, you might want to test the hd for bad sectors using disk utilities. This is just a shot in the dark.

---

### Post by PIDGINZ on 2011-06-22
It is old but the hard drive was replaced about 2 years ago. I've checked it and it is fine.

---

