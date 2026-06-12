---
title: "AMD/ATI Help"
date: 2012-09-08
forum: Hardware
---

### Post by jazzmasterkc on 2012-09-08
Hello,

My graphics card is running really slow. I've read up on some things and I see that their is no more support? Here is specs:

ATI Radeon HD 4200
AMD phenom II x4 830
Running ubuntu 12.04
OpenGL 3.3.1..
RandR version 1.3
catalyst control center 2.14
Driver package version 8.96..

Having the propriety fglrx (amd/ati) driver installed makes it run a lot slower so obviously something is not right with card.. also when i try to install the post release update it doesn't install right and informs me of an error.

Help is greatly appreciated

Edit: also saw that it says my graphics card is VESA: RS880 ?

---

### Post by QIII on 2012-09-08
The post release updates version causes problems for many users.  Uninstall it if you haven't

How did you install the proprietary driver?

How do you define "running slowly"?

---

### Post by jazzmasterkc on 2012-09-08
I have a system settings GUI (I think it came with ubuntu cant remember) that has a drivers thing.. and then It showed AMD/ATI driver, with the original one and post one.. And I activated it which downloaded and installed.. is their a better way or something?

Edit: And I meant low frame rate/laggy.. if I had to guess it would be 10-15FPS

---

### Post by QIII on 2012-09-08
The Additional Drivers method you used also fails for some users.  I have no earthy idea why.

Please see the wiki in my signature and look in the section "Using the Ubuntu repository, alternate command line method."

You can change the settings and increase fps using Catalyst Control Center.

---

### Post by jazzmasterkc on 2012-09-08
Ok, and i didn't mean from just playing games.. my entire computer its-self is like that even just typing now it lags behind a lot

---

### Post by jazzmasterkc on 2012-09-08
What do you suggest for running the fastest in all areas with my set up?

Edit1: Just uninstalled it from terminal.. (fglrx) and trying to figure out what steps to take now...

Edit2: saw LIBGL_DEBUG=verbose glxinfo on the page.. I didn't have it installed and now I do :p .. wonder if i'm missing any more packages relating to graphics...

Edit3: after a restart.. pulled up blender can move a object with a scale of 10x 10y with texure and thousands of faces like a boss

---

### Post by QIII on 2012-09-08
The settings you choose in CCC really need to be done by experimentation to find out what works best for what you want.

Are you satisfied that the driver is installed and working properly?

---

### Post by jazzmasterkc on 2012-09-08
Yes works good, but like you said pretty much test things out myself and go from there. I thought installing the fgl stuff would improve it but really cut my graphics performance in half. 

Thanks for your help.

---

