---
title: "Nvidia lengency drivers work with compiz?"
date: 2008-07-22
forum: General Help
---

### Post by tommy909808 on 2008-07-22
I used compiz fusion on the same hardware and all but somehow i can't get compiz to work and all with a Nvidia Quadro 2 pro. i tried the 71.xx and th 93.xx. Can anyone help me?

---

### Post by jombeewoof on 2008-07-22
Try the drivers from synaptic.
I got my same hardware working before with 7.10 or something, but couldn't do it with the Nvidia drivers this time. I used the glx-new drivers and it worked like a charm.

---

### Post by tommy909808 on 2008-07-22
kk in xorg.conf do i have the driver set to nvidia or nvidia_new?

---

### Post by jombeewoof on 2008-07-22
> **tommy909808 said:**
> kk in xorg.conf do i have the driver set to nvidia or nvidia_new?

Mine is set to Nvidia, but I didn't change anything after the install, I just rebooted.

---

### Post by Happy_Man on 2008-07-22
Does your card have less than 64 MB of video RAM? If so, then Compiz Fusion won't run on it.

---

### Post by tommy909808 on 2008-07-22
Can it be equal too?:lolflag:

---

### Post by Happy_Man on 2008-07-23
Well, if it's got 64 MB of RAM and is a Geforce 4 or higher, then yes, it'll run. Anything less than a Geforce 4, I think with the possible exception of Geforce 2 MX, won't run Compiz Fusion.

---

### Post by tommy909808 on 2008-07-23
well somehow i got it running on the same graphics card and os ubuntu 8.04... and this is a Nvidia Quadro2 pro 

[http://www.nvidia.com/page/quadro2pro.html](http://www.nvidia.com/page/quadro2pro.html)

---

### Post by overdrank on 2008-07-23
> **tommy909808 said:**
> well somehow i got it running on the same graphics card and os ubuntu 8.04... and this is a Nvidia Quadro2 pro 

[http://www.nvidia.com/page/quadro2pro.html](http://www.nvidia.com/page/quadro2pro.html)

Hi and could you give us some specs on the system? The main thing I am thinking is it a laptop?

---

### Post by tommy909808 on 2008-07-23
ok im getting this in the termainal after i try to start compiz --replace
```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

---

### Post by overdrank on 2008-07-23
> **tommy909808 said:**
> ok im getting this in the termainal after i try to start compiz --replace
```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

Additional question is have you tried the compiz-check from the FAQ's? 
Link in my signature.

---

### Post by tommy909808 on 2008-07-23
Weird posted at the same time! any way i have an old dell with wireless and it isn't a laptop , it's and old pentuim 3 650 desktop with a nvidia quadro2 pro.

---

### Post by tommy909808 on 2008-07-23
```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV15GL [Quadro2 Pro] (rev a4)
 Driver in use:         nvidia
 Rendering method:      Xgl

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [SKIP]
 Checking for non power of two support...          [SKIP]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Xgl on Nvidia chip. 

```

---

### Post by overdrank on 2008-07-23
> **tommy909808 said:**
> Weird posted at the same time! any way i have an old dell with wireless and it isn't a laptop , it's and old pentuim 3 650 desktop with a nvidia quadro2 pro.

Ok are the graphics onboard or is it a additional card? What I am thinking is the memory if it is shared this could be a issue.

---

### Post by tommy909808 on 2008-07-23
what i know is there is no itergrated graphics chip, its a card.

---

