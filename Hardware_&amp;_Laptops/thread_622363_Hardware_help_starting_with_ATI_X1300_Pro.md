---
title: "Hardware help starting with ATI X1300 Pro"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by Multi-Booter on 2007-11-24
Hello all... I've just installed 7.10 on my system and so far it works the best "by default" of any linux distro I have tried.

However, I need to go through my hardware and see to it that all is well.

The aggrivation I have right now is that I have an ATI Radeon X1300 Pro graphics card and a dell widescreen monitor. The display ratio is 1.6:1 or it may be better to say the native resolution is 1680x1050 but I prefer something larger like 1280x800.

Anyways, when I check my hardware Ubuntu seems to recognize everything for what it is. But it's using generic drivers... which are working, and look OK other than the fact everything is stretched on the wide screen.

I used ATI's proprietary driver once over a year ago on a Fedora installation and did not like the results at that time.

So I am looking for a little guidance about where to start on this today.....

---

### Post by Multi-Booter on 2007-11-24
This is the right place for hardware talk right?....

Or just laptop hardware? 

:confused:

---

### Post by Multi-Booter on 2007-11-25
Anybody?

---

### Post by Yellow Pasque on 2007-11-25
If you can live without 3d desktop eye candy effects, Install the ATI proprietary driver that comes with Ubuntu (xorg-driver-fglrx). You can do this by simply pulling down the System menu -> Administration -> Restricted Driver Manager
Check the box to enable the drivers. When you reboot, you should be able to change your resolution to whatever you fancy, though 1680x1050 will look best.

If you run into problems, run the following commands and give the output line
```
sudo update-pciids
lspci | grep "VGA"
```

Also,
```
fglrxinfo
```

And, post you /etc/X11/xorg.conf file

---

### Post by Multi-Booter on 2007-11-26
> **Temüjin said:**
> If you can live without 3d desktop eye candy effects, Install the ATI proprietary driver that comes with Ubuntu (xorg-driver-fglrx). You can do this by simply pulling down the System menu -> Administration -> Restricted Driver Manager
Check the box to enable the drivers. When you reboot, you should be able to change your resolution to whatever you fancy, though 1680x1050 will look best.

If you run into problems, run the following commands and give the output line
```
sudo update-pciids
lspci | grep "VGA"
```

Also,
```
fglrxinfo
```

And, post you /etc/X11/xorg.conf file

I can live without the 3d desktop eye candy effects... but what if I couldn't?... just out of curiosity?

As for the ATI proprietary driver... I understand I can use that... I did so with Fedora Core 6.
But I was really unimpressed with that combo.

Outside of that, I was told doing so was a mistake because the proprietary driver permenantly replaced original system files in Fedora.

So I guess what I am asking is... is the same true here, or does Ubuntu handle it differently?

I'm looking to see if there are any long term side effects that I'll regret later down the road before doing it.

---

### Post by Yellow Pasque on 2007-11-27
> I can live without the 3d desktop eye candy effects... but what if I couldn't?... just out of curiosity?
Then you would have to use one of the later releases of the ATI driver, which isn't officially supported by Ubuntu. If you ran them, you would see why (buggy).

> Outside of that, I was told doing so was a mistake because the proprietary driver permenantly replaced original system files in Fedora. So I guess what I am asking is... is the same true here, or does Ubuntu handle it differently?
To my knowledge, you should be able to uninstall the proprietary driver by either unchecking the box in the restricted manager or removing the xorg-driver-fglrx package. I'm not aware of permanent overwriting of files, except for maybe xorg.conf, which is easy to configure yourself.

---

### Post by Multi-Booter on 2007-11-27
OK, have a look at these two links in order and let me know what you think????

[http://www.phoronix.com/scan.php?page=article&item=922&num=1](http://www.phoronix.com/scan.php?page=article&item=922&num=1)

[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)


This would not be officially supported like you are saying?

---

### Post by Multi-Booter on 2007-11-28
Well... for now I have enabled the restricted driver...
Much like when I was in fedora, all I gained was one useable resolution for the wide screen.

It's the 1680x1050 which is the native resolution and all good and fine.

But to be honest, I don't care for this resolution. It's too large, which makes many things display too small, and there is a lot of internet content it doesn't mesh with.

In windows I have the same opinion, but have one other resolution choice that is the proper ratio... which is 1280x800.

I wonder what I might gain by downloading that newest linux driver from ATI's site?

---

### Post by Multi-Booter on 2007-11-30
I tried Envy too... which said I was already using the driver.


I guess the only other thing to try is the ATI Catalyst 7.11?

---

### Post by Multi-Booter on 2007-12-01
Any reason to not try the the ATI Catalyst 7.11?

---

### Post by Yellow Pasque on 2007-12-03
Catalyst 7.11 isn't too much of an improvement over the previous release. 3D performance is better, but the same glaring bugs in 8.42.3 are still there. I'm sticking with 8.40.4 for now.

---

