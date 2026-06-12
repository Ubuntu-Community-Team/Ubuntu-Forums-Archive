---
title: "Asus A4 Fan never stops"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by keplero on 2006-06-03
Hi to all,
I hope you can help me. When I'm running Ubuntu (now with the Dapper LTS, but previously with other versions) a fan inside my laptop never stops running. It is **not the cpu fan** because it starts correctly when necessary, so It should be another of them; it is very noisy, it reduce my battery lifetime, and maybe also my laptop lifetime :shock:  
Obviously under WindowsXP I don't have this problem. :???:

---

### Post by lucianodenti on 2006-06-03
I have the same problem with my Asus A4G.
Problably the fan that never stops is Video Card Fan (I have an ATI 9700).
I installed the ATI proprietary 'fglrx' driver and I solved the problem.

[https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI]("https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI")

---

### Post by keplero on 2006-06-03
[QUOTE=lucianodenti]I have the same problem with my Asus A4G.
Problably the fan that never stops is Video Card Fan (I have an ATI 9700).
I installed the ATI proprietary 'fglrx' driver and I solved the problem.

[https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI]("https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI")[/QUOTE]

Thank you very much! I have the same laptop, an Asus A4G, so I solved the problem with the link you suggested to me. :D

---

### Post by lucascr on 2006-06-07
I have an Asus laptop with the same card and with the same problems using the ubuntu dapper's driver: no accelleration (as in Breezy), no hibernate (but I had in Breezy) and the fan always running.
Following the the guide at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide"), which is almost the same the guide you suggested, I was able to stop the fan and get hibernate working, but I still have non 3D accelleration:
```

> fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```
One thing I noticed is that in /etc/X11/xorg.conf I have:
```

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "ati"
	VideoRam    64000
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

```
Why there are two devices? And why the first has "ati" instead of "fglrx"?

Overall I solved the two main problems, so I could say to be happy for now. :) 
Ciao,
Luca

---

### Post by Patsoe on 2006-06-07
> Why there are two devices? And why the first has "ati" instead of "fglrx"?

You can leave multiple devices in your xorg.conf - the relevant one is the one referred to in the Screen sections. This means you can specify multiple graphics cards and drivers and attach screens to different ones...

The "ati" one is the default. When you installed "fglrx" that didn't remove the default device. This is normal.

---

### Post by Yoeri on 2006-06-07
Glad to see some other people with an Asus A4 ...
I had exactly the same problems ... in Breezer I got it to work but then I experienced artifacts.

In Dapper all the problems are solved when you indeed install the ATI drivers as stated in a previous post by lucianodenti

I DO have the same problem as lucascr. 'fgrlxinfo' also gives me 
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

A bit off-topic but i'm curious:
Did anyone succeeded in connecting to a network through the built-in wifi card ?

---

### Post by arkangel on 2006-06-08
Hi  ubuntians 

I have an issue  with dapper after installing it  on my asus a6va  ,  the baterry life  was bad, the fan never stops  and  it was annoying , (in brezy all was perfect) then  I notice that the only difference  was the kernel  in version  386   to 686  so  i removed the kernel  2.6.15-686  and installed the  2.6.15-386  (you can do it throught synaptic  it is not that  hard  )  but you should  be sure to edit the menu.lst in /boot/grub/ to point to your new image  and  i am  back in the nice silent previous state but in dapper  :)

 I thought  the 686  will have a better  energy administration and  faster response in the cpu stepping  ,  well this was what i read ,  any explanation ?

about  the fglrx   issue   i  installed the  driver from   i tried to do it  canonically (ie generating  the deb file as in the wikihttp://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide ) 
but it was always updated  by the system (and then  the mesa driver installed again and again )
so i installed according to  the ati  website  , just run your  ./ati-driver-installer-8.25.18-x86.run file as root  and it worked perfect for me  :)  no more mesa   8)

---

### Post by ltmon on 2006-06-08
[QUOTE=arkangel]Hi  ubuntians 

I have an issue  with dapper after installing it  on my asus a6va  ,  the baterry life  was bad, the fan never stops  and  it was annoying , (in brezy all was perfect) then  I notice that the only difference  was the kernel  in version  386   to 686  so  i removed the kernel  2.6.15-686  and installed the  2.6.15-386  (you can do it throught synaptic  it is not that  hard  )  but you should  be sure to edit the menu.lst in /boot/grub/ to point to your new image  and  i am  back in the nice silent previous state but in dapper  :)

 I thought  the 686  will have a better  energy administration and  faster response in the cpu stepping  ,  well this was what i read ,  any explanation ?

[/QUOTE]

I'm getting one of these tommorow :-D (although it should have been delivered today :mad:) so thanks for the tip.

There technically should be no difference between the 686 and 386 kernels apart from the fact that the 686 is compiled to take advantage of the optimisations available in newer x86 based processors (i.e. pentium II and onwards I think).  But kernels, processors and compilers are all complex things, so bugs occassionally make it through.  I'll do some experimentation myself and file a bug report if I get the same result as yourself.

L.

---

### Post by SpeLLTjeK on 2007-05-22
> **arkangel said:**
> Hi  ubuntians 

I have an issue  with dapper after installing it  on my asus a6va  ,  the baterry life  was bad, the fan never stops  and  it was annoying , (in brezy all was perfect) then  I notice that the only difference  was the kernel  in version  386   to 686  so  i removed the kernel  2.6.15-686  and installed the  2.6.15-386  (you can do it throught synaptic  it is not that  hard  )  but you should  be sure to edit the menu.lst in /boot/grub/ to point to your new image  and  i am  back in the nice silent previous state but in dapper  :)

 I thought  the 686  will have a better  energy administration and  faster response in the cpu stepping  ,  well this was what i read ,  any explanation ?

about  the fglrx   issue   i  installed the  driver from   i tried to do it  canonically (ie generating  the deb file as in the wikihttp://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide ) 
but it was always updated  by the system (and then  the mesa driver installed again and again )
so i installed according to  the ati  website  , just run your  ./ati-driver-installer-8.25.18-x86.run file as root  and it worked perfect for me  :)  no more mesa   8)

I do hate waking up the dead threads, but I pretty much have the same problem as this guy, though I'm running kubuntu feisty on my a6va, and therefore haven't got synaptic. So is the 'same thing' doable in kubuntu feisty with adept? I'm pretty sure the fan that's running all the time isn't my cpu fan.

---

