---
title: "Nvidia Drivers 11.04"
date: 2011-04-20
forum: Hardware
---

### Post by cjschris on 2011-04-20
I had to reinstall Ubuntu after a Kernal Panic during an upgrade (lucky me), and now I have to reinstall my Nvidia drivers.

I have a Nvidia GeForce 8400M GS and I found the drivers.
But I don't know how to install the .run file it downloads.
I click on it from Chrome and it opens it in Gedit, but I don't think that's right.


Thanks

---

### Post by mikewhatever on 2011-04-20
Don't download drivers from the internet, use the native Additional Drivers utility instead. Natty already has the latest 270.41 driver. Don't install multiple drivers, it will break the system.

---

### Post by cjschris on 2011-04-20
Why are the Ubuntu Visual Effects disabled then?
The weren't before

---

### Post by mikewhatever on 2011-04-20
Nvidia driver is not installed by default, therefore, no effects.

---

### Post by cjschris on 2011-04-20
which was why i was asking how to install the official drivers.

---

### Post by mikewhatever on 2011-04-21
...and I told how to do it in the most efficient way.;)

---

### Post by meighty on 2011-04-23
After spending a good portion of my morning trying to get Unity working on my laptop, I'm pretty much stuck using the non-Unity 11.04.

Right now 11.04 is installed on my Alienware M11x which should have the Nvidia 335m and I'm also using the "nvidia_current" so I'm positive that I have 270.41.06 installed.

Am I missing something? Is there a config I should change or something I should do in order to enable Unity? Obviously I have plenty of power to run Unity. My MSI netbook with shared video ram is able to run Unity.

Thoughts?

---

### Post by Urbanmoth on 2011-04-28
This was what persuaded me to stop worrying about unity and stick with the standard gnome desktop. 

Try:

```
/usr/lib/nux/unity_support_test -p
```

My output was:

```
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce Go 7400/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```

So it looks like my card is backlisted :(

11.04 works fine otherwise

---

### Post by slowtype on 2011-04-28
Blacklisted!  

This is disappointing.

I have the 7400 as well.  Unity worked for a short period of time with the experimental 3D drivers when I tried 11.04 in unity.  Then one day after an update I could no longer enable unity.

[http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity](http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity)

---

### Post by spgrimes on 2011-04-28
Hello all,

I am new to linux/ubuntu and to the forums and need a little bit of help.

I had the same message after installing ubuntu about my hardware not supporting unity but then installed the suggested 3d acceleration drivers and figured that would make it work. But it didn't. I have been searching forums but cannot find exactly what to do to see if I can run it with the updated drivers. I typed in the command from Urbanmoth and got this response. 

OpenGL vendor string:   Nouveau
OpenGL renderer string: Mesa DRI nv17 20091015 x86/MMX/SSE2
OpenGL version string:  1.2 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Any takers on what I should do?

---

### Post by mexp on 2011-04-29
Blacklisted: So this means no Unity for me then? 

That's fine, but how do I actually know that the *nvidia* driver is in use, as the Additional Drivers -application says "This driver is activated but not currently in use."

I didn't dare to remove the nvidia-drivers for reinstall, as I thought I might lose the whole configuration and be left with command line only...

```
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce Go 7300/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no
```

---

