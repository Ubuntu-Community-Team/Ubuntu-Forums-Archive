---
title: "Probelms with VGA/HDMI out"
date: 2012-03-29
forum: Hardware
---

### Post by Idge on 2012-03-29
Hello, 
So i've been trying to solve this a few days now.
I'm running Ubuntu (XBMC) on my Dell XPS M1530 Laptop with a 8600 GT card.
I can't get an external monitor to work, I've tried the usual FN+F8 combination = Nothing. I've tried both HDMI and VGA out = Nothing.
 
Everything worked fine while running Windows XP / Windows Vista,
 
I've also tried running xrandr in terminal which produces a cannot open display message.
 
Anyone have any good suggestions? Is it possible to edit the xorg.conf to force a hdmi/vga output?

---

### Post by zeljkojagust on 2012-03-29
What drivers are you using? Nvidia official, or built in Ubuntu ones?

---

### Post by Idge on 2012-03-29
> **zeljkojagust said:**
> What drivers are you using? Nvidia official, or built in Ubuntu ones?
 
Here's the thing, I'm not used to using the terminal environment nor any linux distribution. At the beginning I just ran with whatever was installed with the Unbuntu/XBMC distro. Then I found a thread on the internet that involved something similiar to this:
 
sudo apt-get ppa://*********
sudo apt-get update
sudo apt-get nvidia-current
 
This seemed to have downloaded something that was approx 30MB of size and installed it. I then proceeded to restart my laptop, but there was no change.

What is the correct way of installing the Nvidia driver through terminal?

---

