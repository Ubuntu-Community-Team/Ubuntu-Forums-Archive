---
title: "Opengl version and nvidia drivers"
date: 2017-08-16
forum: Hardware
---

### Post by c_xy on 2017-08-16
Hello,

Here are the specs for our server

[COLOR=#000000]Again it is dell poweredge r730 server[/COLOR]
[COLOR=#000000]96 GB memory[/COLOR]
[COLOR=#000000]25 TB storage[/COLOR]
[COLOR=#000000]2 CPU 2.6 GHz, 10core.[/COLOR]
[COLOR=#000000]The graphics card on the server is: NVIDIA Tesla K10 GPU

We are using Ubuntu 14.04 LTS.

[/COLOR]Here are my graphics setup:

```

sudo lshw -C display

 *-display                      description: 3D controller
       product: GK104GL [Tesla K10]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: iomemory:33f0-33ef iomemory:33f0-33ef irq:31 memory:92000000-92ffffff memory:33fe0000000-33fefffffff memory:33ff0000000-33ff1ffffff
  *-display
       description: 3D controller
       product: GK104GL [Tesla K10]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: iomemory:33f0-33ef iomemory:33f0-33ef irq:31 memory:91000000-91ffffff memory:33fc0000000-33fcfffffff memory:33fd0000000-33fd1ffffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: G200eR2
       vendor: Matrox Electronics Systems Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=16
       resources: memory:90000000-90ffffff memory:93800000-93803fff memory:93000000-937fffff





```
[COLOR=#000000]
[/COLOR]When I look up Additional Drivers, the NVIDIA driver is installed is 375.66.[COLOR=#000000]
[/COLOR]

We access this server using nomachine and x2go from Windows Clients.

I've run into issues trying to use a software application and we kept getting this message:

```
OpenGL 1.4 or newer is required (detected version: 1.2)
```

I couldn't understand why only version 1.2 is detected.

Here is the output from glxinfo:

```


glxinfo  | grep OpenOpenGL vendor string: Mesa project: www.mesa3d.org
[COLOR=#ff0000]OpenGL renderer string: Mesa GLX Indirect[/COLOR]
OpenGL core profile version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL core profile extensions:
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:



```



One thing I notice is that "[COLOR=#ff0000]OpenGL renderer string: Mesa GLX Indirect[/COLOR]". However, I DON'T declare export LIBGL_ALWAYS_INDIRECT=1 in my .bashrc file. Even when  I use the command

```
unset LIBGL_ALWAYS_INDIRECT
```

The output still is still the same from glixinfo.


I'm confused as to what the issue might be. We have another r730 machine we use with the same Matrox Graphics card, but without the NVIDA cards. 

And the glxinfo output from the other machine is:

```


glxinfo | grep 'version'
server glx version string: 1.2
client glx version string: 1.4
GLX version: 1.2
    Max core profile version: 3.3
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.0
OpenGL version string: 3.0 Mesa 17.0.7
OpenGL shading language version string: 1.30



```


At least with that system, the OpenGL version string is 3.0.

I'm thinking the issue has something to do with having NVIDIA cards and Matrox card on the same system.   When we first purchased our r730 server a couple of years ago, the ubuntu nvidia drivers weren't compatible with the NVIDA cards. I had to manually install the appropriate NVIDIA driver at the time. We still have a NVIDIA driver manually installed. Would this cause this issue? It seems now Ubuntu has higher version NVIDIA drivers. Would uninstalling the NVIDIA site driver and installing the Ubuntu nvidia driver resolve this issue? Or is there something else wrong?


Any help would greatly be appreciated.

Thank you.

c.

---

### Post by Yellow Pasque on 2017-08-16
Yes, when you install the Nvidia driver, it overwrites the the libGL files needed by the Matrox card. The Linux world is moving towards GLVND ([https://www.phoronix.com/scan.php?page=news_item&px=Mesa-Will-Do-GLVND](https://www.phoronix.com/scan.php?page=news_item&px=Mesa-Will-Do-GLVND)) to circumvent the issue, but that's not going to help you on Ubuntu 14.04.

I would think that you would want to run the application on the Nvidia card anyway, but I'm not sure how to do that off the top of my head.

---

### Post by c_xy on 2017-08-16
Temujin,

Thank you for your response, especially the part about overwriting libGL files needed by the Matrox card.

When i run this on our machine with the NVIDIA driver manually installed:

```

	
 ldconfig -p | grep libGL.so
	libGL.so.1 (libc6,x86-64) => /usr/lib/nvidia-375/libGL.so.1
	libGL.so.1 (libc6) => /usr/lib32/nvidia-375/libGL.so.1
	libGL.so (libc6,x86-64) => /usr/lib/nvidia-375/libGL.so
	libGL.so (libc6) => /usr/lib32/nvidia-375/libGL.so




```

But on our other machines with ONLY the Matrox card:

```


ldconfig -p | grep libGL.so

	libGL.so.1 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1	libGL.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libGL.so
	libGL.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/mesa/libGL.so






```

Does installing NVIDIA drivers overwite the libGL files[COLOR=#ff0000] ONLY[/COLOR] when using the drivers from the NVIDIA site (i.e., *.run files)? What if you just installed just using apt-get? Would the problem still remain?

Running the application on the NVIDIA card isn't important for us. We run it on our other machines with the Matrox card with no issues at all.  We are lost on how to set it up with Matrox/NVIDIA dual cards on this current machine.

Any help would greatly be appreciated.

c.

---

### Post by Autodave on 2017-08-16
How did you install the Nvidia driver and where did you get it from?

---

### Post by vocx on 2017-08-16
> **Autodave said:**
> How did you install the Nvidia driver and where did you get it from?
He just said he got them from the Nvidia website. The old fashioned way before Ubuntu used the Additional drivers way.

> **c_xy said:**
> 
Does installing NVIDIA drivers overwite the libGL files[COLOR=#ff0000] ONLY[/COLOR] when using the drivers from the NVIDIA site (i.e., *.run files)? What if you just installed just using apt-get? Would the problem still remain?
c.

I would also advice you to upgrade the entire system to 16.04. Probably the version of the X server in 14.04 also limits your use of the newest Open GL. Everything that is tightly integrated to the hardware should run better with an updated Linux kernel, and X Server. And yes, I would remove those manually installed nvidia drivers, and instead use the "additional drivers" method, from the Ubuntu Settings > Software & updates way.

---

### Post by c_xy on 2017-08-16
> **vocx said:**
> He just said he got them from the Nvidia website. The old fashioned way before Ubuntu used the Additional drivers way.



I would also advice you to upgrade the entire system to 16.04. Probably the version of the X server in 14.04 also limits your use of the newest Open GL. Everything that is tightly integrated to the hardware should run better with an updated Linux kernel, and X Server. And yes, I would remove those manually installed nvidia drivers, and instead use the "additional drivers" method, from the Ubuntu Settings > Software & updates way.

Yes, that is the correct. I obtained the drivers (.run file) from the Nvidia website.

As far as upgrading to 16.04, we prefer not to at the moment. In fact, our current 14.04 LTS is running the same linux kernel ([COLOR=#333333][FONT=&amp]Xenial HWE Stack v4.4. Kernel) [/FONT][/COLOR] as 16.04 since our original installation of 14.04 LTS was 14.04.3. [COLOR=#333333][FONT=&amp]On our other linux machines that run 14.04,  the OpenGL string version is 3.0. 

[/FONT][/COLOR]Is there something more to it? I think I might just remove the manually installed nvidia drivers, and do clean install of the nvidia drivers through apt-get/additional drivers to see if that changes things.

c.

---

### Post by c_xy on 2017-08-17
Update.

Okay, I uninstalled the manually installed NVIDIA driver:

```


sudo ./NVIDIA*.run --uninstall

```


Using this as a guide:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

These were my steps:

```

sudo ubuntu-drivers devices

model    : GK104GL [Tesla K10]
modalias : pci:v000010DEd0000118Fsv000010DEsd0000097Fbc03sc02i00
vendor   : NVIDIA Corporation
driver   : nvidia-375 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-340 - distro non-free
driver   : nvidia-304 - distro non-free


```


```


sudo apt-get install nvidia-375


```



Now, I can't get even get glxinfo to work:

```

glxinfo
name of display: :2000.0
Error: couldn't find RGB GLX visual or fbconfig
Error: couldn't find RGB GLX visual or fbconfig




```

Can't get glxgears to work:

```


glxgears
Error: couldn't get an RGB, Double-buffered visual


```

With the manually installed NVIDIA driver, glxgears and glxinfo would at least work, but I was restricted to OpenGL 1.2.

With the NVIDIA driver installed using the apt-get method, I get error messages with both glxgears and glxinfo and not system output.

I'm kinda stuck. With the manually installed method, at least mostly everything works, except for the OpengGL version glitch.

With either method, any input would greatly be appreciated on how to resolve this issue.

Thanks in advance.

c

---

### Post by c_xy on 2017-08-22
Okay, manually installing the NVIDIA driver seems to work the best.

However, I'm still left with this problem:


**Example A:**
```


% glxinfo | grep Open
[COLOR=#ff0000]OpenGL vendor string: Mesa project: www.mesa3d.org[/COLOR]
OpenGL renderer string: Mesa GLX Indirect
OpenGL core profile version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL core profile extensions:
[COLOR=#ff0000]OpenGL version string: 1.2 (1.5 Mesa 6.4.1)[/COLOR]
OpenGL extensions:





```


Why can I not upgrade version string, and why does it always remain Mesa GLX Indirect?

On another machine with the same VGA graphics card I get:

**Example B:**

```


~$ glxinfo | grep Open
[COLOR=#ff0000]OpenGL vendor string: VMware, Inc.[/COLOR]
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 4.0, 256 bits)
[COLOR=#ff0000]OpenGL version string: 3.0 Mesa 17.0.7[/COLOR]
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:


```

Again, Example A and Example both have Matrox G200eR2 VGA controllers. The only difference is that Example A has two additional NVIDA k10 Tesla 3D Controllers and Example B does not.

Why can't Example A match Example B? Why is Example B's vender string equal VMware and Example A is Mesa project: [www.mesa3d.org?]("http://www.mesa3d.org?") How can I make Example A use VMware string with OpenGL string 3.0 Mesa 17.0.7?

For the software application we want to use, we don't need to use direct rendering. Software rendering is suffice. It works for Example B, but Example A does not because Example's OpenGL version string is 1.2. It needs to be 1.4 or above. With Example B, it is 3.0.

Any input would be appreciated. I'm stuck right now.

Thanks in advance.

c

---

### Post by Yellow Pasque on 2017-08-23
> **c_xy said:**
> How can I make Example A use VMware string with OpenGL string 3.0 Mesa 17.0.7?
No dice. I don't think you can do that without a lot of hacking at library paths. I don't know how your knowledge of Debian's alternatives system is, but installing the Nvidia driver the correct way (via .deb package) may be a better bet than installing the Nvidia driver manually ;)

---

