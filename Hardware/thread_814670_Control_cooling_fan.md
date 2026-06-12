---
title: "Control cooling fan"
date: 2008-05-31
forum: Hardware
---

### Post by ZeldaFan on 2008-05-31
How do I control my cooling fan in ubuntu? How can I make it run faster/slower based on the temperature of my laptop? Are there any utilities for doing this, preferrably GUI.

---

### Post by nyvaerld on 2008-06-08
Hi there,
Try using lm-sensors (I don't know of a GUI for this):

```
sudo apt-get install lm-sensors
sensors-detect
pwmconfig
```

You might also want to give a shot to hddtemp.

---

### Post by ZeldaFan on 2008-06-10
I've tried lm-sensors but for some reason it doesn't work with my laptop. It recognizes my core temperatures but it doesn't recognize my fan speeds. I have an HP dv9000t laptop by the way.

---

### Post by thomas515 on 2011-04-24
I have an HP dv6000 with the same issue.

---

### Post by Easy Does It on 2011-04-26
I have the same problem on my Compaq laptop.  

I seem to have fixed it by also installing the *sensors-applet* and having this always running in the gnome panel.

I have been using it like this  for a couple of weeks and it seems to be behaving itself.

This may be a problem if I decide to start using Unity, but for now it seems to work using Gnome.  :D

---

### Post by KegHead on 2011-04-26
Hi!

I've found that upgrading my kernel helps.

sudo apt-get update

sudo apt-get install linux-image -f

KegHead

---

