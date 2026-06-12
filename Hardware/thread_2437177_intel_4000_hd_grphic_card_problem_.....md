---
title: "intel 4000 hd grphic card problem ...."
date: 2020-02-19
forum: Hardware
---

### Post by hu016865 on 2020-02-19
i have a sony vaio 1521 with intel hd 4000 vga
after install ubuntu 19.10 in details i see graphic as " I_ntel® Ivybridge Mobile_ "
with command lspci i see :
> VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)


with command lshw -c video :

> SVF1521BYGB:~$ lshw -c videoWARNING: you should run this program as super-user.
  *-display                 
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:32 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:3000(size=64) memory:c0000-dffff




how can i detect my vga to ubuntu 19.10 ?

---

### Post by CelticWarrior on 2020-02-19
The card is detected.

What is the actual problem you're trying to solve?

---

### Post by hu016865 on 2020-02-19
i test linux mint and in details i see graphic card was : intel 4000 hd
and icons text was normal.
why in ubuntu i see :  Intel® Ivybridge Mobile?

---

### Post by hu016865 on 2020-02-19
icons size and text in chrome and other programs like filezilla are large...

---

### Post by CelticWarrior on 2020-02-19
The name doesn't matter and has nothing to do with the icons...

First check if the resolution matches the monitor's native resolution. If it' s correct then you can adjust the icons size or scaling.

---

### Post by Yellow Pasque on 2020-02-20
> **hu016865 said:**
> i test linux mint and in details i see graphic card was : intel 4000 hd
why in ubuntu i see :  Intel® Ivybridge Mobile?

Probably because Mint is getting the information from a different command. My guess is that it's looking at OpenGL renderer string from:
```
glxinfo -B
```

---

### Post by hu016865 on 2020-02-21
this command dont work in ubuntu 19.10 

> Command 'glxinfo' not found, but can be installed with:

sudo apt install mesa-utils

---

### Post by mörgæs on 2020-02-23
What was your next step after reading that message?

---

### Post by hu016865 on 2020-02-26
i am new in linux and i cant find way to slove this problem.
in windows 10 or 7 icons fonts was very smaller than ubuntu,
i installed chrome and in chrome tabs and fonts in tabs are very big.
in firefox tabs and font s tabs are 10-15% smaller than chrome.
in linux mint fonts icons was very smaller than ubuntu.

---

### Post by Yellow Pasque on 2020-02-26
Good luck with that. I don't have anything else to offer and I'm leaving this thread to protect my sanity.

---

### Post by mastablasta on 2020-02-27
size can mean different resolution is set. you still didn't answer what happens when you copy and paste the commands you were given. 
```
[COLOR=#000000]sudo apt install mesa-utils[/COLOR]
```

type in your password when asked and then press enter.

then 
```
[COLOR=#000000]glxinfo -B[/COLOR]
```

then copy the result and paste it back using code tags (the # icon in forums advanced answer)

i am still not sure what the issue is. you want smaller letters? as soon as we find out the report, we can help. it can be that letters are set too big or that resolution is simply set too small.

---

### Post by hu016865 on 2020-02-27
> **Yellow Pasque said:**
> Good luck with that. I don't have anything else to offer and I'm leaving this thread to protect my sanity.

tnx for your help....

---

### Post by hu016865 on 2020-02-27
> **mastablasta said:**
> size can mean different resolution is set. you still didn't answer what happens when you copy and paste the commands you were given. 
```
[COLOR=#000000]sudo apt install mesa-utils[/COLOR]
```

type in your password when asked and then press enter.

then 
```
[COLOR=#000000]glxinfo -B[/COLOR]
```

then copy the result and paste it back using code tags (the # icon in forums advanced answer)

i am still not sure what the issue is. you want smaller letters? as soon as we find out the report, we can help. it can be that letters are set too big or that resolution is simply set too small.

i do that..

> SVF1521BYGB:~$ glxinfo -Bname of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Intel Open Source Technology Center (0x8086)
    Device: Mesa DRI Intel(R) Ivybridge Mobile  (0x166)
    Version: 19.2.8
    Accelerated: yes
    Video memory: 1536MB
    Unified memory: yes
    Preferred profile: core (0x1)
    Max core profile version: 4.2
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.0
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL core profile version string: 4.2 (Core Profile) Mesa 19.2.8
OpenGL core profile shading language version string: 4.20
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile


OpenGL version string: 3.0 Mesa 19.2.8
OpenGL shading language version string: 1.30
OpenGL context flags: (none)


OpenGL ES profile version string: OpenGL ES 3.0 Mesa 19.2.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00

---

### Post by mastablasta on 2020-02-28
so this shows us all seems to be installed and working well.

now for the issue of small icons& text. in system settings (i don't know where exactly this is in Ubuntu since i use Kubuntu) there should be settings for screen. and in there you should be able to set resolution. higher resolution  will make everything look smaller and more crisp /clear at the same time. 

Q: what is the maximum resolution your screen supports? what is the maximum shown in the settings? if you screen supports higher resolution than the one available in settings then we have some more work to do.

then there should also be setting for fonts, where you can set default system font size. so you can increase that to get bigger letters for example. 

more on resolution here: [https://help.ubuntu.com/stable/ubuntu-help/look-resolution.html.en](https://help.ubuntu.com/stable/ubuntu-help/look-resolution.html.en)
and for the font size here: [https://vitux.com/how-to-change-text-size-in-ubuntu/](https://vitux.com/how-to-change-text-size-in-ubuntu/)


I prefer Kubuntu because all these settings are out in the open and easy to find. or maybe i am just too used to old windows interface.

---

