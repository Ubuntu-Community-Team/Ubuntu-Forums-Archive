---
title: "HP tx2z -1000 touch-screen issues"
date: 2011-04-27
forum: Hardware
---

### Post by thed0ctor on 2011-04-27
Hello all!

I just recently installed Ubuntu 10.10 and I tried to install the drivers for the touch screen and no avail. Also if I touch the screen and it recognizes that I touched the screen the computer freezes and I'm forced to reboot. Is there any way I can disable the touch screen or install the drivers so it won't freeze? I already tried using [http://ubuntuforums.org/showthread.php?t=1252492&highlight=uninstall+ginn+tx2z]("http://ubuntuforums.org/showthread.php?t=1252492&highlight=uninstall+ginn+tx2z") and even then it still locks up.

I'm new to Ubuntu but am pretty savvy so any help would be appreciated.

This is a 64bit machine

---

### Post by Favux on 2011-04-27
Hi thed0ctor,

Welcome to Ubuntu forums!

The only freeze issue I'm aware of for N-Trig in Maverick is if you are using older firmware that only offers single finger touch.  If that's the case (check the output of *xinput list*) you can use Ayuthia's patch in the DKMS implementation located in **1) Maverick:  b) Vista firmware and single finger ("N-Trig Touchscreen") touch** on the N-Trig HOW TO.  Did you already try that?

Obviously updating the firmware would be better so you can have multi-touch if that is the problem.  Hopefully you have a Windows 7 partition and can do that.

---

