---
title: "AMD Stoney Ridge Graphics (R2,R3,R4,R5) flickers screen and other problems"
date: 2019-05-07
forum: Hardware
---

### Post by rathorecdn on 2019-05-07
AMD APU A4-9125 with Stoney R3 graphics.

LENOVO IDEAPAD 330-15AST

i always use ubuntu 19.04 on my older lenovo g560 with intel graphics. and has no problem.

but in amd graphics ubuntu 19.04 creates screen flicker at "FULL BRIGHTNESS". when i set brightness to one step low, then its become okay. when charger connected and set to full brightness then screen flickers. this does happens on when running on battery.

ubuntu kernel 4.18 on ubuntu 18.10 works perfect with some startup error messages like "amdgpu constructor. ..." etc etc...

i have also used ppa for amdgpu graphics like "obaif" etc...but nothing happens.

also when put to sleep, laptop hardware freezes. and no wakeup from sleep problem. no keyboard and no other peripheral works.

---

### Post by mastablasta on 2019-05-08
i would check all logs for any errors, maybe try to change (if this is still possible) to X.org session instead of Wayland or Mir or whatever it is these days.

it's hard to say what is happening from your description since you didn't add any error messages.

then report the issue(s) to people making the opensource AMDGPU drivers.

as for the sleep/wake... this is power management issue. it can be caused by drivers or something else. again try to enter terminal console and check the logs for errors.

finally, try the 18.04 LTS  version. it is supported until 2023. if it works, use it (use what works best).

---

### Post by rathorecdn on 2019-05-14
hi friends, i'm not advanced to linux but the thing is i have switched to fedora 30, which is by default uses wayland session with gnome and all the other problems i faced with ubuntu has gone with it. because of fedora constantly upgrades to newer version of kernels. i'm currently on 5.0.14-300.fc30.x86_64 kernel and no issues so far.

only one common problem that at 100% brightness screen starts flickering. that's the problem with all the distros. maybe it will be fixed with future versions in kernel.

thanks for the help guys.

---

