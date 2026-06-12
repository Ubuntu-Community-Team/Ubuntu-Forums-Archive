---
title: "didn't work when installed, didn't work now"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by currag on 2009-09-03
I've installed the latest version of ubuntu, 9.04, using the "install inside windows" option, great. When booting for the first time, it gives me this error:

"powernow-k8 bios error no psb or acpi _pss object"

i googled it and found that i had to enable the "cool n' quiet" option of my mother.. did that, so now it doesn't give me any error, but still hangs and now only shows this thing(which also showed earlier along whit the error):

BusyBox v.1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)

letting me ready to write (don't know what...)

so, back to windows i uninstalled ubuntu, but know everytime i restart it  keeps asking me if i want to boot windows or ubuntu:confused:

any suggestions?

PS: sorry for any sintax problem but the spanish forums aren't working..!

---

### Post by raymondh on 2009-09-03
> **currag said:**
> I've installed the latest version of ubuntu, 9.04, using the "install inside windows" option, great. When booting for the first time, it gives me this error:

"powernow-k8 bios error no psb or acpi _pss object"

i googled it and found that i had to enable the "cool n' quiet" option of my mother.. did that, so now it doesn't give me any error, but still hangs and now only shows this thing(which also showed earlier along whit the error):

BusyBox v.1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)

letting me ready to write (don't know what...)

so, back to windows i uninstalled ubuntu, but know everytime i restart it  keeps asking me if i want to boot windows or ubuntu:confused:

any suggestions?

PS: sorry for any sintax problem but the spanish forums aren't working..!

Currag,

If you are using XP, you need to access the boot.ini file (in XP) and manually delete the wubi/ubuntu related line.  **ONLY THE WUBI RELATED LINE**.

Aqui esta la documentacion:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

About the inoperable Ubuntu inside windows, I have found that if my windows is fragemented, bloated or whatever, I have a terrible wubi-ubuntu experience.  I hope you consider installing Ubuntu in its' own partition.

Muy buenas,

---

### Post by currag on 2009-09-03
thanks! xp problem solved

and yes, tomorow i'll try again making a partition for ubuntu

---

### Post by raymondh on 2009-09-06
> **currag said:**
> thanks! xp problem solved

and yes, tomorow i'll try again making a partition for ubuntu


Congratulations and happy ubuntu-ing :)

---

