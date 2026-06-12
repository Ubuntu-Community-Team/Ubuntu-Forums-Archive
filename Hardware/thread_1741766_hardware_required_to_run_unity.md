---
title: "hardware required to run unity"
date: 2011-04-28
forum: Hardware
---

### Post by Ve5ahchoo8ah on 2011-04-28
I've just downloaded and installed 11.04!
No Unity!
it says I don't have "the hardware required to run unity"!
I have a [GeForce 9400 with 1GB dedicated ram graphic card]("http://www.google.com/products/catalog?hl=en&ds=pr&sugexp=gsish&pq=geforce+9400gt&xhr=t&q=geforce+9400gt+1gb&cp=16&client=ubuntu&channel=fs&bav=on.2,or.r_gc.r_pw.&biw=1024&bih=602&um=1&ie=UTF-8&cid=8919769395582150559&sa=X&ei=wJO5TavAIIqGtwf246jeBA&sqi=2&ved=0CGwQ8wIwAQ#")!! (a Dual-core 5300MHz CPU and 4GB ram)
how it's not enough??!!

when I run "/usr/lib/nux/unity_support_test -p" I get:
```

$ /usr/lib/nux/unity_support_test -p  
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

```It's a shame!
Is there anything I can do?!
:confused:

---

### Post by gyussz on 2011-04-28
Have you installed and configured the Proprietary drivers correctly? I'm not sure about the relationship between Unity and the Open Source drivers.

---

### Post by adamcmwilson on 2011-04-29
I installed 11.04 in a VM as a test and got the 'insufficient hardware' error you mentioned.

I then installed 11.04 on my laptop, (Core2Duo 2.8 GHz, 4 Gb RAM, 1GB vid), and got the same error.  I did a system update, still could not enable unity.  I ran the Ubuntu Software Center to install Eclipse, when I was alerted to found proprietary drivers for my video card.

Once the drivers were properly installed, (after a long, slow, download), and a system reboot - voila - Unity desktop.

So this is not necessarily a hardware issue - may be more likely related to drivers, as per gyussz.

---

### Post by SkyWasher on 2011-05-01
typically Virtual Machines don't support 3D acceleration which is required for the unity eye-candy.   Try doing an actually install and then enabling the proprietary driver for your video card and see what results you get.   

-or-

try the live disk, then install/enable  the proprietary drivers for your video card. 

I got the same error until I installed/enabled the proprietary drivers.

---

### Post by Trulyhappy on 2011-06-06
Hi all ! I'm a new user of ubuntu and i don't really know how to install the appropriate drivers ! May someone explain to me what i should do to install those drivers
Thanks:)

---

### Post by mmg666 on 2011-07-20
Maybe I'm wrong but while upgrading ubuntu warns you about "some" proprietary drivers being deactivated which basically means it is, very likely, deactivating your graphics driver alongside with probably some others.

To activate it, you can go to the menu System > Administration > Additional Drivers, you will see your deactivated driver activate it...

---

### Post by eokeefe on 2011-07-21
Using the Administration > Additional Drivers worked for me. Appreciate the help.

---

### Post by G_R_O_N_D on 2011-08-11
I got the same error message when trying to install 11.04 on VMware Player, hosted by Windows 7.

I wanted to install it on a VM so as to try Unity before installing/upgrading my 10.10 laptop.
I didn't want to install alongside Windows because of some horrible experiences doing so a little while back.

Is there any way to ensure that 3D acceleration is enabled via VMware? Or is that just impossible?

I'd really prefer to run from a VM rather than installing proper....


Thanks.

---

### Post by gyussz on 2011-08-11
> **G_R_O_N_D said:**
> 
Is there any way to ensure that 3D acceleration is enabled via VMware? Or is that just impossible?

Thanks.

Not sure about unity and Vmware, but I think you have to install VMware tools (or something like that, it's kinda the same thing as VirtualBox quest additions). Found this with a quick googling: [https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools) 

Hope that helps, I'm not familiar with VMware.

---

### Post by Jnich20 on 2011-08-13
i am having a similar problem in that it says i do not have the hardware to run unity i have an asus-n53sv with a gt540m 1gb ddr3 card so the hardware is there when i go into the additional drivers app it says they are activated but not in use is there a way to activate it through terminal
thanks

---

### Post by n0an on 2011-09-11
I know this is late, but this seems to work. Trying it now!

> [http://www.dtamonline.com/wordpress/2011/04/ubuntu-11-04-unity-on-vmware-fusion-and-virtualbox/](http://www.dtamonline.com/wordpress/2011/04/ubuntu-11-04-unity-on-vmware-fusion-and-virtualbox/)

---

### Post by kevinnorton on 2012-07-19
For what it is worth, I just installed 11.04 on my Vaio VPCSB. Unity was working fine until I activated the ATI driver. After that, I got the message that my hardware did not support Unity. So, after removing the driver and restarting, Unity is back! 
One more possible option.

---

### Post by wildmanne39 on 2012-07-19
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

