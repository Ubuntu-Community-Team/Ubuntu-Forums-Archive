---
title: "Unity not working with AMD Phenom II x6 1055T processor"
date: 2011-08-10
forum: Hardware
---

### Post by Rutilus on 2011-08-10
It's a Ubuntu 11.04 AMD64 desktop install.

Ubuntu Classic works.

Command ```
usr/lib/nux/unity_support_test -p
``` gives:

```
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no
```

The day before this happened, I used the same CD to install successfully Ubuntu 11.04 and Unity on my old machine bought in 2006 (AMD Turion 64 Mobile Technology ML-34 processor), so imagine my surprise when Unity wouldn't run on my partner's new machine bought in 2010, hence this thread.

Does anyone have any suggestions of what I can try?

---

### Post by Rutilus on 2011-08-12
To provide more information:

I'm using (or trying to) this page of Unity graphics hardware requirements:

wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements

My video card is GeForce 240 which is also a 2010 product.

I checked, using command lshw, that the cpu and video card I believe are in the computer are the ones in the computer.

I'm mystified. Would you expect Unity to work with my hardware, in which case the parts are faulty, or what can I do?

---

### Post by .... on 2011-08-12
The nvidia video driver isn't installed properly. Are you trying to use the proprietary nvidia driver or the open-source nouveau driver?

---

### Post by Rutilus on 2011-08-13
Nouveau is the answer that I discovered by running System - Administration - System Testing and getting, among the responses:

```

compiz_check  PASSED  Gathering information about your system... Distribution: Ubuntu 11.04 Desktop environment: GNOME Graphics chip: nVidia Corporation GT215 [GeForce GT 240] (rev a2) Driver in use: nouveau Rendering method: AIGLX Checking if it's possible to run Compiz on your system... Checking for texture_from_pixmap... [SKIP] Checking for non power of two support... [SKIP] Checking for composite extension... [ OK ] Checking for FBConfig... [SKIP] Checking for hardware/setup problems... [WARN] Something potential problematic has been detected with your setup: Warning: Detected driver is not on the whitelist. Would you like to know more? (Y/n)

```

I didn't see where to answer the "Y/n" at the end of that message so I don't know more.

Another answer would be "whatever driver got installed from the Ubuntu install disk". I'm a newbie to installing a driver if that's what's required.

Again any help would be appreciated.

---

### Post by Rutilus on 2011-09-01
This post is for anyone who finds this thread looking to solve the same or a similar issue.

I was unable to resolve this matter with the information helpfully provided so I decided to try Linux Mint 11 and it's worked for nearly a week on both my and my partner's computers. Linux Mint 11 is similar to, and indeed it's based on, Ubuntu 11.04.

---

### Post by coffeecat on 2011-09-01
@Rutilus, the answer to your original question is simply answered and the fix is equally simple. Indeed, .... was putting you on the right line.

The default nouveau driver for nvidia cards that comes with 11.04 is not quite capable of running the 3d acceleration that is needed for the Unity desktop - Unity is a compiz plugin. Classic gnome doesn't need 3d acceleration **unless** you want the gee-whiz compiz effects. Ditto for Mint 11. You need the proprietary nvidia driver or an experimental plugin if you have a nvidia card and want compiz.

My guess is that the older AMD Turion machine is using Intel or ATI graphics for which you will get 3d out of the box (for most Intel and ATI cards) with the default open source driver for those cards.

The fix for 11.04 installed to the machine with the nvidia card is to install the proprietary nvidia driver or the experimental plugin for the nouveau driver. You can do this from the Additional Drivers utility.

---

