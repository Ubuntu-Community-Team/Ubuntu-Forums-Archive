---
title: "Acer 7740 No Brightness Control"
date: 2010-09-06
forum: Hardware
---

### Post by caperren on 2010-09-06
Hey guys...I have an acer aspire 7740 laptop that works perfectly running Ubuntu 10.04 other than the brightness control. I have been trying to get it working for the past couple of hours and have only found one way to get it to work. If I edit /proc/default/grub and add acpi=ht, I am able to control my brightness. However, this removes the ability to use CPU-Scaling, which I need to keep. Without that addition I have not been able to get it working. Trying to manually change brightness by using this command,
```
echo 50 > /proc/acpi/video/GFX0/DD02/brightness
```
does not error out, but it doesn't change the brightness either. I'm not sure if anyone else has been able to get this working, but if you have, please let me know.

---

### Post by pashilkar on 2010-10-15
Don't know if this is relevant but this change in grub worked for my Acer Aspire 4736....
[http://ubuntuforums.org/showpost.php?p=9978592&postcount=24](http://ubuntuforums.org/showpost.php?p=9978592&postcount=24)

---

### Post by Elmer Fudd on 2010-11-15
Worked on my 7736 (in Burg) as well.
thanks pashilkar

---

### Post by fishbulb1022 on 2011-03-11
There is a ppa for a modified kernel that fixes this issue on laptops that use i915 graphics. I have installed the new kernel on my Acer Aspire 7740 and it works great. Hopefully the fix will be integrated into the main kernel soon. For now, here is the link the page where you can read about the modded kernel and the info for the ppa: 

[https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight]("https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight")

---

