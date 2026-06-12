---
title: "Can't set my 21.6&quot; screen resolution of 1680x1050 with Intel GM965/GL960 of my laptop"
date: 2008-11-08
forum: Hardware
---

### Post by xuncall on 2008-11-08
Hi everybody!

I am getting crazy... :( I have been almost for two weeks searching for solutions but not enough at the moment.

I have a Hanns.g hg216d screen, with 21.6" and optimal resolution of 1680x1050, tested ok in Windows with this screen and my graphic card, Intel GM965/GL960 of my MSI PR300 laptop. I have connected both by VGA now in ubuntu 8.10, and i have the problema because maximun resolution that i get is 1360x768.

I am trying to follow this guide ([https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)) to configure my xorg for 1680x1050 but i can't... To do it i think that i have to configure xrandr by a modeline but i don't know how to do it. Then, i have to configure my xorg and as well, i don't know how to do it. Even, i don't know what drivers am i using now (i have intel drivers installed but i don't know if i am using them).

Here are my xrandr: [http://paste.ubuntu.com/69299/](http://paste.ubuntu.com/69299/)

and my xorg: [http://paste.ubuntu.com/69286/](http://paste.ubuntu.com/69286/)


***Can you help me, please?***


THANKS in advance!

---

### Post by xuncall on 2008-11-09
No one??

---

### Post by oldsoundguy on 2008-11-09
just to let you know you are not the only one with wide screen issues in Intrepid.  I have a desktop that will not drive a 24" cinema with an Nvidia card, so, there MAY be an issue with the OS.

---

### Post by xuncall on 2008-11-09
I never set before my 21.6" screen with another ubuntu. This is my first time and people said to me that setting the correct modeline and resolution in xorg it is posible and easy to do it, but as i am new with this...

Continue asking for help...

---

### Post by xuncall on 2008-11-10
Does anybody know if is posible what i am asking for? I am sure than yes, but nobody answer...

---

### Post by xuncall on 2008-11-14
Finally, i fixed my problem installing Mandriva 2009 One. After to read this article: [http://www.rebelion.org/noticia.php?...uro-de-ubuntu-](http://www.rebelion.org/noticia.php?...uro-de-ubuntu-)

and that i couldn't fix my problem, i tryed another distributions. I found Mandriva and in 2 min i could fix it without xorg.conf and without console. Really good!!

I left here my actual xorg.conf in Mandriva because it can help people with the same problem.

[http://pastebin.com/mfc53ffe](http://pastebin.com/mfc53ffe)


Good luck!

---

### Post by orvils on 2009-03-10
The solution that worked for me.

**1.** Get geeky config data (modline) for a desired resolution (1680x1050).

```
gtf 1680 1050 60
```
last 60 is refresh rate.
The output is something like this

```
user@user-laptop:~$ gtf 1680 1050 60

  # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  Modeline [COLOR="DarkRed"]"1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync[/COLOR]


```

**2.** Add a desired resolution (1680x1050) to the "system"

```
 xrandr --newmode [COLOR="DarkRed"]"1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync[/COLOR]
```

I also did the following, but I don't konw if that is neceserry

```
 xrandr --output VGA --mode 1680x1050_60.00
```
[B]
3.[/B]Configure display via Gnome settings. (System -> Preferences -> Screen resolution)

From now on everything works fine, Gnome screen resolution tool allows to configure everything and settings remain after reboot.

Hope this helps someone :)

---

