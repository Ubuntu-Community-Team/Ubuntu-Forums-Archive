---
title: "Reduce brightness on HP Pavilion dv5-1020ep (Ubuntu 8.10 64 bits)"
date: 2009-01-10
forum: Hardware
---

### Post by paapereira on 2009-01-10
My brightness function keys always worked, but suddenly they stopped working as well as the "Reduce backlight brightness" option in Power Management Preferences :( 

I have a HP Pavilion dv5-1020ep running Ubuntu 8.10 64 bits.

I'm having trouble understanding the problem.

Here some additional info after searching the forum and google the problem:

```
grep . -r /var/lib/acpi-support/*-*
/var/lib/acpi-support/bios-version:F.20
/var/lib/acpi-support/system-manufacturer:Hewlett-Packard
/var/lib/acpi-support/system-product-name:HP Pavilion dv5 Notebook PC
/var/lib/acpi-support/system-version:Rev 1
```

```
more /proc/acpi/video/DVGA/LCD/brightness 
<not supported>
```

```
sudo echo -n 5 > /proc/acpi/video/DVGA/LCD/brightness 
bash: /proc/acpi/video/DVGA/LCD/brightness: Permission denied
```

Needless to say my battery ends very fast this way.

Please help me to fix this.

---

### Post by HA4ever on 2009-01-12
I have exact problem since 3days

I'm using hp dv6800  (Ubuntu 8.10 32 bits)
 f
<< maybe cuz i use pre-release updates from update-manager

---

### Post by paapereira on 2009-01-12
I believe it was a recent kernel or hal update...

After many digging I found a workaround somewhere (sorry, don't remember where). This isn't a fix... If I unplug my power cord the monitor still don't dim... Still the function keys now do their job.

Just add *acpi_osi="Linux"* to your grub menu:

```
sudo vi /boot/grub/menu.lst
```

```
title           Ubuntu 8.10, kernel 2.6.27-11-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=cba317f7-1d97-4cf8-9ac8-a4a6aaf0ea81 ro quiet splash **acpi_osi="Linux"**
initrd          /boot/initrd.img-2.6.27-11-generic
quiet
```

I add a post in my blog:

[http://lof-ubuntu-xp.lofspot.net/reduce-brightness-hp-pavilion-dv5-1020ep-ubuntu-810-64-bits/](http://lof-ubuntu-xp.lofspot.net/reduce-brightness-hp-pavilion-dv5-1020ep-ubuntu-810-64-bits/)

---

### Post by Ayuthia on 2009-01-12
> **paapereira said:**
> 

```
sudo echo -n 5 > /proc/acpi/video/DVGA/LCD/brightness 
bash: /proc/acpi/video/DVGA/LCD/brightness: Permission denied
```


I don't have a solution to your problem, but if you are trying to change the settings for brightness by changing /proc/acpi/video/DVGA/LCD/brightness, you can try the following instead:
```
echo -n 5 | sudo tee /proc/acpi/video/DVGA/LCD/brightness
```You are getting the permission denied because the info after the '>' is not getting the sudo permission.

---

### Post by crazyness003 on 2009-01-14
I started a bug report o this issue. Check it out here:
[https://bugs.launchpad.net/ubuntu/+bug/316145](https://bugs.launchpad.net/ubuntu/+bug/316145)

---

### Post by paapereira on 2009-01-16
Latest acpi and kernel updates just solved my problems :guitar:

---

### Post by crazyness003 on 2009-01-16
confirmed

---

### Post by TonyFordz on 2009-02-18
I had same problems with my Windows installations screwing up my gamma & lighting on my monitors & honestly at first I thought it was the monitor, but tried a different one did the same damn thing but more so in my games, and then thought it was my video card, but once I got the AMD motherboard with different video it was the same thing, so I use the follow freeware program which works great in both windows & linux if you run it in WINE.

Gamma Panel 1.0.0.2 beta
[http://www.download.com/Gamma-Panel/3000-2094_4-10703616.html?tag=mncol](http://www.download.com/Gamma-Panel/3000-2094_4-10703616.html?tag=mncol)

This is a very easy to use program works great I love it myself use it a lot with Shaiya, 2Moons, Combat Arms, Counter-Strike:Source, and so on.

Still have no clue what the hell cases the lighting to get all out of wack like I said this happened to me in Windows not Ubuntu my light is just fine with Ubuntu so who knows.

---

