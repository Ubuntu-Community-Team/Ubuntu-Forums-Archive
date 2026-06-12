---
title: "Laptop graphics card"
date: 2008-09-15
forum: Hardware
---

### Post by tojas on 2008-09-15
Hi!

I tried to install my graphic card. So I downloaded the needed driver.
After this I unpacked the driver. Then I got in the folder a runnable file called "install.sh". So I thought this will solve everything for me :D
But I got an error...

> 
Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.


So guys, can you help me in this problem?

---

### Post by Squish on 2008-09-15
you shouldnt need to manually download the driver. 

In doing it the way you do it, I usually got to tty1, stop the xserver, then run the install.sh ~

If you are running ubuntu though, the restricted drivers utility should have detected it  and installed it for you.

What type of graphics card do you have?

---

### Post by tojas on 2008-09-15
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)

When I type lspci I got this... I don't know if it is installed or not...

My real problem is that when I run a program with wine I got the following error:

> fixme:win:EnumDisplayDevicesW ((null),0,0x33e468,0x00000000), stub!
err:ddraw:IDirectDrawImpl_QueryInterface (0x1345d8) The App is requesting a D3D device, but a non-OpenGL surface type was choosen. Prepare for trouble!
err:ddraw:IDirectDrawImpl_QueryInterface  (0x1345d8) You may want to contact wine-devel for help
err:ddraw:IDirectDrawSurfaceImpl_QueryInterface No interface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
Segmentation fault


---

### Post by Squish on 2008-09-16
hmmm, I had no idea the terminal could output emoticons

lol

yah man, wine is a bit more fickle of a question, check out their app database for the program in question.
you probably know this, but not all programs will work in wine. Id say a good half do though.

---

### Post by tojas on 2008-09-17
Aha ok... thanks :)


Btw. I forgot to disable emoticons on that post...:)

---

