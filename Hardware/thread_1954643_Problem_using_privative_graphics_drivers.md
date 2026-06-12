---
title: "Problem using privative graphics drivers"
date: 2012-04-08
forum: Hardware
---

### Post by HaPK_PerCar on 2012-04-08
Hi all,

I've had a concurrent problem. Whenever I try to install and use the privative graphics drivers for my desktop I'm left out with a broken desktop environment, it fails to load.

I was using the embedded graphics chipset from my board so using the open source drivers was fine, I wasn't missing much. But now I recently acquired a Sapphire Radeon HD 6750 so having 3D accelerated graphics would be nice. The embedded chipset was also an ATI one.

What happens is this: I install the privative drivers, they install fine (followed the instructions from [this wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide")) and when I restart the PC it seems to be fine, LightDM loads correctly, but then when I enter the desktop fails to load. I switch to a shell and try to load unity and this is what comes out
```

Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: glXCreateContext failed
Compiz (bailer) - Info: Ensuring a shell for your session
WARNING: no DISPLAY variable set, setting it to :0
```I think OpenGL fails to load somehow so that's what breaks the desktop, but I don't know what causes it.

I have a laptop, with Linux Mint on it, ATI Mobility card, and the same story happens. Also my desktop, with the previous hardware config happened the same thing.

Have been looking in the internet for this problem but there's very little info around.

I hope you can help me here

---

