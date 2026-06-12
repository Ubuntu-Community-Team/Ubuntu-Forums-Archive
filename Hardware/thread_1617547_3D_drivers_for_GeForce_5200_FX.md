---
title: "3D drivers for GeForce 5200 FX"
date: 2010-11-09
forum: Hardware
---

### Post by Masquerade on 2010-11-09
Hey everyone,

I have a GeForce 5200 FX graphics card and I struggle to get it work for 3D.
As far as I know I need the nvidia-173 package for it to be able to run a 3D desktop and so on.

Booting with this package installed doesnt even get me to the login screen. I usually get dropped to a CLI login (if I remember right).

Booting in safe mode does let me get to the failsafeX menu but messing around there hasnt helped. 

Right now I am sticking with the nouveau drivers but I think I read that 3D is still experimental there and I dont want to keep it like that anyways.

```
compibenjamin@desktop:~/Desktop$ compiz --replace
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :1.0

Launching fallback window manager

```

[This]("http://pastie.org/1284965") is my xorg.conf. I suspect when using nouveau or other drivers I should wrte "nv" in the marked line but it works like that so whatever ^^.

Unfortunately I dont know the locations of the other relevant logs by hand so just tell me and I'll paste them. I cant be bothered to purge nouveau, install nvidia drivers, reboot into safe mode, copy the logs by hand, get into safe graphics mode, purge nvidia and install nouveau again.

---

### Post by Masquerade on 2010-11-10
bump?

---

