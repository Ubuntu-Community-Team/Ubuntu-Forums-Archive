---
title: "[SOLVED] Ubuntu is not using my Graphics Card (Dell Inspiron 530)"
date: 2008-08-30
forum: General Help
---

### Post by sirgazil on 2008-08-30
Hello,

Some days ago I started to download 3D games and I noticed that they don't behave as I think they should. Following are some of the games I
have downloaded:

[LIST]
[*]Billard-GL
[*] Extreme Tux Racer
[*] Glest
[*] Supertuxkart
[/LIST]

And these are the problems I have with them:

[LIST]
[*] If I move the game's window, it leaves behind something like an image of the content it had when I started moving it.
[*] They run slowly.
[/LIST]

How can I check if the graphics card is working or not?

Thanks in advance,

_____________________________________________________
System specs:

Dell Inspiron 530
Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
Integrated Intel(R) Graphics Media Accelerator 3100
1 GB RAM

---

### Post by fedex1993 on 2008-09-01
well are you able to run compiz. The video card should be working intel video cards arnt as good as nvidia ati etc. i have the same problem with my intel video card on my laptop but with my nvidia on my desktop it never does this.

---

### Post by sirgazil on 2008-09-01
> **fedex1993 said:**
> well are you able to run compiz. The video card should be working intel video cards arnt as good as nvidia ati etc. i have the same problem with my intel video card on my laptop but with my nvidia on my desktop it never does this.

When I installed Ubuntu Hardy it didn't activate the visual effects by default. But if I activate them manually, the only effect I see is some kind of flexibility when I move windows around.

As for the nvidia, that's not an option for me at the moment.

I've been looking for information in other places and found this:

I have the **xserver-xorg-video-intel** package but if I run **gksudo displayconfig-gtk** in the mini-cli, it shows me that Ubuntu is using **VESA driver (generic)**. It also gives me the option to chose another driver from Intel but I don't know which model I should use. These are my options:

**Model**

[I]5430
740 (generic)
810
815
830
845
85x
865
915
945
965
Express 3d agp
Q35
[/I]

Thanks for your help, fedex1993.

---

### Post by fragos on 2008-09-01
My Dell laptop also says VESA with the Intel graphics. Run "glxgears", a rotating gears window will pop up and your terminal window will report a perhaps unscientific frame rate. With the Intel it should report a little over 1000fps which would indicate that you have the correct driver. "glxinfo |grep render" will show direct rendering off and what Intel chip you have -- probably Intel 956GM. On my desktop box with an Nvidia FX5200 it shows direct renedering on but reports the a similar frame rate.

---

### Post by sirgazil on 2008-09-06
> **fragos said:**
> My Dell laptop also says VESA with the Intel graphics. Run "glxgears", a rotating gears window will pop up and your terminal window will report a perhaps unscientific frame rate. With the Intel it should report a little over 1000fps which would indicate that you have the correct driver. "glxinfo |grep render" will show direct rendering off and what Intel chip you have -- probably Intel 956GM. On my desktop box with an Nvidia FX5200 it shows direct renedering on but reports the a similar frame rate.

Thank you for your help, fragos!

This is the output when I run **glxgears**:

```
6865 frames in 5.0 seconds = 1372.030 FPS
6860 frames in 5.0 seconds = 1371.782 FPS
6880 frames in 5.0 seconds = 1372.162 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 331180 requests (330417 known processed) with 0 events remaining.
```

That **IO error** always happens when I close the gears' window.

And this is the output for **glxinfo |grep render**:

```
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
OpenGL renderer string: Mesa DRI Intel(R) G33 20061017 x86/MMX/SSE2
```

It seems that the frame rate is ok, but I'm not happy with the performance of applications that use 3D stuff. I can't use Google Earth, for example; which use to work in another computer I had, with integrated graphics too.

---

### Post by fragos on 2008-09-06
I did a little experimenting with GoogleEarth on my Dell 1420n with Intel graphics and my older desktop with AMD Sempron 2800+ and Nvidia FX5200. They register similar frame rates to what you reported and both perform well. I do have a high speed cable Internet connection perhaps your is slower. I don't know how Internet bandwith impacts the user experience or if it does.

---

### Post by sirgazil on 2008-09-06
> **fragos said:**
> I did a little experimenting with GoogleEarth on my Dell 1420n with Intel graphics and my older desktop with AMD Sempron 2800+ and Nvidia FX5200. They register similar frame rates to what you reported and both perform well. I do have a high speed cable Internet connection perhaps your is slower. I don't know how Internet bandwith impacts the user experience or if it does.

Internet connection: 1 Gbps. :-k I don't know what's the problem then.

---

### Post by sirgazil on 2008-10-18
> **sirgazil said:**
> Hello,

Some days ago I started to download 3D games and I noticed that they don't behave as I think they should. Following are some of the games I
have downloaded:

[LIST]
[*]Billard-GL
[*] Extreme Tux Racer
[*] Glest
[*] Supertuxkart
[/LIST]

And these are the problems I have with them:

[LIST]
[*] If I move the game's window, it leaves behind something like an image of the content it had when I started moving it.
[*] They run slowly.
[/LIST]

How can I check if the graphics card is working or not?

Thanks in advance,

_____________________________________________________
System specs:

Dell Inspiron 530
Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
Integrated Intel(R) Graphics Media Accelerator 3100
1 GB RAM

I got rid of this problem by choosing **None** in the visual effects options in Ubuntu.

Doing this solved the following problems:

[LIST]
[*] Lots of issues with 3D games: no title bar in some of them (BillardGL, for example), windows left a trace when moved.
[*] Blender's windowed option not available.
[*] Gecko based Web browsers going full screen at times without asking them.
[/LIST]

At last I can use 3D in my computer :)

---

