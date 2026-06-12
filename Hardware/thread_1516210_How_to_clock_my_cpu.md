---
title: "How to clock my cpu"
date: 2010-06-23
forum: Hardware
---

### Post by sokekoke on 2010-06-23
Hello,

I'm using a asus UL80VT laptop, with a Core 2 Duo SU7300 (1.3 GHz) cpu

now when i run:

   cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

it print:

1300000 800000 

however my laptop has this "turbo boost" button, where on windows it get overclocked to 1.7ghz
How can i achieve this on ubuntu? And if theres any other asus ul users, do any of you guys know how to make the button work? :)

Thanks!!!

---

### Post by dino99 on 2010-06-23
dont know about this button, but first you have to know if it is activated: system prefs keyboard

some usefull packages: xkb-data, x11-xkb-utils

---

### Post by sokekoke on 2010-06-23
> **dino99 said:**
> dont know about this button, but first you have to know if it is activated: system prefs keyboard

some usefull packages: xkb-data, x11-xkb-utils

Thanks, ill look into that. Do you know what is up with my frequencies? updated the post a little =)

---

### Post by dino99 on 2010-06-23
absolutly dont care about overclocking, kidding craps

---

### Post by Yellow Pasque on 2010-06-23
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429036](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429036)
[http://code.google.com/p/i7z/](http://code.google.com/p/i7z/)

> absolutly dont care about overclocking, kidding craps
People of all ages OC, and it's not really OC'ing when the manufacturer specs the product to do it. Also, if you don't care, then why bother posting?

---

### Post by sokekoke on 2010-06-23
thanks, i7z seems useful!

And yes, i would like to get 1.7ghz since that was the basis i bought my pc on - asus used a slower cpu to reduce power consumption and the overclocked it to improve preformance, atleast thats how i understand things.

but the overclocking dosen't work on ubuntu seems

---

### Post by Yellow Pasque on 2010-06-23
Ah, here's the kernel bug: [https://bugzilla.kernel.org/show_bug.cgi?id=15064](https://bugzilla.kernel.org/show_bug.cgi?id=15064)

It was fixed in kernel 2.6.33, so you would need to run a newer kernel than the Lucid default (2.6.32). This would work: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)
You need the headers and image package for your architecture, as well as the headers-all package. Download them to whatever directory you like, cd to it and:
```
sudo dpkg -i linux*.deb
```

---

### Post by sokekoke on 2010-06-24
> **Temüjin said:**
> Ah, here's the kernel bug: [https://bugzilla.kernel.org/show_bug.cgi?id=15064](https://bugzilla.kernel.org/show_bug.cgi?id=15064)

It was fixed in kernel 2.6.33, so you would need to run a newer kernel than the Lucid default (2.6.32). This would work: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)
You need the headers and image package for your architecture, as well as the headers-all package. Download them to whatever directory you like, cd to it and:
```
sudo dpkg -i linux*.deb
```

Oh, great!!! thanks for respond, now i have something to do when time presents itself :) cheers.

---

