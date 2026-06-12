---
title: "Compiz on Ubuntu 8.04"
date: 2008-07-31
forum: General Help
---

### Post by lawksalih on 2008-07-31
Hi-

I have installed Ubuntu 8.04 on an IBM T40 laptop and I wanted to install Compiz as well.  However, I cannot seem to get Compiz to work.  

This is what I have done so far:  I went to this website to check my compiz, [http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check) and here's the result:

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV350 AR [Radeon 9600]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

However, when I follow the instruction on this website, I get the following error:

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 [COLOR="Red"]Checking for hardware/setup problems...           [FAIL][/COLOR]

There has been (at least) one error detected with your setup:
 Error: Laptop using radeon driver. 

I dug a little deeper and people recommended downloading EncyNG and I did and EnvyNG tells me this:

EnvyNG Version 1.1.1
Ubuntu Hardy 32Bit
Your graphic card has been detected as ATI mobility  / Radeon 9000
Your graphic card is supported by the legacy driver
EnvyNG Error:  ATI's legacy driver  does not support your operating system.

So please help me if you have encountered this issue before or know of a solution.

Best, 

Lawk Salih

---

