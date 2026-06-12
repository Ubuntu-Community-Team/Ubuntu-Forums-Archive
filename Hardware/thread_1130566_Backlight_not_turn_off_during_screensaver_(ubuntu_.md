---
title: "Backlight not turn off during screensaver (ubuntu 8.10 - 32 bit)"
date: 2009-04-19
forum: Hardware
---

### Post by plusnplus on 2009-04-19
Hi All,

My notebook, compaq cq-40 series use ubuntu 8.10 desktop edition (32bit).
The problem is backlight of the screen not turn off during screen saver on. (i set blank screen)
I tried google it and find some clue, but still not success.
The backlight can turn off when lid notebook is close.
Also success using command vbetool force off.

One of the article i found, is try to make script of vbetool force off, then set is on when the screen saver on.
I'm do not know how to do that. So anyone can guide me step by step how to execute a acript at screensaver ?
Sorry for my poor english.
Thanks for any reply.

---

### Post by plusnplus on 2009-04-20
help me please :)

---

### Post by plusnplus on 2009-04-21
no one experience this kind of problem ?

---

### Post by plusnplus on 2009-04-22
bummmpppppppp :)

---

### Post by plusnplus on 2009-04-23
help me, as i don't want waste my lcd age, by always turn on the backlight

---

### Post by plusnplus on 2009-04-26
up for today :)

---

### Post by ssri on 2009-04-30
~$sudo vbetool off

warning, this will turn the screen completely off, so hitting a key or moving won't mouse won't bring your screen back

If this happens to you, immediately press enter to clear any keystrokes, since you are presumably still in the terminal and type:

~$sudo vbetool on

to give your user access to vbetool without elevation to superuser access with sudo, type:

~$chmod a+s /usr/sbin/vbetool

(or replace a+s with u+s to allow your group to access it)

Now, you can type vbetool off without sudo..

IMHO, this is a kludgy solution to an annoying problem that cropped up on me today btw.

good luck!

---

### Post by wolfdale on 2009-05-01
I had a similar problem with my desktop. The backlight to my lcd screen would not turn off whenever power saver mode would kick in. I did some research and troubleshooting for about 2 weeks and never could get it to work. I email AMD for some help (I have an ati card) but never got a response from them. I ended up ditching the fglrx driver (AMD's graphic driver for linux) and re-installed Ubuntu's open source "ati" or "radeon" driver which corrected my backlight problem.

I also recall reading somewhere that for laptops, a setting in the BIOS will handover power-saving mode to the OS. Maybe you should check you BIOS to see if such a setting exists.

---

