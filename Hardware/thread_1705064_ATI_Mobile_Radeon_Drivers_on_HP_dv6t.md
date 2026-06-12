---
title: "ATI Mobile Radeon Drivers on HP dv6t"
date: 2011-03-11
forum: Hardware
---

### Post by m60dude5 on 2011-03-11
Hi guys,
I'm pretty new at Ubuntu but I'm trying to install it on my laptop. I have an HP Pavillion dv6t. The install for 10.10 worked fine, I'm dual booting perfectly. I installed all of the updates, no problem. However, I got a message saying proprietary video card drivers were available. So I installed them and rebooted. On reboot, I only got a command prompt. I knew it had something to do with the drivers I had just installed, so I reverted back to the previous, standard drivers and rebooted back into the GUI. Everything's fine. However, I can't find out how to install the drivers so I can use compiz, etc.

I also have switchable graphics, which might be an issue, but I don't know. Thanks for any help!

Oh, the graphics card is an ATI Mobility 5000 Radeon series.

---

### Post by adduds on 2011-03-11
hey i had the same problem...when you install the fglrx drivers linux is still trying to use the onboard graphics chipset....

go into ur bios and change graphics to discrete (from switchable)

that'll disable ur onboard chipset

hope that helps mate :)

---

### Post by m60dude5 on 2011-03-11
Hi, thanks for the quick reply! Unfortunately, there is no option in my BIOS for switching graphics modes. It seems to be a built-in-to-Windows kind of thing. I'm trying to disable it from there, but once I try that, is it possible to install alternate drivers? Thanks again!

---

### Post by adduds on 2011-03-11
> **m60dude5 said:**
> Hi, thanks for the quick reply! Unfortunately, there is no option in my BIOS for switching graphics modes. It seems to be a built-in-to-Windows kind of thing. I'm trying to disable it from there, but once I try that, is it possible to install alternate drivers? Thanks again!

I'm sorry what do you mean install alternate drivers? and where?

---

### Post by m60dude5 on 2011-03-11
Nevermind, I managed to get it working. For anyone looking at this thread:

1. I went to this site:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

2. I downloaded the drivers for the dv6t

3. I installed them by following these directions exactly:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

4. Reboot, enable Advanced Desktop Effects, it searches and enables the driver. Everything works.

Thanks for helping! I hope someone finds this useful.

---

### Post by adduds on 2011-03-11
glad you got it working g/l :)

---

### Post by Porto143 on 2011-03-18
and you are running now with both your graphics turned on?

---

