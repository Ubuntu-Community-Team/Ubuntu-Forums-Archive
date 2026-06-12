---
title: "How to fix Karmic graphics on Lenovo 3000 n100"
date: 2009-11-03
forum: Hardware
---

### Post by whitefort on 2009-11-03
Hi.

I was delighted when Karmic fixed the intel graphics on my PC, but REALLY disappointed when I found I could no longer enable desktop effects on my laptop.  (Lenovo 3000 n100).

This machine has never had graphic problems on any previous Ubuntu (since Dapper), so I'm hoping there's some (easy!) thing I can do to fix it.

I'd be really grateful for any tips or advice.

Thanks!

---

### Post by Axx83 on 2009-11-03
Try

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

restart

then try disabling and re enabling effects

if it's intel it should definitely work correctly

---

### Post by whitefort on 2009-11-03
Thanks for the reply, but the fix didn't work.

I wish I knew more about hardware.  I'm probably wrong, but I didn't think the 3000 had intel graphics (otherwise wouldn't it have stopped working when I installed Jaunty)

Compiz worked fine out of the box with Jaunty, and it's only since Karmic that visual effects don't work.

Is there something I can type into a terminal to see what my graphics card is?  Then I might be able to find the right driver in Synaptic or something?

---

### Post by drs305 on 2009-11-03
I have the same laptop and can use compiz (although I don't). You can get a nice GUI app to show your system hardware called "hardinfo".

```
sudo apt-get install hardinfo
hardinfo &
```

I checked my installations. I have no hardware drivers (other than Broadcom wireless). In Synaptic, I show the following installed:
xserver-xorg-video-intel
xserver-xorg-video-i740

---

### Post by whitefort on 2009-11-03
Thanks!!

It turns out that my Lenovo has an nvidia card (which Karmic was getting wrong for some reason.)

I downloaded something called EnvyNG, and it found the right drivers for me.

Now I can get my desktop spinning again.  (I know it's just eye candy, but it's the thing that most consistently WOWs my Windows friends, so I like to keep it)

Thanks again - problem solved!

---

