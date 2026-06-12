---
title: "Is ubuntu using my graphics card?"
date: 2008-08-08
forum: General Help
---

### Post by mahela007 on 2008-08-08
How can I see if ubuntu is using my graphics card? or more specifically if ti recognizes it?

---

### Post by iaculallad on 2008-08-08
> **mahela007 said:**
> How can I see if ubuntu is using my graphics card? or more specifically if ti recognizes it?

On your terminal:

```
lspci | grep VGA
```

---

### Post by zipperback on 2008-08-08
> **mahela007 said:**
> How can I see if ubuntu is using my graphics card? or more specifically if ti recognizes it?

You can see what is being recognized pretty easily.

Open a terminal window with Applications -> Accessories -> Terminal

and then issue the following.

```


lspci


```

You can also see your usb hardware with.

```

lsusb

```

Hope this helps you.

- zipperback
:popcorn:

---

### Post by Mgiacchetti on 2008-08-08
if its an Nvidia card, go System > Administration > Hardware Drivers.
If you are supposed to be using a proprietary driver, it will show up here, if the box isn't checked, your not using it.

---

### Post by mahela007 on 2008-08-08
no. there is nothing listed in the drivers window. it says my system is not using any proprietary drivers

---

### Post by Sycron on 2008-08-08
If you type ```
glxgears
``` and you have over 600fps your video device  may work properly. Did the 
```
lspci | grep VGA 
```
worked ?

---

### Post by jocko on 2008-08-08
If you want us to help you figuring out if you use the correct drivers, it would help if you told us what graphics card you have.
What's the output of this command:
```
lspci | grep VGA
```
That will tell you what graphics card you have.
This is a command that will tell you which driver is used:
```
grep driver /var/log/Xorg.0.log
```

---

### Post by mahela007 on 2008-08-08
I'm still relatively new to linux so I don't know what any of this means.
heres the output of both these commends
```
mahela007@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
mahela007@ubuntu:~$ grep driver /var/log/Xorg.0.log
    X.Org XInput driver : 2.0
(==) Matched ati for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
    ABI class: X.Org XInput driver, version 2.0
    ABI class: X.Org XInput driver, version 2.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32

```

---

### Post by jocko on 2008-08-08
The lspci tells you that you have an ATI Radeon 7000 graphics card, and according to the log it is using the "radeon" driver, which is the only driver which supports that card.
So you are fine, Ubuntu is using your card.

---

