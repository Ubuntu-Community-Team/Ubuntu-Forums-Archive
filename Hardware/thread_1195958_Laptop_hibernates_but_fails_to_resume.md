---
title: "Laptop hibernates but fails to resume"
date: 2009-06-24
forum: Hardware
---

### Post by jawadams on 2009-06-24
Hello,

I have Ubuntu 9.04 Jaunty Jacakalope running on my Toshiba Satellite A200 laptop.

It has 2GB RAM and I created a 2.25 GB swap space (wanted to be safe and create more than I needed).

I edited my /etc/fstab to automatically use my swap space and this does work correctly.

Going into hibernation appears to work correctly, but when I hit the power button to come on, it just starts up like normal.

This is not a battery issue either, it happens when plugged in.

Anyone have any ideas?

---

### Post by jverge on 2009-06-24
I fixed a similar problem with a Dell XPS laptop with an nVIDIA graphics card.  The newest driver at the time would not allow the laptop to resume from a suspension but an older driver worked great.  If you have an nvidia card I would try older and newer drivers.

---

### Post by jawadams on 2009-06-24
Mines an intel actually GMA 965 I believe...

---

### Post by andreselsuave on 2009-06-24
try using s2ram instead of the regular suspend comand. there are posts in this forum describing how to do it. If I remember correctly:

```
sudo apt-get install s2ram
sudo s2ram --force
```

try that. If that works for you, you can also substitute the default command that  gnome uses with the s2ram editing a text file, but don't remember how to do hat right now. Post your results ^_^

---

### Post by jawadams on 2009-06-25
> **andreselsuave said:**
> try using s2ram instead of the regular suspend comand. there are posts in this forum describing how to do it. If I remember correctly:

```
sudo apt-get install s2ram
sudo s2ram --force
```try that. If that works for you, you can also substitute the default command that  gnome uses with the s2ram editing a text file, but don't remember how to do hat right now. Post your results ^_^

  It says that s2ram isn't an app I can download...

---

### Post by andreselsuave on 2009-06-25
I was wrong, it is:
```
sudo apt-get install uswsusp
```

---

