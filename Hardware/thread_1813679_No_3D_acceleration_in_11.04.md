---
title: "No 3D acceleration in 11.04"
date: 2011-07-28
forum: Hardware
---

### Post by Blitzskee on 2011-07-28
So I have 11.04 installed on a Dell Inspiron 15R laptop 525m Nvidia with Optimus

After installing the OS and booting ubuntu for the first time when I went to login I was presented with this message:

> It seems that you do not have the hardware required to run Unity.  Please choose Ubuntu Classic at the login screen and you will be using the traditional environment.

This was my first hint that 3D acceleration was not in use.

Under Additional drivers it tells me the Nvidia driver is selected and displays a message at the bottom of the window saying:  This device is activated but not in use (I think).

Since then I have installed bumblebee with no difference (I think..)

Someone suggested I run this code to tell me if I have 3D acceleration:

```
glxinfo | grep dire
```

It gave me this output:

> Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".

Does anyone know how I can get 3D acceleration to work?

---

### Post by Blitzskee on 2011-07-28
Additional info, I ran two codes I found in other threads not sure what they do but they might be of use to someone trying to help

```
/usr/lib/nux/unity_support_test -p
```

> Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context

```
sudo lshw -c video
```

> *-display UNCLAIMED     
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f6000000-f607ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:58 memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64)


---

### Post by mastablasta on 2011-07-28
> **Blitzskee said:**
> So I have 11.04 installed on a Dell Inspiron 15R laptop 525m Nvidia with Optimus

 
But Optimus (from what i read) is not supported in Ubuntu (and linux in general) and causes problems. you should have gone with ATI card.

---

### Post by Blitzskee on 2011-07-28
Well....I decided to use Ubuntu AFTER getting the laptop lol, so I don't have much choice in the matter.

From what I have gathered from other people running optimus is that theirs is running fine except they have poor battery management.  As far as I can tell they are not having the same 3D acceleration problems I am getting.

---

### Post by Blitzskee on 2011-07-28
.

---

### Post by khelben1979 on 2011-07-29
If you get [nouveau]("http://nouveau.freedesktop.org/wiki/") working, you will get working 3D acceleration. It's the nVidia open source video driver.
[nouveau Wiki - FAQ]("http://nouveau.freedesktop.org/wiki/FAQ").

Maybe it can help you begin having a look at the possibilites.

---

### Post by Blitzskee on 2011-07-30
> **khelben1979 said:**
> If you get [nouveau]("http://nouveau.freedesktop.org/wiki/") working, you will get working 3D acceleration. It's the nVidia open source video driver.
[nouveau Wiki - FAQ]("http://nouveau.freedesktop.org/wiki/FAQ").

Maybe it can help you begin having a look at the possibilites.

Well I fixed it...not sure how but I removed the NVIDIA driver from Additional drivers, then deleted xorg.conf and installed the updates released today.

Then after I rebooted I had 3D acceleration

Used the command: "sudo lshw -c video" and the output was NOW this:

>   *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f6000000-f607ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:57 memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64)


Thanks everyone for your input!

---

