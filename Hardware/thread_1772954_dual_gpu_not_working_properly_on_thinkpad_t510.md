---
title: "dual gpu not working properly on thinkpad t510"
date: 2011-06-01
forum: Hardware
---

### Post by baarn on 2011-06-01
Hey, I am proud owner of a thinkpad t510
it has a dual gpu setup and i read a lot of threads about problems caused by intel optimus technology and X.

```
:~$ lscpi -v
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 21d9
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f8800000 (64-bit, non-prefetchable) [size=4M]
    Memory at f0000000 (64-bit, prefetchable) [size=128M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

01:00.0 VGA compatible controller: nVidia Corporation GT218 [NVS 3100M] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 21d8
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at cc000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ce000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 2000 [size=128]
    [virtual] Expansion ROM at cd000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

```as you can see i have the proprietary driver installed (and i want to use this one, expecially for openGL applications and programming.

yeah well but:
```
:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```nvidia-settings told me to run nvidia-xconfig which trashed that users desktop...

what can i do? any ideas?

---

### Post by baarn on 2011-06-01
is there maybe a way to reconfigure xorg.conf by hand?
or some other file, because xorg.conf seems to be some kind of deprecated since an upgrade of X some years ago...
or any log that would help on this matter?

---

### Post by Toz on 2011-06-01
Have you come across these posts/links yet? Perhaps they might be of assistance?

[http://ubuntuforums.org/showthread.php?t=1598531]("http://ubuntuforums.org/showthread.php?t=1598531")(post #6 looks promising)

[http://ubuntuforums.org/showthread.php?t=1681523]("http://ubuntuforums.org/showthread.php?t=1681523")

[http://www.thinkwiki.org/wiki/Category:T510]("http://www.thinkwiki.org/wiki/Category:T510")

---

### Post by baarn on 2011-06-01
ok, thats pretty much what i read before... (before i installed xubuntu i tried to install gentoo on this laptop but encountered pretty much the same problem, but with ubuntus bigger community i was hoping that there was a solution for this problem)

is there a way to tell grub which driver to use X with maybe?
it wouldn't be as good as switching graphics on the fly but atleast i could use the nvidia chip when at home or the intel chip when on battery.

---

### Post by Toz on 2011-06-01
In those posts it states that the switchable graphics can be turned off in the bios:

> From: [http://www.thinkwiki.org/wiki/Category:T510]("http://www.thinkwiki.org/wiki/Category:T510") - "If using the proprietary Nvidia driver (NVIDIA Driver Version 260.19.06) one has to set "Discrete" in BIOS. Linux seems to have some problems with Switchable Graphics (Optimus)."

> From: [http://ubuntuforums.org/showpost.php?p=10015663&postcount=6]("http://ubuntuforums.org/showpost.php?p=10015663&postcount=6") - "you can turn off the switchable graphics in the bios"

Have you tried turning off the switchable graphics?

---

### Post by baarn on 2011-06-01
nope, not yet... but i dont get the point, i mean i don't have to switch something off i cannot use anyway ;)
i think i miss something there...

will try it tomorrow anyway, don't wanna wreck my computer before going to bed, wont let me sleep.
thanks for your help

---

