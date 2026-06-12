---
title: "Open Source video drivers + Mesa + Gallium. I am confused."
date: 2014-09-09
forum: Hardware
---

### Post by Bear_Ukraine on 2014-09-09
Hi guys, pls help. 
I can not find some answers about open source drivers. In Windows everything is clear about Intel, Nvidia and Ati drivers - for each manufacturer you need to use 1 proper driver. In the Linux world, this question is more complicated) Already a complete mess in my head. Who could describe in details the situation with drivers? 

For example, lets take the Radeon card.
1. Is my understanding correct, that there are at least two drivers - One for Xorg (means 2D), another for OpenGL (3D)? 
1.1 In the case of the Radeon for xorg is required one of the following: 
- Xf86-video-ati 
or 
- Xserver-xorg-video-radeon. 
Right? What is the difference between them? Which one is better? Is there anything else except those 2?

1.2 for OpenGL: 
- Xorg-edgers 
or 
- Oibaf? 
Same questions - What is the difference between them? Which one is better? Is there anything else except those 2?

1.3 In the case of proprietary drivers, do they provide support just only for OpenGL, or also for Xorg?

2. Question about Mesa\Gallium and xorg-edgers\oibaf 
As I understand it, at [http://www.mesa3d.org/download.html](http://www.mesa3d.org/download.html) I can download the official\latest version of Mesa\Gallium. What is the difference between xorg-edgers\oibaf and [www.mesa3d.org?](www.mesa3d.org?) Why xorg-edgers\oibaf generally needed if there is mesa3d.org? 

3. Question on Gallium Nine. 
Does Mesa\Gallium include Gallium Nine by default or do I need to download it separately? 

4. What is the name of standard (out of the box) drivers\packages of Ubuntu for the xorg and OpenGL, for Ati\Nvidia\Intel? 

Please help to sort everything on the shelves, what, how, for what should be?
Thank you very much for the clarification.

---

### Post by grahammechanical on 2014-09-09
> [COLOR=#252525][FONT=sans-serif]**OpenGL** (**Open G**raphics **L**ibrary)[SUP][[2]]("http://en.wikipedia.org/wiki/OpenGL#cite_note-2")[/SUP] is a [cross-language]("http://en.wikipedia.org/wiki/Language-independent_specification"), [multi-platform]("http://en.wikipedia.org/wiki/Cross-platform") [application programming interface]("http://en.wikipedia.org/wiki/Application_programming_interface") (API) for [rendering]("http://en.wikipedia.org/wiki/Rendering_(computer_graphics)") [2D]("http://en.wikipedia.org/wiki/2D_computer_graphics") and [3D]("http://en.wikipedia.org/wiki/3D_computer_graphics") [vector graphics]("http://en.wikipedia.org/wiki/Vector_graphics"). The API is typically used to interact with a [graphics processing unit]("http://en.wikipedia.org/wiki/Graphics_processing_unit") (GPU), to achieve[hardware-accelerated]("http://en.wikipedia.org/wiki/Hardware_acceleration") [rendering]("http://en.wikipedia.org/wiki/Rendering_(computer_graphics)").[/FONT][/COLOR]



[http://en.wikipedia.org/wiki/OpenGL](http://en.wikipedia.org/wiki/OpenGL)

> **Gallium3D is a set of interfaces and a collection of supporting libraries[SUP][[2]]("http://en.wikipedia.org/wiki/Gallium3D#cite_note-2")[/SUP] intended to ease the programming of [device drivers]("http://en.wikipedia.org/wiki/Device_driver") for[3D graphics]("http://en.wikipedia.org/wiki/3D_computer_graphics") chipsets for multiple operating systems, rendering or video acceleration APIs by splitting the graphics device driver into three parts.**

[http://en.wikipedia.org/wiki/Gallium3D](http://en.wikipedia.org/wiki/Gallium3D)

> **Mesa is a collection of [free and open-source]("http://en.wikipedia.org/wiki/Free_and_open-source") [libraries]("http://en.wikipedia.org/wiki/Library_(computing)") that implement several[rendering]("http://en.wikipedia.org/wiki/Rendering_(computer_graphics)") as well as video acceleration [APIs]("http://en.wikipedia.org/wiki/Application_programming_interface") related to [hardware-accelerated]("http://en.wikipedia.org/wiki/Hardware_acceleration") [3D rendering]("http://en.wikipedia.org/wiki/3D_rendering"), [3D computer graphics]("http://en.wikipedia.org/wiki/3D_computer_graphics") and [GPGPU]("http://en.wikipedia.org/wiki/General-purpose_computing_on_graphics_processing_units"), the most prominent being [OpenGL]("http://en.wikipedia.org/wiki/OpenGL"). Mesa is hosted at [freedesktop.org]("http://en.wikipedia.org/wiki/Freedesktop.org") and used on [Linux]("http://en.wikipedia.org/wiki/Linux"), [BSD]("http://en.wikipedia.org/wiki/Berkeley_Software_Distribution") and other [operating systems]("http://en.wikipedia.org/wiki/Operating_system"). Additionally to the APIs, Mesa also harbors most of the available [free and open-source graphics device drivers]("http://en.wikipedia.org/wiki/Free_and_open-source_graphics_device_driver").**

[http://en.wikipedia.org/wiki/Mesa_(computer_graphics)](http://en.wikipedia.org/wiki/Mesa_(computer_graphics))

The Open Source video driver for Nvidia graphic adapters is called Nouveau. The Open source video driver for AMD/ATI graphic is called Radeon. In Ubuntu we get the open source video drivers by default. 

When we install, if we tick the box "Install Third Party Software" we will get installed a proprietary video driver. In other words, a video driver provided by the maker of the graphic adapter be it Nvidia or AMD/ATI. These are closed source software. Which means that Ubuntu developers cannot alter the software to fix things. The only thing that the Ubuntu developers can do is pass our bug reports back to Nvidia or AMD/ATI.

In Ubuntu we get tested proprietary video drivers. There are a couple of places where we can get the newest versions of the video drivers. The X-edgers PPA (Personal Package Archive) and the Oibaf PPA are two of those places. Installing these newly released versions of video drivers should be viewed as an experiment and an opportunity to find bugs.

At the moment all Linux distributions run on the X.Org server.

[http://en.wikipedia.org/wiki/X.Org_Server](http://en.wikipedia.org/wiki/X.Org_Server)

> [COLOR=#252525][FONT=sans-serif]X provides the basic framework for a [/FONT][/COLOR][GUI]("http://en.wikipedia.org/wiki/Graphical_user_interface")[COLOR=#252525][FONT=sans-serif] environment: drawing and moving [/FONT][/COLOR][windows]("http://en.wikipedia.org/wiki/Window_(computing)")[COLOR=#252525][FONT=sans-serif] on the [/FONT][/COLOR][display device]("http://en.wikipedia.org/wiki/Display_device")[COLOR=#252525][FONT=sans-serif] and interacting with a [/FONT][/COLOR][mouse]("http://en.wikipedia.org/wiki/Computer_mouse")[COLOR=#252525][FONT=sans-serif] and[/FONT][/COLOR][keyboard]("http://en.wikipedia.org/wiki/Computer_keyboard")[COLOR=#252525][FONT=sans-serif]. X does not mandate the user interface &#8212; this is handled by individual programs. As such, the visual styling of X-based environments varies greatly; different programs may present radically different interfaces.[/FONT][/COLOR]

[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

So, we should not be surprised that the X organisation is closely linked to the open source video drivers. I have an Nvidia graphic adapter and I am using the open source video driver. When I run this command

```
/usr/lib/nux/unity_support_test -p
```

I get this

> OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 10.2.6


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes



Mesa is an implementation of the OpenGL specification and the Gallium open source video driver has Mesa 10.2.6.

And you thought that you would get a simple answer.

Regards.

---

### Post by Bear_Ukraine on 2014-09-09
Everything you linked and much more Ive read a couple of times) Ive spent about a week trying to find details on my questions) Generally I have a vision, how video system in Linux works (because spent 1 week ;) ), but still have a specific questions.

I cant understand does Linux use 2 drivers (for X and OpenGL) or just one? Maybe question is stupied but this questions is arised because of different info from different sources Ive read.
Could you explain the difference between X-edgers PPA (Personal Package Archive) and the Oibaf PPA and Xf86-video-ati\Xserver-xorg-video-radeon?
How about Gallium Nine?
What is the name of standard (out of the box) drivers\packages of Ubuntu? On different forums I see names of graphic packages but dont know what they mean. That is the reason why I asked about the names. I want to have a list of this packages that helps me to understand Ubuntu better. I have a laptop with Intel\ATI and I dont know from which side would be better to come in order to update drivers, because I want to get more FPS) I know, there are lots of instructions like "do this do that", which I already used, but I want to understand this question deaper (I mean theoretic side, because instructions just tell what to do and do not provide any info "What is this, what is that, why do we need to do this, etc.". Im Windows guru, but now I decided (at 4th time) to become an Ubuntu guru :)
Thanks.

---

