---
title: "help pls VIA VN896"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by dark_thug on 2007-03-14
1st of all let me say hi to every one ^_^

can some one help me pls i got a fujitsu amilo pro v3515 laptop using VIA chipset
well my problem is that the resolution needs to be 1280x800 but im stuck at that 768
something and is someone can poit me out on how and where to get the video card driver
of VIA896 Chrome9 IGP, thnks, sorry for asking this questions but i really really want to use ubuntu

---

### Post by ihrd on 2007-03-15
hi!

I am buy v3515 to, and now have many problems (Kubuntu 6.10)
don`t work via driver, audio, bright maximum and i can`t down it.
Now i googling, and use search on this forum
[http://www.ubuntuforums.org/showthread.php?t=292016&highlight=VIA+Chrome9+HC](http://www.ubuntuforums.org/showthread.php?t=292016&highlight=VIA+Chrome9+HC)
[http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/](http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/)

m.b. it can be helpful for us ^

sorry my bad english.

---

### Post by ihrd on 2007-03-16
so, i just change notebook :) only 200$ and now i work on Lenovo 3000 N100. All right.

---

### Post by probos on 2007-04-01
> **ihrd said:**
> 
bright maximum and i can`t down it.


I had the same problem, it's so bright it hurts your eyes, try Fn + F8 before the system loads. It's not a fix but at least works.

---

### Post by dark_thug on 2007-06-10
well i tried the tutorial from [http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/](http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/)
well it worked after 3 reboots it only shows a white line and a blue background :( anyway i like ubuntu but i need games to play ill switch back to this CR*PY windows and ill just wait for openchrome and atlst ill wait for 3D support but stil if some one found a fix pls post or msg me thnkx




ubuntu Edgy          -Best as God
fedora core 6        -Some What Ok
OpenSuSE 10.2     -Some What Ok
Back|Track2           -Good for security and CR*PS

---

### Post by agsamek on 2007-11-08
I've got v3515 and Ubuntu 7.04. Use:

sudo dpkg-reconfigure -phigh xserver-xorg

select vesa, then 1280x800, reboot and it should work.

---

### Post by oreja on 2007-12-02
Thanks, that works!

---

### Post by santoxyz on 2007-12-31
i have 7.10 on v3515;
the best compromise i found to make all fully (or... something like) functional is:

1) recompile the kernel DISABLING alsa built-in driver and patching DSDT to make the fan stop when the cpu is cold (i wrote a post for this)
2) install (from source) alsa-driver 1.0.15 and do an alsaconf
3) install last (svn) openchrome video drivers

to change the video brightness you can, as root 

echo "7" > /proc/acpi/video/VGA/LCD/brightness

substitute '7' with 0 or 1 or 2 or 3 ......

---

