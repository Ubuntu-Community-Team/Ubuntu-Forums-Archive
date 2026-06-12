---
title: "Leaving Ubuntu for now."
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by dannyp on 2005-04-10
Hello,

I first must start out by saying, Ubuntu Linux is by far the best Linux Distro I have ver used, and believe me I have used them all. However I am forced to leave Ubuntu and go back to my old distro which was Mephis. I was unable, with all the help in these forums and google combined to get my Linksys WPC54G ver2 PCMCIA card to work. I had no power light, I tried all the drivers, I tried the ndiswrapper, I have been through everything and no luck. I will keep my out for when this card is supported and definitely return. Thanks to all who tried to help.

---

### Post by arctic on 2005-04-10
[QUOTE=dannyp]Hello,

I first must start out by saying, Ubuntu Linux is by far the best Linux Distro I have ver used, and believe me I have used them all. [/quote] all 396? wow... you are brave :D
>  However I am forced to leave Ubuntu and go back to my old distro which was Mephis. I was unable, with all the help in these forums and google combined to get my Linksys WPC54G ver2 PCMCIA card to work. I had no power light, I tried all the drivers, I tried the ndiswrapper, I have been through everything and no luck. I will keep my out for when this card is supported and definitely return. Thanks to all who tried to help.
mepis is a fine distro. so good luck. and maybe we will see you back with ubuntu in six months? ;)

---

### Post by poofyhairguy on 2005-04-10
[QUOTE=dannyp]Hello,

I first must start out by saying, Ubuntu Linux is by far the best Linux Distro I have ver used, and believe me I have used them all. However I am forced to leave Ubuntu and go back to my old distro which was Mephis. I was unable, with all the help in these forums and google combined to get my Linksys WPC54G ver2 PCMCIA card to work. I had no power light, I tried all the drivers, I tried the ndiswrapper, I have been through everything and no luck. I will keep my out for when this card is supported and definitely return. Thanks to all who tried to help.[/QUOTE]


Well thanks for the shot. I don't blame you for Mepis, its nice.

---

### Post by hohllp on 2005-04-10
have you tried this:

[http://tiefighter.et.tudelft.nl/~arthur/wpc54g/](http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)

also I had a similar problem (no status lights) and found that the radiostate flag was set wrong. I almost gave up too, but now that my wireless works, ubuntu rocks. I have been a debian fan for a while and this distro is the best of both worlds... easy to use and powerful.

Vince

---

### Post by az on 2005-04-10
Maybe this.

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8575](https://bugzilla.ubuntu.com/show_bug.cgi?id=8575)

Have you tried it with the warty kernel?

---

### Post by dannyp on 2005-04-11
Actually. that is one thing I did not try, I will give it a shot cause I love this distro.  Thanks azz.

---

### Post by joplass on 2005-04-13
[QUOTE=hohllp]have you tried this:

[http://tiefighter.et.tudelft.nl/~arthur/wpc54g/](http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)

also I had a similar problem (no status lights) and found that the radiostate flag was set wrong. I almost gave up too, but now that my wireless works, ubuntu rocks. I have been a debian fan for a while and this distro is the best of both worlds... easy to use and powerful.

Vince[/QUOTE]

Do you mind giving me a hand with mine?  I have everything looking good but I don't get the signal maybe my radiostate flag is set wrong too.  By the way I don't even know what "radiostate flag" means.  My power light is on and the card appears under networking but no signal.
Help please!

---

### Post by blu.gecko on 2005-04-14
I too had the same problem that you were having, no power light on the WI-FI,
and I am using the preview version, but I found that I had to "sudo modprobe ndiswrapper" then go to "administrator" - "network" - "wireless adapter" then activate" reboot system, then konsole and sudo ndiswrapper -m, then reboot, now I have a light and my laptop has a power button on the front, my wifi will not power up  unless I push that button.

Good Luck To You Bro.. I felt the same way I almost went back to XP....... \\:D/

---

### Post by dannyp on 2005-05-04
I am happy to report that I finally got my WPC54G Version2 wireless PCMCIA card working. The whole time all I needed was the other driver  ](*,)  I had the lsbcmnds installed in ndiswrapper thinking that was all I needed. Not the case, I also needed the LSTINDS driver wich is for the hardware piece. This explains no lights on the crad. As soon as I installed this driver and loaded the ndiswrapper module, did a reboot and boom I was surfing wireless on Ubuntu. I glad to back using the best distro ever. Thanks again to all who have helped. :-P

---

