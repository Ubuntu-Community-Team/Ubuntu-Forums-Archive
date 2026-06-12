---
title: "Firefox_problem"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by NielsAMD on 2009-08-19
Hello,

I have a problem to run firefox, i dont know precise what i have done wrong.
It may have to do something with this command:
>: sudo apt-get upgrade

I have tried using this command:
>: sudo dpkg-reconfigure firefox
Results in saying i havent installed firefox, however i have reinstalled it twice now using the synaptics package manager.

When i try to lauch firefox the process does not show up in the system monitor (process tab).

I only have had this problem today, using another computer to write this.

My system:

Ubuntu 9,04 Jaunty - kernel 2.6.28-15-generic
AMD 7750 X2 BE OC @ 3 Ghz
2 GiB OCZ DDR-2 RAM @ 1066 MHz
ASUS M3A78PRO
Radeon 3850 OC
250 GiB HD Samsung Spinpoint F1


Thanks for helping,

Niels

---

### Post by linux4me on 2009-08-19
You might get some useful information by trying to start Firefox from Terminal.

Open Terminal (Applications->Accessories->Terminal) and type:
```
firefox
```
then hit Enter.

Post the error message you get there.

---

### Post by oldsoundguy on 2009-08-19
Many now use the Source Forge Ubuntuzilla python script for updating Firefox (or anything Mozilla).
[http://linux.softpedia.com/get/Internet/HTTP-WWW-/Ubuntuzilla-30545.shtml](http://linux.softpedia.com/get/Internet/HTTP-WWW-/Ubuntuzilla-30545.shtml)

As to launching the program .. why terminal?

Applications> Internet> and there it is.  I took the icon and dragged it to the top panel and dropped it there.  Instant one click launch.

---

### Post by NielsAMD on 2009-08-19
I think I already fixed it, thanks for helping me anyway.

I used the command:

sudo aptitude install firefox

then rebooted, and now it works.

Thanks,

Niels

---

### Post by linux4me on 2009-08-19
> **oldsoundguy said:**
> Many now use the Source Forge Ubuntuzilla python script for updating Firefox (or anything Mozilla).
[http://linux.softpedia.com/get/Internet/HTTP-WWW-/Ubuntuzilla-30545.shtml](http://linux.softpedia.com/get/Internet/HTTP-WWW-/Ubuntuzilla-30545.shtml)

As to launching the program .. why terminal?

Applications> Internet> and there it is.  I took the icon and dragged it to the top panel and dropped it there.  Instant one click launch.

I thought he had installed Firefox but wasn't able to get it to launch. Starting it from Terminal would have given him some error output in that case instead of silently failing.

---

