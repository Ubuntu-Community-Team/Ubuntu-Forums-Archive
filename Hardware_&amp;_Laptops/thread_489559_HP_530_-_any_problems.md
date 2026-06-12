---
title: "HP 530 - any problems?"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by belda on 2007-07-01
Hi, anyone running ubuntu on **HP 530** notebook?
I'm deciding which notebook to buy and HP 530 meets my needs (low cost, dual core processor, GMA 950 grapaphics) and hope it will meet the most important **running Ubuntu on it**.
What I am asking is if there are problems with wifi, cause wireless cards are usually problem.?
**Is the wireless on hp 530 running ok under linux?**

---

### Post by belda on 2007-07-02
So I just bought this machine.

[INDENT]HP 530 - GH640AT#ABA
Core Duo Processor T2050 (1.6 GHz@533MHz FSB)
Chipset - Mobile Intel 945GM Express
Graphics - Intel GMA 950
Audio - Conexant CX20549
Ethernet - Intel 82562GT
Modem CX20548-11
WiFi - Intel PRO/Wireless 3945ABG 802.11[/INDENT]

**Ubuntu 7.04 Feisty Fawn**

[LIST]
[*]boot ok
[*]installation ok
[*]reboot
[/LIST]
**Video**
[LIST]
[*]no accel problems, just needed to install **915resolution** package to be able to have resolution 1280*800
[/LIST]
**Sound**
[LIST]
[*]works just fine
[/LIST]

---

### Post by belda on 2007-07-03
**WIRELESS**
[LIST]
[*]it finds few networks, but is not connecting to any of them
[*]it uses restricted driver which I unloaded and loaded again and yup, it works
[*]no security, wpa, wep, wep2 all works
[*]there is just problem, that it takes pretty long to load the applet and same long to connect, but once connecte4d works well
[/LIST]
**EyeCandy**
[LIST]
[*]it is 21st century, there are things, I cannot live without. on desktop I have beryl, but developers promised integration of compiz with beryl named compiz-fusion. Look [here]("http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml")
[/LIST]

---

### Post by bogdan.veringioiu on 2007-07-10
Hi.
I have the same laptop here.
What do you mean by loading/unloading the restricted driver?
Thanks.

---

### Post by rror on 2007-07-31
if the front microphone jack isn't working (for skype e.g.), follow this howto:
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
you don't have to specify parameters manually, so you can skip 'Manually Specify Module Parameters' completely

if you are wondering why the internal speaker doesn't mute when you connect headphones: HP phone support told me that muting of the internal speaker isn't possible

---

### Post by Arthur Archnix on 2007-08-08
Also check out this thread, [HP 530 Support]("http://ubuntuforums.org/showthread.php?t=502833&highlight=hp+530").

Best,

---

### Post by Shuntu on 2007-09-10
I recently Got my new HP530, all seems to work well exept the fact that I connot play anything in Mpayer (video clips etc). the splash screen opens, it wants to start & immediately terminates without any warning. I have intalled the Intel 945 driver via synaptic manager., but still have the same fault. what else can I try.

---

### Post by htoerrin on 2007-09-16
The problem is that the XVideo output, that is used by default, does not work. This applies to mplayer as well, but you can override the output by using mplayer -vo x11 <video file>

You can disable XVideo by appending  the following line line in the video driver section of xorg.conf:

Option "XVideo" "false"

By disabling XVideo, the system will use another method by default, and video playback should work.

---

### Post by King Lacho on 2007-09-21
Hello everyone, I bought my HP 530 notebook a few months ago, and I've tried to install Ubuntu on it. Even though it has worked really well, even with the 915resolution app, I just haven't been able to connect via my wireless card. I've already tried installing bcm43xx-fwcutter and also ndiswrapper, but that just doesn't seem to work. What could I do?

BTW, I've tried both applications separately as well as at the same time, but it just doesn't work. Please help!!!

---

### Post by Arthur Archnix on 2007-09-21
Well, a few people now have mentioned using the 915 resolution hack. There is likely no  need for this, and its just that, a hack. Why not just install the proper driver rather than hacking another to make it work?

```
sudo apt-get install xserver-xorg-video-intel
```

As for the immediate question, post your wireless card info. You'll find it in here..

```
sudo lspci
```

---

### Post by King Lacho on 2007-09-24
thanks, but does anybody know how i could solve my trouble with the wireless please? because I really do not want to go back to windoze but i'm really getting tired of always having to carry a wire with me

---

### Post by Arthur Archnix on 2007-09-26
Post the output of this:
```
lspci
```
If you want, just copy the part about your wireless card.

---

### Post by rror on 2007-10-16
> **King Lacho said:**
> thanks, but does anybody know how i could solve my trouble with the wireless please? because I really do not want to go back to windoze but i'm really getting tired of always having to carry a wire with me

using the network-manager applet is a little weird: select network from the list, type in password. you are now connected to the network but you do not have an ip adress, gateway or dns server. so open the shell and type
```
sudo dhclient
```
and it should work.
You will still be asked for the password of the network (just ignore) and will see the two grey balls and swirl of the applet...

nicer: use the 'normal' network configuration thingie, deactivate roaming mode select network, enter password and enter ip adress, subnet mask, gateway and dns server manually -> automatically connected after boot.

---

### Post by hcolyn on 2007-11-25
> **King Lacho said:**
> Hello everyone, I bought my HP 530 notebook a few months ago, and I've tried to install Ubuntu on it. Even though it has worked really well, even with the 915resolution app, I just haven't been able to connect via my wireless card. I've already tried installing bcm43xx-fwcutter and also ndiswrapper, but that just doesn't seem to work. What could I do?

BTW, I've tried both applications separately as well as at the same time, but it just doesn't work. Please help!!!

sorry for digging up an old thread, but have you had any luck yet?
i am in the process of trying to get it to work, and some tips would be appreciated ;)

---

### Post by nooby on 2008-05-17
I want to buy this machine and feel bad about it ahving trouble with wifi. 

I found this on the net 
[http://www.linlap.com/wiki/HP-Compaq+530](http://www.linlap.com/wiki/HP-Compaq+530)

maybe that one helps? 

Could anyone confirm. I don't dare to buy it if it 
has so much work to be done on it for it to work.

---

