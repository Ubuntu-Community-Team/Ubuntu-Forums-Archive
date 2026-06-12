---
title: "Synaptic Package manager ignores .fonts.conf"
date: 2008-07-28
forum: General Help
---

### Post by raab on 2008-07-28
Hi there,

Running Hardy Heron: Linux guevara 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

I'm currently playing round with my fonts trying to get them looking better as Sans isn't the greatest. Anyway I pretty much have it how I like except Synaptic Package Manager and Software Sources seems to ignore my .fonts.conf where I've specified to turn off anti alias on fonts between 0-15. If I go to System - Admin -> Appearance and turn off Sub Pixel Smoothing then it turns off but then fonts greater than 15 wont be smoothed.

Image to see what I mean.

[[IMG]http://img214.imageshack.us/img214/2672/34457824on5.th.png[/IMG]](http://img214.imageshack.us/my.php?image=34457824on5.png)

You can see that the fonts in Synaptic are being aliased where as they shouldn't be.

And here's my .fonts.conf

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
 <test compare="more" name="pixelsize" qual="any">
  <double>0</double>
 </test>
 <test compare="less" name="pixelsize" qual="any">
  <double>15</double>
 </test>
 <edit mode="assign" name="antialias">
  <bool>false</bool>
 </edit>
</match>
</fontconfig>

```

Any help would be appreciated.

---

### Post by Oldsoldier2003 on 2008-07-28
Moved from Multimedia/video at OP request

---

### Post by raab on 2008-07-29
*bump*

someone must've run into this problem before?

---

### Post by raab on 2008-07-29
Turns out it looks in /etc/fonts/local.conf instead of .fonts.conf

---

### Post by dmizer on 2008-07-29
> **raab said:**
> Turns out it looks in /etc/fonts/local.conf instead of .fonts.conf

This is because synaptic package manger runs as root, not as your logged on user.

You'll notice that any other GUI interface running as root would have the same issue.  It's a good practice to run with different fonts for your root and user level applications so you can tell at a glance which ones are which.

---

### Post by raab on 2008-07-29
Yeah, I realised that after thinking about it properly :P I'm just anal when it comes to athestics! :)

---

