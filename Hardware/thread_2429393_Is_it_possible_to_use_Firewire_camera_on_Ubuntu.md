---
title: "Is it possible to use Firewire camera on Ubuntu"
date: 2019-10-17
forum: Hardware
---

### Post by bundyboy on 2019-10-17
Hello,

I work at school and we have old computer with windows xp, which is connected to microscope which has a digital camera.
Digital camera is connected to computer by firewire connection. camera is Olympus dp25.

But we recently purchased a new computer, and unfortunately the driver of the camera does not support 
newer windows operating systems. So at this moment we can only install windows 10 with VMware, and then install windows xp
to get working camera.

but someone told us that maybe on Ubuntu can camera work, so I dont know which version of Ubuntu you recommend ?

It needs to have support for Firewire for Olympus dp25 camera.

And one other thing, I have read that through the program called Wine, i can install windows program. Is this true ?

that would be great, because then we could use the program from the camera.

I hope you can help me

Thank you

---

### Post by jimmyrus on 2019-10-17
> **bundyboy said:**
> Hello,

I work at school and we have old computer with windows xp, which is connected to microscope which has a digital camera.
Digital camera is connected to computer by firewire connection. camera is Olympus dp25.

But we recently purchased a new computer, and unfortunately the driver of the camera does not support 
newer windows operating systems. So at this moment we can only install windows 10 with VMware, and then install windows xp
to get working camera.

but someone told us that maybe on Ubuntu can camera work, so I dont know which version of Ubuntu you recommend ?

It needs to have support for Firewire for Olympus dp25 camera.

And one other thing, I have read that through the program called Wine, i can install windows program. Is this true ?

that would be great, because then we could use the program from the camera.

I hope you can help me

Thank you
yea, firewire is supported but I haven't used a fw camera in several years. The driver should be in the kernel, and just plugging it in should activate it providing you have a firewire port. always install the latest version and install the cheese application which is probably the easiest to use for testing a video camera

---

### Post by bundyboy on 2019-10-17
> **jimmyrus said:**
> yea, firewire is supported but I haven't used a fw camera in several years. The driver should be in the kernel, and just plugging it in should activate it providing you have a firewire port. always install the latest version and install the cheese application which is probably the easiest to use for testing a video camera

great ! I will try Ubuntu 18.04.3 LTS on [COLOR=#000000][I]VMware. 

[/I][/COLOR][COLOR=#000000]*Also, I have read that through the program called Wine, i can install windows program. Is this true ?*[/COLOR]

[COLOR=#000000]*that would be great, because then we could use the program from the camera.*[/COLOR]

[COLOR=#000000]*Thank you*[/COLOR]

---

### Post by jimmyrus on 2019-10-18
> **bundyboy said:**
> great ! I will try Ubuntu 18.04.3 LTS on [COLOR=#000000][I]VMware. 

[/I][/COLOR][COLOR=#000000]*Also, I have read that through the program called Wine, i can install windows program. Is this true ?*[/COLOR]

[COLOR=#000000]*that would be great, because then we could use the program from the camera.*[/COLOR]

[COLOR=#000000]*Thank you*[/COLOR]
Wine isnt windows. Only some programs work and some only partially work. What is this program that you want to use from windows because there are probably several linux programs
that do what your after. And if your working with vmware be careful since the usb and other ports need to be shared to the host os first. anytime you virtualize you add a layer. And why are
you using ubuntu 18 when 19 is the latest after being told to always use the latest version?  you can reinstall windows later if you want to, but I'd do a real installation onto the new computer
since its free to try and eliminates a lot of snags you could have later.

---

### Post by kurt18947 on 2019-10-18
> **jimmyrus said:**
> Wine isnt windows. Only some programs work and some only partially work. What is this program that you want to use from windows because there are probably several linux programs
that do what your after. And if your working with vmware be careful since the usb and other ports need to be shared to the host os first. anytime you virtualize you add a layer. [B]And why are
you using ubuntu 18 when 19 is the latest after being told to always use the latest version?[/B]  you can reinstall windows later if you want to, but I'd do a real installation onto the new computer
since its free to try and eliminates a lot of snags you could have later.

Ubuntu 19.x are not LTS so limited time support. I would not use a non-LTS version for 'real work' if I could avoid it.

---

### Post by bundyboy on 2019-10-20
> **jimmyrus said:**
> Wine isnt windows. Only some programs work and some only partially work. What is this program that you want to use from windows because there are probably several linux programs
that do what your after. And if your working with vmware be careful since the usb and other ports need to be shared to the host os first. anytime you virtualize you add a layer. And why are
you using ubuntu 18 when 19 is the latest after being told to always use the latest version?  you can reinstall windows later if you want to, but I'd do a real installation onto the new computer
since its free to try and eliminates a lot of snags you could have later.

We at school recently purchased a new computer, and installed Win 10. But unfortunately our microscope which has a digital camera Olympus DP25 does not work.


to be more precise, when installing the driver for the camera, it simply nothing happens after the installation.


therefore we can assume that the driver is not compatible with Win 10.

so i was thinking of installing ubuntu via virtual machine, but I'm not sure if firewire will work on virtual machine ?

or in the worst case to install directly ubuntu.

but my question is, will ubuntu have driver for Olympus DP25 firewire camera ?

if yes, then other thing i need to try is camera program by Wine ?

> **kurt18947 said:**
> Ubuntu 19.x are not LTS so limited time support. I would not use a non-LTS version for 'real work' if I could avoid it.

ok. thank you :)

---

### Post by jimmyrus on 2019-10-21
> **bundyboy said:**
> We at school recently purchased a new computer, and installed Win 10. But unfortunately our microscope which has a digital camera Olympus DP25 does not work.


to be more precise, when installing the driver for the camera, it simply nothing happens after the installation.


therefore we can assume that the driver is not compatible with Win 10.

so i was thinking of installing ubuntu via virtual machine, but I'm not sure if firewire will work on virtual machine ?

or in the worst case to install directly ubuntu.

but my question is, will ubuntu have driver for Olympus DP25 firewire camera ?

if yes, then other thing i need to try is camera program by Wine ?



ok. thank you :)
there some reason you just asked the same question again after it was already answered? I told you that firewire cameras have been supported for a while and that you should just have to plug it in and even gave you the name of a program to try. You shouldn't need a driver or anything else, unless the camera has some incredibly odd features. Like you were told before you can load ubuntu up and just try it its free. And like you were told before  you can always just put windows back on the new pc if it doesnt work so whats the problem? And even though that thing only says it supports up to windowsxp, you can run their software in compatability mode just fine.
 
And there may be a linux program that works [https://micro-manager.org/wiki/Device_Support](https://micro-manager.org/wiki/Device_Support)

---

