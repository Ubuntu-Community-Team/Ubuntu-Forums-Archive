---
title: "DualScreen problem with Optimus (but functional)"
date: 2014-04-07
forum: Hardware
---

### Post by seto2 on 2014-04-07
[COLOR=#000000][FONT=Arial]Hi all,

I have a Lenovo T430 (with an Optimus graphical system), connected to a Dock Station with an output DVI (a 23" screen is on this output). I have Ubuntu 14.04 Beta1.

Optimus works great with the last nVidia drivers (331) and nvidia-prime.

With the command
```
prime-select nvidia
```
I'm able to use the nvidia card rather than the Intel one. Note that the DVI port on the DockStation can be used only with the nVidia card ! 

The dualscreen is nearly functionnal, I have my workspace on the two screens, and when I go in the parameters, I see correctly my two screens.

But, if I want to configure a little bit deeper, via nvidia-settings, it sees only the screen on the DVI port. So I cannot manage anything, and the problem is : the system thing I have only one screen. When a new window appear, it's between my two screens. When I "maximize" a window, it's done like if I had only one screen (so my window use the two screens).

I'm not enough confident to edit xorg.conf or other things by myself, it's why I need your help.

Here a screenshot of the screen parameters settings from Ubuntu versus nvidia-settings : [Screenshoot]("https://www.dropbox.com/s/w9s8vf40rthjtk0/dualscreenprobl.png")

I hope you can help me =) thanks.[/FONT][/COLOR]

---

### Post by seto2 on 2014-04-14
Up ?

---

### Post by seto2 on 2014-05-05
Hi all,

I still have the problem, but now I maybe can be more precise. When I switch from the intel card to the nVidia one, I have this message :

```

update-alternatives: utilisation de « /usr/lib/nvidia-331-prime/ld.so.conf » pour fournir « /etc/ld.so.conf.d/i386-linux-gnu_GL.conf » (i386-linux-gnu_gl_conf) en mode manuel
update-alternatives: utilisation de « /usr/lib/nvidia-331-prime/alt_ld.so.conf » pour fournir « /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf » (x86_64-linux-gnu_gl_conf) en mode manuel

```

Thanks in advance

---

