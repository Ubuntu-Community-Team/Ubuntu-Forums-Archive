---
title: "Desktop Effects Could Not Be Enabled - S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
date: 2008-08-17
forum: General Help
---

### Post by Autodidactic on 2008-08-17
Hi,
I've searched high and low for a solution but I just can't find an answer to my problem.

I installed Ubuntu 8.04 using Wubi on an HP Pavilion zt1175 laptop with an S3 Inc. VT8375 [ProSavage8 KM266/KL266] video card. When I try to enable visual effects (I realllly want to get compiz running on this box) I get "Desktop Effects Could Not Be Enabled."

Over the last couple days of trying to fix this problem I have tried many of the suggestions recommended to others who have had the same issue but so far my problem persists.

Can anyone help me? 

Thanks in advance...

:)

Edit:
Here is the results that I get when I run Compiz-Check;
./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         S3 Inc. VT8375 [ProSavage8 KM266/KL266]
 Driver in use:         savage
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

### Post by fragos on 2008-08-18
Compiz only works with video cards that have 3D rendering and I don't know if yours does. Run "glxinfo |grep rendering" to see if the result is "direct rendering: Yes".

---

### Post by Autodidactic on 2008-08-18
Hi Fragos, thanks for the help. I ran "glxinfo |grep rendering" and here are the results:
```
sean@sean-laptop:~$ glxinfo |grep rendering
direct rendering: Yes

```

---

### Post by fragos on 2008-08-19
So you do have a driver that supports 3D rendering. A ways back the Intel driver had some issues with Compiz even though 3D acceleration worked correctly. At that time Compiz blacklisted the Intel graphics. Perhaps your 3D card is blacklisted for some reason. That's all I can think of. Try Googling "Compiz+{graphics chipset}".

---

### Post by Autodidactic on 2008-08-19
Thanks Fragos; got some reading to do - Google came back with 353 hits. I will see what I can learn from there and post back.

Thanks for the advice.

---

### Post by sandycreek91 on 2009-02-23
Did you find a solution?  I'm experiencing the same behavior.

---

### Post by Autodidactic on 2009-02-24
Nah, turns out this hardware just can't handle it. I've long given up on having sweet eye candy on this box. 

Hopefully I'll be updating soon and my next laptop will i'm sure handle things fine.

Sorry.

---

