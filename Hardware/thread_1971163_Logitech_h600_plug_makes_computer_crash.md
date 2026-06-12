---
title: "Logitech h600 plug makes computer crash"
date: 2012-05-02
forum: Hardware
---

### Post by ilesumalt on 2012-05-02
Hello ,


I am completely new to linux , actually i've been using it for   something like two hours now so don't  be mad at my ignorance. 

I have a logitech h600 wireless headset  that i'm trying to  make work under ubuntu 12.04.

the problem is   a few seconds after i plug the  wireless usb adaptor  my computer just  turns off and ubuntu won't start again unless i unplug  the adapter.

What can i do  about this issue? 

Thank you  for your attention, any help  would be great.

---

### Post by mijette on 2012-05-05
Hi,

just tried my new H600 headset with ubuntu 12.04 and got a similar problem. When I start my computer with the USB adapter plugged in ubuntu starts without graphical user interface (tty1).
When I unplug the USB adapter and start ubuntu it works fine. But as soon as I plug the adapter in the system crashes and I only see command lines. 
Help would be very much appreciated and please let me know what kind of detailed information you need.

rgds

---

### Post by Mfodhu on 2012-05-21
I'm just signalling that I have exactly the same problem H600 headset makes xorg crash - and it cannot restart while the H600 headset is still plugged in, but it can start once you unplug the headset adapter.

---

### Post by uylug on 2012-06-02
Damnit! I was just about to buy one of these and decided to check for compatibility issues.

It definitely needs to run on Ubuntu since it's the OS that I use.

---

### Post by MikePaNtZ on 2012-06-08
I have this same exact issue. I had no problems with these headphones in earlier versions of Ubuntu. After doing some research on this issue I was able to read that someone claims it is a known issue. Here's the link with the info that I'm referring to:

[http://askubuntu.com/questions/144290/crash-after-plugging-in-the-logitech-h600-wireless-transmitter](http://askubuntu.com/questions/144290/crash-after-plugging-in-the-logitech-h600-wireless-transmitter)

Can anyone here confirm/deny this? If it is a known issue, is there a submitted bug report I can look at? I'd like to follow the issue as I will be sticking with Ubuntu 12.04 and I'd like to know if it gets fixed.

Thanks to anyone that can help!

---

### Post by BeenLikeFlynn on 2012-06-08
Check for drivers. Otherwise, keep trying to make the H600 compatable.

---

### Post by JBudOne on 2012-06-28
**Fix**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/973297](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/973297)

**Solution**
Ubuntu Software Centre -> Edit -> Software Sources -> Updates -> [X] (precise-proposed)

```

sudo apt-get update
sudo apt-get dist-upgrade
sudo restart

```

---

