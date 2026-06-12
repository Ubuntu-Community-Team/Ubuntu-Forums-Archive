---
title: "Mesa/OpenGL"
date: 2008-11-06
forum: General Help
---

### Post by zuheyr on 2008-11-06
Hello,

I am using 64 bit 8.10 desktop.

I use a visualization package Tecplot that uses either Mesa or OpenGL alternatives, OpenGL being the preferred one, faster than Mesa according to Tecplot.

In Ubuntu there is an OpenGL "imitiation ??" called Mesa that confuses me.

I am using it and it works but I am not sure I understand this, also is this the best I can do?

Thanks for reading, kind regards,
Zuheyr

---

### Post by Yellow Pasque on 2008-11-06
It depends on your video card and driver. 
```
sudo lshw -C display
```

"Mesa" is an open-source implementation, not an imitation, of OpenGL. Some proprietary drivers (i.e. Nvidia and ATI Catalyst/fglrx) use different implementations of OpenGL that often perform better, but using proprietary drivers can have its disadvantages (bugs).

Mesa has the ability to use DRI/hardware acceleration if the driver allows it. The worst-case scenario is when your video driver doesn't support DRI and all the rendering is done with the CPU ("software Mesa").

---

### Post by zuheyr on 2008-11-06
Thank you very much for this comprehensive reply.
If you excuse me asking a silly question: How do I see if the driver supports DRI? My graphic card is Intel G33. There is a driver download is available for Linux but I wanted to check with Ubuntu friends here first.

Many thanks, regards
Zuheyr

---

### Post by Yellow Pasque on 2008-11-06
The intel driver is capable of using DRI.
The best way to check this is with:
```
glxinfo | grep direct
```

If that reports no, we'll figure out why.

---

### Post by zuheyr on 2008-11-06
Thank you Temujin.

I am at work now, this evening I will test that. I appreciated your help. 

Kind regards, Zuheyr

---

### Post by zuheyr on 2008-11-06
Hi Temujin,

The command you taught me is affirmative:

~$ sudo lshw -C display
[sudo] password for zuheyr:
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
~$ glxinfo | grep direct
direct rendering: Yes

Thank you very much, I guess this is the best I can do.
Kind regards, Zuheyr

---

### Post by Yellow Pasque on 2008-11-06
> Thank you very much, I guess this is the best I can do.
You're welcome. That is the best you can do for now, though Intel and X.org devs are working on some interesting stuff (GEM, kernel mode-setting, and EXA 2D-accel improvements). Hopefully, the intel 2.5.0 driver will be available from the repos in the near future.

---

### Post by zuheyr on 2008-11-07
Thank you very much Temujin. Best regards, Zuheyr

---

### Post by forsumitonly on 2008-11-15
Hey zuheyr,

I don't know if you solved your problem or not, but I was wondering if you can help me, just like you I am using Tecplot360, my machine is an AMD-64 bit and I am running Ubuntu 8.10. 
The problem is that when ever I open data in TecPlot it image doesn't stay in the plotting area I have to keep the mouse button clicked to see any image othe wise the area becomes grey.
The driver I am having is fglrx.

Would you have any idea??

Thanks,
Sumit

---

### Post by forsumitonly on 2008-11-15
Just a little more detail

*-display               
       description: VGA compatible controller
       product: RS780M/RS780MN [Radeon HD 3200 Graphics]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx

---

### Post by Yellow Pasque on 2008-11-15
> The problem is that when ever I open data in TecPlot it image doesn't stay in the plotting area I have to keep the mouse button clicked to see any image othe wise the area becomes grey.
The driver I am having is fglrx.

It sounds like a bug in fglrx (fglrx isn't renowned for stability/accuracy). Unfortunately, fglrx is the only driver that does video hardware acceleration for the 780 IGP right now.

---

### Post by zuheyr on 2008-11-15
Hi,

Yes, I know. You have to disable the graphics acceleration.
In the main toolbar:

1) System --> Preferences --> Appearance --> Visual effects 
2) Click on None

I am of course not knowledgeable on the matter, I just discovered it by looking around, but this will help.

Another Tecplot help, if you are not happy with the fonts, as I was not, it was not easy to read, go to tecplot installation directory  

1)cd app-defaults
2) and edit the file (I only have one file Tecplot113

/opt/tec_360/app-defaults$ ls
Tecplot113  Tecplot113~

3) And disable the "new look" by commenting each line with "!" and enable the "old look" by uncomemmenting (remove the leading "!"s).

You may find it much easier to read and work with Tecplot.

Hope this helps, as they say, 

Good luck, greetings, Zuheyr

---

### Post by forsumitonly on 2008-11-15
Hey Zuheyr,

I jumped up and screamed ....:)

Thanks a lot for the prompt reply and solving my problem.

Greetings,
Sumit

---

### Post by zuheyr on 2008-11-15
Hi Sumit,

I thank *you* very much!! 

This is the very first time I helped someone in any Ubuntu forum.
I received zillions.   

It feels great!

Have fun, Regards, Zuheyr

---

