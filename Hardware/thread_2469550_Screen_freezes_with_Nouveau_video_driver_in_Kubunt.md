---
title: "Screen freezes with Nouveau video driver in Kubuntu 21.10"
date: 2021-12-02
forum: Hardware
---

### Post by hstoellinger on 2021-12-02
Hello,
Having installed Kubuntu 21.10 lately (from an USB-stick - since a DVD did not work!) I now have problems with recurring freezes of my laptop screen. This happens in particular with browsers (eg. with Vivaldi, but also with Firefox, MS-Edge, Brave or Chrome - all of those at the most recent level). I wonder what might be the reason.
The laptop is an Sony VGN-AW11M_H, graphics card: NVIDIA G98M [GeForce 9300M GS], using the distro-supplied Nouveau driver.
I have tried all possible compositors - they all "freeze". From time to time the screen "recovers" again after 1 minute or two, but this is unusable! Seems to be a kernel (5.13) problem.
I also use Kubuntu 20.10. In this case the driver is the proprietary Nvidia 340-108, which comes from a patched version of a ppa. Everything worked o.k. under Kubuntu 21.04. I don't remember the kernel version off-hand, but was "lower" than 5.13...
Any hints?
Regards
H. Stoellinger

---

### Post by vmpx on 2021-12-02
Try this:
```
Replace in GRUB menu ”quiet splash” with ”quiet splash nomodeset” (On the grub screen click select ‘*Ubuntu’ and press ‘e’)
```

---

### Post by hstoellinger on 2021-12-03
> **vmpx said:**
> Try this:
```
Replace in GRUB menu &#8221;quiet splash&#8221; with &#8221;quiet splash nomodeset&#8221; (On the grub screen click select &#8216;*Ubuntu&#8217; and press &#8216;e&#8217;)
```
I tried your suggestion. However, the result was that my screen resolution decreased from the used 1680x945 to something like 860x... . This obviously happened 
at boot time.
By the way:
Who actually produces the Nouveau graphics driver? Maybe one can contact them directly and tell them about the problems with their driver and old graphics cards like mine...
After all - one of the "selling-points" Linuxers brag about is that old hardware keeps being supported longer...

---

### Post by hstoellinger on 2021-12-06
I now installed kernel 5.15.6, hoping that it might solve my problem. It did NOT, at least not completely! 
Now the behavior is such that most applications work flawlessly (at least so it seems for the time I have been testing it!). 
With browsers it is still the same situation: Things work o.k. for a while, then the system "stalls" for a couple of minutes. 
In the end it recovers, and the "game" starts again. Syslog (dmesg or syslog) don't show any hints. 
In the end I also upgraded KDE to Plasma 5.23, but this doesn't change anything with respect to screen freezes, etc...
Thanks for any hints
H. Stoellinger

---

### Post by #&amp;thj^% on 2021-12-06
> **hstoellinger said:**
> 
By the way:
Who actually produces the Nouveau graphics driver?.

It's open-source (many contribute to the code ), Nvidia(Propritary) is not a lot of help in aiding with " Nouveau "(open-source)
BTW>>> Kubuntu 21.10 is a point release have you tried with 20.04 LTS?

---

### Post by hstoellinger on 2021-12-07
No, I haven't tried 20.04. I am now leaning towards using 20.10 until the appearance of 22.04 next spring, and then install that version on a new laptop. Thanks for your remarks!

---

