---
title: "What is GOOD Graphics Card for Kubuntu 9.04?"
date: 2009-07-14
forum: Hardware
---

### Post by HighlyDubious on 2009-07-14
I'll try to keep this short and sweet.

I've built a new system:[INDENT] ASUS Rampage II GENE
Intel i7 920 @ 2.66 Ghz
ATI Radeon HD 4650
6 gb RAM
2TB worth of HD's
 Two 22" LG Flatron W2234S monitors
[/INDENT]I installed 9.04, it looked great, but I could only get one monitor to work. I tried upgrading to the proprietary ATI drivers, and that's when my problems started. Now, about half the time, when I re-boot, I get the dreaded screen full of pixel garbage, indicating that the graphics driver is somehow fouled up. 

I've found this command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```and sometimes with more messing around and more Googling, I can get the drivers to finally reset back to default. -- but sometimes not.

So, bottom line, I'm prepared to toss the ATI HD 4650, and I just need to know, what is a good NVidia card that is stable, widely used, well supported, supports 3D Desktop, and preferably will give me full support for dual monitors at 1680x1050. -- AND won't require me to diddle with the damn drivers every time I reboot? (btw, gaming is not an issue for me)

For what it's worth -- and I know I may be asking *too much* here -- but I'd prefer it to be a relatively "newer" card. This machine will also probably end up dual-booting with Windoze 7 when that is stable. So I know I'll want a card that is powerful enough to handle the insane code-bloat and gpu hogging that will bring.

---

### Post by lykwydchykyn on 2009-07-14
I'm not a video card expert, but I'm using a GeForce 8400 GS and it's been working great for me for about 3 or 4 months.  I have dual monitors on Kubuntu 9.04, just using the proprietary Nvidia driver in the repos.

I don't think it was that expensive, but then the company bought it not me.

---

### Post by HighlyDubious on 2009-07-14
> **lykwydchykyn said:**
> I'm not a video card expert, but I'm using a GeForce 8400 GS and it's been working great for me for about 3 or 4 months.  I have dual monitors on Kubuntu 9.04, just using the proprietary Nvidia driver in the repos.

I don't think it was that expensive, but then the company bought it not me.

That's very good information. Especially since I happen to have an 8400 GS in my old machine.  So it wouldn't take much to rip it out and swap them.

This next question may more correctly belong in another area, but can anyone point me to some fairly straight-forward instructions on how to un-install the ATI drivers, and install the NVidia ones from CLI? 

I can get to the CLI (with networking), but as of now, every time I try to start the x-server, my screen goes all screwy. If possible, I'd prefer to not do a whole new re-install of 9.04.

---

### Post by lykwydchykyn on 2009-07-14
> **HighlyDubious said:**
> That's very good information. Especially since I happen to have an 8400 GS in my old machine.  So it wouldn't take much to rip it out and swap them.

This next question may more correctly belong in another area, but can anyone point me to some fairly straight-forward instructions on how to un-install the ATI drivers, and install the NVidia ones from CLI? 

I can get to the CLI (with networking), but as of now, every time I try to start the x-server, my screen goes all screwy. If possible, I'd prefer to not do a whole new re-install of 9.04.

You shouldn't need to do either of those.  At worst, just rename your /etc/X11/xorg.conf file to something else.  The next time X starts up, it will see there is no xorg.conf file and generate a default one.   By default, X autodetects the card and applies the most appropriate (non-proprietary) driver.  In the case of Nvidia, this will be the free "nv" driver.

Once you're there, you just run the hardware and drivers tool and enable the proprietary driver.  You can configure things with nvidia-config (run it with sudo so you can save the xorg.conf info it generates), and it should be set from there.

---

### Post by HighlyDubious on 2009-07-15
> **lykwydchykyn said:**
> You shouldn't need to do either of those.  At worst, just rename your /etc/X11/xorg.conf file to something else.  The next time X starts up, it will see there is no xorg.conf file and generate a default one.   By default, X autodetects the card and applies the most appropriate (non-proprietary) driver.  In the case of Nvidia, this will be the free "nv" driver.


uh... nope.

Tried that, and got a somewhat different garbage screen. Clearly something is wrong. Maybe I'll just boot from the live CD, back-up what I want, and start fresh. It's a pain, but might be easier than spending a long time trying to track down the "ideal" solution. (I've already tried some other solutions found[COLOR=Blue] [here]("http://ubuntuforums.org/showthread.php?t=1152992") [/COLOR]and [COLOR=Blue][here]("http://ubuntuforums.org/showthread.php?t=683291")[/COLOR], and none worked)

---

### Post by vinutux on 2009-07-15
> **HighlyDubious said:**
> uh... nope.

Tried that, and got a somewhat different garbage screen. Clearly something is wrong. Maybe I'll just boot from the live CD, back-up what I want, and start fresh. It's a pain, but might be easier than spending a long time trying to track down the "ideal" solution. (I've already tried some other solutions found[COLOR=Blue] [here]("http://ubuntuforums.org/showthread.php?t=1152992") [/COLOR]and [COLOR=Blue][here]("http://ubuntuforums.org/showthread.php?t=683291")[/COLOR], and none worked)

install ATI driver form official repos

**System->Administration->Hardware Drivers**

.

---

### Post by HighlyDubious on 2009-07-15
> **lykwydchykyn said:**
> You shouldn't need to do either of those.  At worst, just rename your /etc/X11/xorg.conf file to something else.  The next time X starts up, it will see there is no xorg.conf file and generate a default one.   By default, X autodetects the card and applies the most appropriate (non-proprietary) driver.  In the case of Nvidia, this will be the free "nv" driver.

Once you're there, you just run the hardware and drivers tool and enable the proprietary driver.  You can configure things with nvidia-config (run it with sudo so you can save the xorg.conf info it generates), and it should be set from there.

No matter what I did, I couldn't get any correct display. So, I went ahead and booted from the LiveCD (9.04), backed up my stuff, and did a brand new install. Not the optimal solution, but probably saved me time overall. :D

Anyway, once up, I followed your advice, and *poof*, I've now got dual monitor support, and it looks GOOD! ;-)

Best of all, I just plugged it in, right off-the-shelf and it worked! LoL

Thanks much for the suggestion, and if the rest of my needs can be solved this easily, I might just stick around! LoL

---

