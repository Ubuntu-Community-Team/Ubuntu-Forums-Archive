---
title: "Upgrade to 9.10, X\GNOME no longer work"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Alboin on 2009-11-01
Hello,

I just upgraded to 9.10, and now GNOME does not work.

The system boots, and using rescue mode I can log in through the text interface without any apparent issues. However, when I startx, GNOME loads, seems to work for around 10 seconds, and then stalls outright. It is the weirdest thing. 

I mean, it seems to be fully functional for a few seconds, but then just suddenly dies whether or not I move the mouse at all. (When I say 'die', I mean the mouse stops moving and the screen is static. I cannot shift to any other virtual consoles or anything like that either.)

Anyone know what the matter is? I am on a 32bit x86 machine with 512MB of RAM and a sizable hardrive. (90Gb) I have never had any trouble with any past Ubuntu installs.

Thanks very much for your time and help,
Alboin

---

### Post by Alboin on 2009-11-03
Hi again,

The problem is solved.

It turned out that compiz was causing the issue. 

I believe the Intel GMA 950 drivers are the root of the problem, because I found a similar situation on these here forums where I found the hint at compiz being an issue.

Thanks, 
Alboin

---

### Post by FelixS on 2009-11-03
I'm new in Ubuntu, How can I get and install these drivers? I have the same problem and Graphics Accelerator. Thanks.

---

### Post by sherylyamjg on 2011-01-14
> **Alboin said:**
> Hello,I just upgraded to 9.10, and now GNOME does not work.The system boots, and using rescue mode I can log in through the text interface without any apparent issues. However, when I startx, GNOME loads, seems to work for around 10 seconds, and then stalls outright. It is the weirdest thing. I mean, it seems to be fully functional for a few seconds, but then just suddenly dies [[COLOR=#000000]whether[/COLOR]](http://www.tekbar.net/ja/hackers-and-security/everyone--can-use-linux-firewall.html) or not I move the mouse at all. (When I say 'die', I mean the mouse stops moving and the screen is static. I cannot shift to any other virtual consoles or anything like that either.)Anyone know what the matter is? I am on a 32bit x86 machine with 512MB of RAM and a sizable hardrive. (90Gb) I have never had any trouble with any past Ubuntu installs.Thanks very much for your time and help,AlboinThanks for your reply! I found that it is really the cause.

---

