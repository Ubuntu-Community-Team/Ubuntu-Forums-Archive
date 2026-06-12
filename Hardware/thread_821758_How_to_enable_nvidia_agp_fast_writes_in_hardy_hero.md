---
title: "How to enable nvidia agp fast writes in hardy heron??"
date: 2008-06-07
forum: Hardware
---

### Post by vectorslave on 2008-06-07
Hello!

I have Nvidia 6600GT and the latest nvidia drivers 169.12 by EnvyNG!

I try this guide 
[http://lj4newbies.blogspot.com/2007/09/enable-nvidia-agp-fast-writes-and-side.html]("http://lj4newbies.blogspot.com/2007/09/enable-nvidia-agp-fast-writes-and-side.html")
but nothing. :/

This is my result:

```
analog@analog-desktop:~$ cat /proc/driver/nvidia/agp/status
Status: 	 Enabled
Driver: 	 NVIDIA
AGP Rate: 	 8x
[COLOR="Red"]Fast Writes: 	 Disabled[/COLOR]
SBA: 		 Enabled
```

```
analog@analog-desktop:~$ cat /proc/driver/nvidia/registry
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
[COLOR="Red"]EnableAGPSBA: 0
EnableAGPFW: 0[/COLOR]
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UseCPA: 4294967295
UseVBios: 1
```

```
analog@analog-desktop:~$ glxgears -info
GL_RENDERER   = GeForce 6600 GT/AGP/SSE/3DNOW!
GL_VERSION    = 2.1.2 NVIDIA 169.12
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffe
12789 frames in 5.0 seconds = 2557.652 FPS
13078 frames in 5.0 seconds = 2615.255 FPS
13823 frames in 5.0 seconds = 2764.582 FPS
12874 frames in 5.0 seconds = 2574.699 FPS
13573 frames in 5.0 seconds = 2714.577 FPS
14044 frames in 5.0 seconds = 2793.969 FPS
```

I Add this lines into [COLOR="Red"]/etc/modprobe.d/nvidia-kernel-nkc[/COLOR] :

```
alias char-major-195* nvidia
options nvidia NVreg_EnableAGPFW=1 NVreg_EnableAGPSBA=1
```



and.....at last fast writes still disabled

```
analog@analog-desktop:~$ cat /proc/driver/nvidia/agp/status
Status: 	 Enabled
Driver: 	 NVIDIA
AGP Rate: 	 8x
[COLOR="Red"]Fast Writes: 	 Disabled[/COLOR]
SBA: 		 Enabled
```

anyone can help me plz?

---

### Post by darklordveynom on 2008-06-11
I have the same problem and am still unable to figure out how to fix it.

---

### Post by vectorslave on 2008-06-19
I cant find any solution :(

---

### Post by stchman on 2008-06-19
> **vectorslave said:**
> Hello!

I have Nvidia 6600GT and the latest nvidia drivers 169.12 by EnvyNG!

I try this guide 
[http://lj4newbies.blogspot.com/2007/09/enable-nvidia-agp-fast-writes-and-side.html]("http://lj4newbies.blogspot.com/2007/09/enable-nvidia-agp-fast-writes-and-side.html")
but nothing. :/

This is my result:

```
analog@analog-desktop:~$ cat /proc/driver/nvidia/agp/status
Status: 	 Enabled
Driver: 	 NVIDIA
AGP Rate: 	 8x
[COLOR="Red"]Fast Writes: 	 Disabled[/COLOR]
SBA: 		 Enabled
```

```
analog@analog-desktop:~$ cat /proc/driver/nvidia/registry
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
[COLOR="Red"]EnableAGPSBA: 0
EnableAGPFW: 0[/COLOR]
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UseCPA: 4294967295
UseVBios: 1
```

```
analog@analog-desktop:~$ glxgears -info
GL_RENDERER   = GeForce 6600 GT/AGP/SSE/3DNOW!
GL_VERSION    = 2.1.2 NVIDIA 169.12
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffe
12789 frames in 5.0 seconds = 2557.652 FPS
13078 frames in 5.0 seconds = 2615.255 FPS
13823 frames in 5.0 seconds = 2764.582 FPS
12874 frames in 5.0 seconds = 2574.699 FPS
13573 frames in 5.0 seconds = 2714.577 FPS
14044 frames in 5.0 seconds = 2793.969 FPS
```

I Add this lines into [COLOR="Red"]/etc/modprobe.d/nvidia-kernel-nkc[/COLOR] :

```
alias char-major-195* nvidia
options nvidia NVreg_EnableAGPFW=1 NVreg_EnableAGPSBA=1
```



and.....at last fast writes still disabled

```
analog@analog-desktop:~$ cat /proc/driver/nvidia/agp/status
Status: 	 Enabled
Driver: 	 NVIDIA
AGP Rate: 	 8x
[COLOR="Red"]Fast Writes: 	 Disabled[/COLOR]
SBA: 		 Enabled
```

anyone can help me plz?

You enable AGP fast writes in the BIOS.  I have not messed with AGP in some time but I do remember that.

---

### Post by vectorslave on 2008-06-23
I dont have any option in my bios to do this :/.

---

### Post by stchman on 2008-06-23
Ok, I have done some looking around.  Not all AGP mobos support fast writes.  If your mobo supported fast writes, the option in the BIOS would be there.

There is a very marginal improvement in enabling fast writes.  I personally would not worry about it.

---

### Post by vectorslave on 2008-06-24
Thanks for the infos dude!

---

### Post by Ben_H on 2009-02-19
since I did this, my computer won't resume from suspend. I have "NvAGP" turned to "1" in the xorg.conf. What could the problem be? 

I have an ABIT nf7 motherboard (nforce2 chipset, supports fast writes) and a Geforce4 mx440 64mb graphics card. I run intrepid ibex with  2.6.27-11-generic kernel.

Thanks for any help,

Ben

---

