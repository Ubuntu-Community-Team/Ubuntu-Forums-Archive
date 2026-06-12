---
title: "My Radeon HD hardware is not supported yet? Radeon AMD Radeon HD 7450A"
date: 2012-03-29
forum: Hardware
---

### Post by thomasw81 on 2012-03-29
First I would like to say that I have been using Ubuntu since 10.04 for a few years now, with great satisfaction.

But I am having trouble installing ubuntu on my new pc, specs below:

HP TouchSmart 520-1100ed desktop pc (H1E89EA)
Intel® Core(TM) i3-2120 (3,3 GHz 3 MB L3 cache )
Intel H61
AMD Radeon HD 7450A (1 GB gereserveerd)

I tried different approaches:

Installing 10.04 results in a working system, but without display driver. I tried out the radeonhd and ati drivers bij installing them with apt-get. Also managed to install the proprietory driver (12-2xxx) from amd.com, but my hardware is nog recognized by the system. Also adding gits repositories does update the needed drivers and packages, but to no avail. I found out later that for this proprietory driver to work, I need Ubuntu 11.10. 

Ubuntu 11.10 installation cd program starts fine, but when selecting any option from the install menu (try ubuntu, install ubuntu etc) the screen shows pretty colours in succession: red green blue black white. That is all, the installer does not load, even after an extended time.

So my conclusion is that my hardware is not yet supported. My model is not listed in the xorg supported hardware page, found here: [http://www.x.org/archive/X11R7.5/doc/man/man4/radeonhd.4.html#toc3](http://www.x.org/archive/X11R7.5/doc/man/man4/radeonhd.4.html#toc3)

I am almost concluding to just start using the Winblows 7 ultimate home edition for now, until my hardware is supported and I can try again. But by posting this information I hope someone might help me along or at least show me an unknown way to getting ubuntu to run on my new computer.

Many thanks in advance!

---

### Post by mastablasta on 2012-03-29
> **thomasw81 said:**
>  
Ubuntu 11.10 installation cd program starts fine, but when selecting any option from the install menu (try ubuntu, install ubuntu etc) the screen shows pretty colours in succession: red green blue black white. That is all, the installer does not load, even after an extended time.
 
Use boot options on boto menu (F6 i think) and select  nomodeset. This should allow you to boot into the OS and then install it. After it is installed you can install the proprietary drivers.
 
if that doesn't work try another boot option
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
[/QUOTE]
So my conclusion is that my hardware is not yet supported. My model is not listed in the xorg supported hardware page, found here: [http://www.x.org/archive/X11R7.5/doc/man/man4/radeonhd.4.html#toc3](http://www.x.org/archive/X11R7.5/doc/man/man4/radeonhd.4.html#toc3)
[/QUOTE]
 
this is for opensource drivers where it might not be fully supported. however you should get at least basic vesa mode and be able to install proprietary drivers.
 
you need 11.10 because it has higher kernel. in linux drivers are part of kernel, so newer kernel, newe drivers. you could maybe also give 12.04 beta a try. i read it is quite stable already. comes out next month.

---

### Post by Mark Phelps on 2012-03-29
> **mastablasta said:**
> .. you could maybe also give 12.04 beta a try. i read it is quite stable already. comes out next month.
What I read, from Canonical's own Release Notes (for Beta 1 -- haven't seen the Beta 2 yet), is that it has "issues" and is only to be used by Developer's and Testers.

That said, if the OP wants to experiment with a Live USB (I think it's still too large to fit on a CD), then they should have at it!

But, upgrading at this point, especially since Canonical has YET to provide any decent roll-back capability, could be disastrous.

---

### Post by Yellow Pasque on 2012-03-29
> I found out later that for this proprietary driver to work, I need Ubuntu 11.10.
You can install Catalyst 12-3 on Lucid and it may have added support for your GPU. [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)

---

### Post by mastablasta on 2012-03-30
> **Mark Phelps said:**
> What I read, from Canonical's own Release Notes (for Beta 1 -- haven't seen the Beta 2 yet), is that it has "issues" and is only to be used by Developer's and Testers.
 .
i ment beta 2 that just came out. 
 
you are correct it should be tried live session first. however (especially KDE) seems to be quite stable accoridng to some reports. I owuld give live a try and see if it works a bit better.
 
[https://lists.ubuntu.com/archives/ubuntu-announce/2012-March/000157.html](https://lists.ubuntu.com/archives/ubuntu-announce/2012-March/000157.html)

---

### Post by thomasw81 on 2012-04-01
Hello everyone. May thanks for the replies. I also got a lot of help from Glosoli on IRC (#linux-ati). He set me up with 12.04 and everything is working out of the box now, except the touchscreen.

Aparently the pc is not fitted with an Ati card, but integrated Intel video graphics driver. Wich is supported in 12.04, but not in older versions.

Dont I feel stupid! I got the wrong specs. My system is a HP TouchSmart 520-1000nl.

Anyway, I think this thread can be closed. I will see if anyone here got the touchscreen working.

---

