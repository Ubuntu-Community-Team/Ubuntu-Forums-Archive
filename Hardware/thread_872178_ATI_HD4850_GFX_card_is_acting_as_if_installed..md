---
title: "ATI HD4850 GFX card is acting as if installed."
date: 2008-07-27
forum: Hardware
---

### Post by hippyguy7 on 2008-07-27
I followed a guide to install my HD4850 with the latest drivers straight from ATI themselves. (Catalyst 8.7), not repository.

I finished the guide and blacklisted the old driver so that my new one would be noticed. I checked the box to enable the driver then clicked it(or something else) again. When I re-booted, I was told I would be using safe GFX mode, and had the black screen with a black x cursor. But in ubuntu, all the graphics look normal.

In driver info, it says "proprietary drivers are being used to make this computer work properly" above the box that shows my supposed driver. It is not enabled, and when I try to enable it, it fails every time. Yet it is checked for "In Use".

I also get an error when trying to access "ATI catalyst control center", this is the error:
```
 Failed to execute child process "amdcccle" (No such file or directory)
```


Also,l when trying to install the driver again via the ".run" file that contains it, I also get an error.

Please help?

---

### Post by recover89 on 2008-07-28
I built my new computer this weekend and I got an HD4850 as well.
I tried installing the latest catalyst drivers but didn't have much success.
I eventually ended up reinstalling and using the default configuration, even though I have some graphic bugs (some colors are wrong).

I'm mostly using Windows but it would be great if HD4850 will work well in Ubuntu.

Let me know if you manage to get it working properly.

---

### Post by markbuntu on 2008-07-28
You need to follow these directions carefully to get your cards working:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

They have worked for everyone who I sent there with your card.

After that, you can try the adjustments recommended here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by andycs on 2008-09-02
That guide hasn't worked for me. I'm running Hardy Heron, and any driver I try to install for my graphics card (ATI HD4850) results in failure to load graphics properly or at all on boot, and the only way to get a desktop back is by reconfiguring xorg. Any ideas? From what I can tell, I have the same issue as hippyguy.

EDIT: Have since installed manually, which (finally!) worked, bar the hard drive failing, but I don't think I can really blame that on Ubuntu. Thanks!

---

