---
title: "Graphics Drivers"
date: 2008-06-24
forum: Hardware
---

### Post by Dark_Fire on 2008-06-24
Hey hey,

I need to install graphics drivers for this one laptop, but im not sure if its ATI or NVidia... how can I find this out?

Also what is the best way to go about installing drivers?

Thanks allot

Dark_Fire

---

### Post by Dark_Fire on 2008-06-24
Is there no way to find this out? I know how to get the NVIDIA graphics driver... but have no idea about ATI...

If someone can just help me to find out what card it is. How does one go about checking the hardware?

Thanks

---

### Post by Qrikko on 2008-06-24
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

there you can get the vendor versions of drivers for nVidea and/or ATI

and to find out what card you are running.. hmm.. either check the manual you got with your computer.. or I guess it would be easy to check the "Hardware drivers" application you can find it through your Gnome Ubuntu menu..

System | administration | Hardware drivers

I only know that if you have an ATI card it should say there.. but there is probably better ways to find out.. maybe this help some?


[http://ubuntuforums.org/showthread.php?t=511116](http://ubuntuforums.org/showthread.php?t=511116)

or simply run:

```

lspci | grep ATI

```

if you have a ati card this should return some info while:

```

lspci | grep nvidia

```
should not..

hope it helps :)

---

### Post by jualin on 2008-06-24
To find out your hardware please type on the terminal> lspci and look for the VGA line. That will give you the name of your Video Card. The link provided above is the Envy-ng package from the repos. This utility will only work with Ndivia and ATI chipsets. After you found out the model of your video card you can search the forums or google with the exact model.

---

### Post by Dark_Fire on 2008-06-24
Thanks so much guys. The guy came to take his laptop but I tried it on my PC and it works. So ill try to get his laptop back and quickly update that. :)

I am still trying to find out if the Samsung F700 would work as a modem on Linux, and how?
Also the Sony Ericsson 910i.

Where should I post this question or can anyone give me a answer for this?

Thanks

Dark_Fire

---

