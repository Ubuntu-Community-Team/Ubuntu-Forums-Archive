---
title: "Any difference between OS of same kernel?"
date: 2012-06-02
forum: Hardware
---

### Post by inashdeen on 2012-06-02
Hi there, I would like to ask a question here. is there any difference in terms of kernel performance between two OS, say archlinux and ubuntu when both are using the same version of Kernel? thanks in advance

---

### Post by 0011235813 on 2012-06-02
Yes, but not much.
Arch Linux would be slightly faster because it is a lighter base (which is what type of packages a distribution uses and is less important than the kernel) and therefore includes less services, programs running etc.
**Especially** if you're using LXDE with Arch as opposed to Unity in Ubuntu.

---

### Post by inashdeen on 2012-06-02
I see a great difference in temperature of the PC when using Arch fork, Chakra in oppose to Ubuntu 12.04 . both are using a similar Kernel. what might be the cause?

---

### Post by 0011235813 on 2012-06-02
Might be Chakra is newer and more optimised for your hardware. What hardware are you running it on?

PS: How did you measure it? Software is known to give inaccurate results in some cases.

---

### Post by inashdeen on 2012-06-02
I am using HP compaq laptop CQ42 203 AU. 

random specification, RAM 3GB, ATI graphic card with AMD dual core.
well, there is only 1 thing i check on this laptop since it has been suffering from overheating since 11.04. i installed lm-sensors in both and perform the similar taks in bots OS. I can get up to 97^ on Ubuntu 12.04, but only 90* max on chakra. on average, ubuntu runs at 78* and chakra at 72*

---

### Post by 0011235813 on 2012-06-02
> **inashdeen said:**
> I am using HP compaq laptop CQ42 203 AU. 

random specification, RAM 3GB, ATI graphic card with AMD dual core.
well, there is only 1 thing i check on this laptop since it has been suffering from overheating since 11.04. i installed lm-sensors in both and perform the similar taks in bots OS. I can get up to 97^ on Ubuntu 12.04, but only 90* max on chakra. on average, ubuntu runs at 78* and chakra at 72*

lm-sensors? That's a software based solution, and I've heard software is notorious for giving inaccurate results in this type of thing. You might get a more accurate reading from something like the *phoronix-test-suite*  or the AMD/ATI control panel. Of course, the best way is to put a thermometer on the thing itself and see what you get.

Anyhow, those differences are quite small. There's no absolute factor I can pinpoint, just that some distributions run better on certain hardware than others.

---

### Post by inashdeen on 2012-06-02
Hurm,.. you got a point there. how do you actually get the phoronix-test-suite

---

### Post by 0011235813 on 2012-06-03
> **inashdeen said:**
> Hurm,.. you got a point there. how do you actually get the phoronix-test-suite

In Debian-based systems like Ubuntu? 
```
sudo apt-get install phoronix-test-suite
```
Or just search for phoronix in the software center.

Note: The suite you install will ask you to download additional packages for some tests.

---

### Post by inashdeen on 2012-06-03
so the source is preinstalled. ok, thank you.will try in the near future :) thanks.

---

