---
title: "No Thermal Reading"
date: 2008-08-26
forum: Hardware
---

### Post by youthforlinux on 2008-08-26
Hey everybody, got a quick question for ya...

I recently got an Asus M2N-MX SE Plus motherboard and AMD X2 4400+ processor to upgrade my old box, and they are running great with ubuntu, like my old box, without any tweaks except for video card drivers.  The only thing with this new hardware is that if I do not boot with noapic, i get a kernel panic complaining about my Io apic not being able to sync or something im not at that box right now so i can't post the exact error, when i get home i will try to look it up, but the kernel error message told me to use the noapic option, after that everything booted and works great.  The only thing is that now I cannot get any sort of thermal reading via acpi -t

It just says that no thermal device is found, but in the bios i can check my temp settings

Once before i used a live cd on my brother's computer and he has an athlon 32bit and i needed noapic and nolapic to boot

Is this an issue with newer AMDs and linux since my only other AMD is and old K6-2 which doesnt need the noapic boot option to work...

getting thermal to work would be amazing, i check it a lot

thanks everyone,

youthforlinux

---

### Post by Kane_of_NOD on 2008-08-26
get a terminal
and do like this...

```

sudo apt-get install lm-sensors

```

then

```

sudo sensors-detect

```

you should say YES... and accept all stuff...

after all, you can run :

```

sensors

```

and you will get a lot of information


good luck :guitar:

---

### Post by garfunk3l on 2008-10-16
Hi, this works but is there a way to get hdd and gpu temperatures aswell? My comp can on windows xp but they don't detect with ubuntu.

Cheers,

David

---

### Post by kostkon on 2008-10-16
> **garfunk3l said:**
> Hi, this works but is there a way to get hdd and gpu temperatures aswell? My comp can on windows xp but they don't detect with ubuntu.

Cheers,

David
[*hddtemp*]("http://packages.ubuntu.com/hardy/hddtemp") for your HDD temp. For GPUs it depends on your card, but I think for *Nvidia* ones you can get the temp with the [*nvidia-settings*]("http://packages.ubuntu.com/hardy/nvidia-settings") utility.

You can then use a applet, like the [*sensors-applet*]("http://packages.ubuntu.com/hardy/sensors-applet") to display your readings on your panels.

---

