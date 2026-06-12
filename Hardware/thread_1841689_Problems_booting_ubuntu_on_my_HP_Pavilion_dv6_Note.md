---
title: "Problems booting ubuntu on my HP Pavilion dv6 Notebook"
date: 2011-09-09
forum: Hardware
---

### Post by chichali on 2011-09-09
Hello everybody!
Since i have tried to install ubuntu 11.04 32Bit on my Pavilion dv6 Notebook, i had troubles with the boot up!
in the past i thougth i had solved this bootup problem with adding  "i915.modeset=1" to my boot parameters. but it seams not to work with  this.

After poweron, my laptop tries directly to boot without showing up of grub menu. after that the screen stays black. when i toogle the consol to alt + F7 then i sea some information about call trace and then information belonging to my radeon mobility hd5600.
then when i reboot again, the grub menu shows and i can select the options of my default bootselection.
after one, two tries booting with ctrl + x i finally get my system booted.

can anyone please help me on that?

---

### Post by 2F4U on 2011-09-10
The parameter i915.modeset=1 turns on kernel mode setting (early activation of the graphics drivers), which should be the default with current kernels. So it is not necessary to feed this parameter to the kernel. I would try and go the other way and disable kernel mode setting by feeding nomodeset as boot parameter and see if it helps.

---

### Post by chichali on 2011-09-10
Hi 2F4U!
thanks for your help!
when i do what you said, i can bootthru without Problems, but unity is no more "ubuntu classic" and some applications aren't working properly anymore (like kairodock etc.). if i readd the i915 command, i have unity and my apps but the same story again. 

It seemd after changing from nomodeset to i915.modeset=1 that i could not boot up anymore. after i replugged the powerchord, it workd as described above. i've unplugged it to test your tip, because i had this problem from begining that i mostly had to plug in the poweradapter, that it worked at all.

do you have an other idea?

---

