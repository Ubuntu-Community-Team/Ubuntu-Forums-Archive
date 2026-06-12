---
title: "OpenGL 4.x enquiry - Xorg vs fglrx for Radeon HD 7970"
date: 2015-06-13
forum: Hardware
---

### Post by Ben_Radburnd on 2015-06-13
Hey there,

Im running Ubuntu 15.04 and loving it. But I would simply like to know more about the Xorg open source drivers in it and whether I messed up [IMG]http://ubuntuforums.org/images/icons/icon10.png[/IMG]

I've been [here]("http://ubuntuforums.org/help.ubuntu.com/community/BinaryDriverHowto/AMD?action=show&redirect=BinaryDriverHowto%2FATI") to ensure I'm doing things right. But it turns out when I use the Radeon proprietary drivers I get a black screen on login on my main user. The only way I was able to switch back, was to log into the guest user first then switch users and sometimes (not always), it would allow me to change back to Xorg drivers in my main account before the screen goes black..

But when I would do that, they somehow mess up the Xorg open source drivers when I switch back (no high resolution setting, wine doesn't work properly, steam wont open)
I followed another [forum]("http://askubuntu.com/questions/539423/revert-amd-graphic-drivers") to purge the xorg drivers, reset the config file, re-downloaded, reinstalled + reconfigured, which fixed it.

I am new and I'm not sure whether me doing this is related to my current problem.

My question is this:
Xorg drivers only give me OpenGL 3 support, when my card is capable of 4.x, is this normal or is this because the xorg.conf is empty or is it something I did from the purge?

Why do I ask this?
Proprietary drivers make my computer black screen. There if Xorg drivers could possibly provide the OpenGL support for 4.x, I'd be able to avoid using closed source drivers to run my games, or downgrade to 14.04 to resolve this.

Here is my VGA and OpenGL info:

```
tankburn@Reanimated:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X] [1002:6798]
Subsystem: ASUSTeK Computer Inc. Tahiti XT2 [Matrix HD 7970 Platinum] [1043:044c]
Kernel driver in use: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT HDMI Audio [Radeon HD 7970 Series] [1002:aaa0]

```


```
tankburn@Reanimated:~$ glxinfo | grep -i opengl
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD TAHITI
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.5.2
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.5.2
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 10.5.2
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:

```

Some help would be greatly appreciated, let me know if you would like more information.

---

### Post by Yellow Pasque on 2015-06-14
Normal. OpenGL 4.x for open drivers is getting close, but not there yet (radeonsi is the name of your gallium/3D driver): [http://cgit.freedesktop.org/mesa/mesa/tree/docs/GL3.txt](http://cgit.freedesktop.org/mesa/mesa/tree/docs/GL3.txt)

---

### Post by Ben_Radburnd on 2015-06-15
Thats great info, thanks for confirming this good sir o7.

---

