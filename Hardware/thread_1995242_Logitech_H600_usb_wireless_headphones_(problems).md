---
title: "Logitech H600 usb wireless headphones (problems)"
date: 2012-06-03
forum: Hardware
---

### Post by JBudOne on 2012-06-03
Hey guys! I just got my birthday present yesterday, a pair of H600 USB Wireless Headphones (obviously, judging from the title). I've got some serious problems though when trying to plug them into the laptop.

Firstly, another person has posted some issues with this exact same device here: [http://ubuntuforums.org/showthread.php?t=1912450](http://ubuntuforums.org/showthread.php?t=1912450)  However in his, he wasn't able to get the sound working. With mine, as soon as I plug in the USB, the screen goes all pinky/yellow/purple, then swaps over to pure Console mode and spits out a bunch of stuff. The stuff it spits out doesn't appear very descriptive or even in any way related to the headphones/usb (Apache restarting, sendmail restarting, checking the laptop battery, etc.)  It never gets out of console mode though, and trying Alt+F8 doesn't take me back to everything. I just have to send the shutdown signal to restart into the system. 

I really don't want to have to just toss these out, or put them up on the shelf where they'll never be touched again. There must be something that I can do to get this working, especially since some people in the that other thread clearly got it working for them. Any ideas? Hints tips? Is there any more information that I can provide in here? Thanks so much to anybody that can help me out here :)

---

### Post by JBudOne on 2012-06-03
If it helps, I'm using the latest stable version of Ubuntu -- 12.04 Precise

---

### Post by JBudOne on 2012-06-06
Bump.. 

Anybody have any hints or tips? I'd really like to do everything that I can to make this work. It must be possible, other people clearly got it to work. I don't know why its causing such intense problems for me, but I'm sure there must be a way to get around it and even get these working?

---

### Post by JBudOne on 2012-06-09
So I haven't quite given up on this yet. I've tried plugging the USB into my netbook with Wubuntu installed. Turns out it works just fine! It only plays out of the right earpiece, but that's good enough. Seems like the problem is directly in Ubuntu though. Is that because Wubuntu runs off of Windows, where the USB is supported?

I've also disabled auto-run scripts from removable devices, but still when I plug in the USB I get the same glitch as earlier (screen changing pink/yellow, then goes to console mode and won't go back). Also if I keep the USB plugged in and restart the computer, it skips the Ubuntu login screen entirely, and goes directly to console-mode login

---

### Post by JBudOne on 2012-06-28
Hello, me!

**Fix**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/973297](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/973297)

**Solution**
Ubuntu Software Centre -> Edit -> Software Sources -> Updates -> [X] (precise-proposed)

```

sudo apt-get update
sudo apt-get dist-upgrade
sudo restart

```


Enjoy, me!

---

### Post by 1976MrEMan on 2012-08-12
> **JBudOne said:**
> Hello, me!

**Fix**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/973297](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/973297)

**Solution**
Ubuntu Software Centre -> Edit -> Software Sources -> Updates -> [X] (precise-proposed)

```

sudo apt-get update
sudo apt-get dist-upgrade
sudo restart

```


Enjoy, me!

This is the closest i've gotten to making my H600 headphones work with 12.04, and I think it will happen, but one question? what are you typing in order to sudo restart? That is the only hiccup i've had.....

---

