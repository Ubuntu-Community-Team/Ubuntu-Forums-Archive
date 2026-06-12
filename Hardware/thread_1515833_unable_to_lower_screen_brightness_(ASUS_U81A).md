---
title: "unable to lower screen brightness (ASUS U81A)"
date: 2010-06-22
forum: Hardware
---

### Post by v1gorus on 2010-06-22
I have installed Ubuntu 9.10 with wubi along side Win7. I noticed that my brightness is at 100% and kills my battery and eyes. I have tried almost everything to fix it. So I turn to you guys.
First things I tried is obviously my fn buttons which work on Win7. But the wireless fn does work. I also tried the brightness applet, also doesn't work. 
I also tried to upgrade to 10.04 in case the latest kernel supports my laptop but it doesn't fix brightness either. In fact 10.04 made it worse since now I can boot into Ubuntu at all because of this [http://ubuntuforums.org/showthread.php?t=1515803](http://ubuntuforums.org/showthread.php?t=1515803)
Anyways one problem at a time right.
I also tried this 
[http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html](http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html)
but it work let because of some permission issues.
I also found a folder where the fn button functions are stored etc/acpi/events:
[http://www.overclock.net/attachments/linux-unix/159461d1276209479-ubuntu-comeback-help-screenshot.png](http://www.overclock.net/attachments/linux-unix/159461d1276209479-ubuntu-comeback-help-screenshot.png)
I don't think anything in bios would help me with this but I wouldn't rule it out.
I think gave info about the problem.

---

### Post by Picro on 2010-06-23
Hi there,
I faced a similar problem when I installed Lucid 10.04 NRE on my netbook, with volume and brightness Fn keys refusing to work. This post was useful and helped me resolve the issue: [http://ubuntuforums.org/showthread.php?p=9314215#post9314215](http://ubuntuforums.org/showthread.php?p=9314215#post9314215)
Cheers

---

### Post by v1gorus on 2010-06-24
I've done these instructions no luck.
[http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html](http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html)
```

root@igor-laptop:~# mv '/home/igor/Downloads/video_brightnessdown.sh' '/etc/acpi' 
root@igor-laptop:~# mv '/home/igor/Downloads/video_brightnessup.sh' '/etc/acpi'

```
prehaps i should update bios?

---

