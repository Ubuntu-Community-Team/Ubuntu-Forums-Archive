---
title: "Install a discrete video card to use nouveau drivers to an already installed system."
date: 2016-08-30
forum: Hardware
---

### Post by mikodo on 2016-08-30
Hello everyone,

This is not a problem as such so, I hope this is the correct forum to ask this question.

I am wanting to install a PCI-E nVidia video card, to my Desktop Intel machine. I have Intel integrated graphics now with no HD graphics and no discrete card. (2007 technology).

I have two instances of Xubuntu 16.04 installed and I _do not want_ to re-install to swap in the discrete video card. I am quite sure from reading of others' experience with the card, the nouveau drivers for that card will work for these installs.

Question:

If in Synaptic, on the section on Software & Updates if, I keep as I have now, in the section for Proprietary drivers _unchecked_, will my system once the card is placed in, try to boot using the _nouveau_ drivers automatically to my installed 16.04 OS's?

Anything else I should do for this to happen?


I don't have time to re-install now but, am feeling pressured to get this card in, so I can test upcoming MIR changes that most likely will need the graphics of a nVidia card for me to test them with. By installing along side  the 16.04 installs upcoming releases as they become available. 

Thanks.

```
glxinfo | grep 'version'
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
    Max core profile version: 0.0
    Max compat profile version: 1.4
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 2.0
OpenGL version string: 1.4 Mesa 11.2.0
OpenGL ES profile version string: OpenGL ES 2.0 Mesa 11.2.0
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16




```

---

### Post by mikodo on 2016-09-01
Any sage words of advice?

I need to attend to my day so, if anyone responds, I will be away from my computer and not be available to respond immediately.

Thank you.

---

### Post by Yellow Pasque on 2016-09-01
If you didn't have any proprietary drivers installed (and no customized /etc/X11/xorg.conf file), it should be "plug 'n play" for all except most recent Nvidia card (Pascal or Maxwell-based GPU's).

---

### Post by mikodo on 2016-09-01
> **Temüjin said:**
>  - What you wrote - 

Thank you! 

The nVidia Card is an older one that today, manufactures of Linux/Ubuntu boxes are using for lower end graphics. I will look to see what "Pascal or Maxwell-based GPU's" are, and determine if the one I want is in one of those categories. My guess it is not, as it is not a 'newer' nVidia card, as you spoke of. I have not  customized my systems', /etc/X11/xorg.conf files personally, in any way.


Take Care!

---

