---
title: "Ubuntu 20.04 does not use my GPU even if NVIDIA drivers are loaded correctly"
date: 2024-01-17
forum: Hardware
---

### Post by manentai on 2024-01-17
I am on an headless server Ubuntu 20.04 and I have an NVIDIA Tesla P4, for which I have installed NVIDIA drivers 525 with CUDA 12.0 from the NVIDIA website (.run, not with ubuntu-drivers)

It seems like the server sees the GPU fine:

```

+-----------------------------------------------------------------------------+
| NVIDIA-SMI 525.147.05   Driver Version: 525.147.05   CUDA Version: 12.0     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  Tesla P4            Off  | 00000000:21:00.0 Off |                    0 |
| N/A   40C    P0    22W /  75W |      0MiB /  7680MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+

```

```

inxi -G
Graphics:  Device-1: NVIDIA GP104GL [Tesla P4] driver: nvidia v: 525.147.05 
           Display: server: X.Org 1.21.1.6 driver: nvidia resolution: 4080x2160~1Hz 
           OpenGL: renderer: Tesla P4/PCIe/SSE2 v: 4.6.0 NVIDIA 525.147.05

```

```

lspci -v | grep -EA3 'VGA|3D'
01:00.1 VGA compatible controller: Matrox Electronics Systems Ltd. MGA G200EH (prog-if 00 [VGA controller])
        Subsystem: Hewlett-Packard Company iLO4
        Flags: bus master, fast devsel, latency 0, IRQ 16, NUMA node 0
        Memory at d9000000 (32-bit, prefetchable) [size=16M]
--
21:00.0 3D controller: NVIDIA Corporation GP104GL [Tesla P4] (rev a1)
        Subsystem: NVIDIA Corporation GP104GL [Tesla P4]
        Physical Slot: 4
        Flags: bus master, fast devsel, latency 0, IRQ 110, NUMA node 1

```

however when I tell it to use nvidia, it gives me this:
```

sudo prime-select nvidia
Error: no integrated GPU detected.

```

Or when I try to use the GPU with software like llama.cpp, trying to load a LLM to the GPU, it ends up using only the CPU only as if I had no GPU... 

my end goal is also to use the GPU in X-forwarding to run programs that need to build OpenGL windows. If I run 

```
xclock
```

I see the XQuartz window popping up, but any other command like 
```

glxgears
Error: couldn't get an RGB, Double-buffered visual

```

or

```

glmark2
Error: glXChooseFBConfig() failed
Error: Error: Couldn't get GL visual config!
Error: main: Could not initialize canvas

```

So I guess first thing I want to be sure that the server sees the GPU... are there any other test I can try to see if actually my server sees the GPU? or to select it definitively as the de-facto video card?

---

### Post by TheFu on 2024-01-18
Does X/Windows work that way?  I didn't think it did.  Seek out some other method. 

Last time I checked, the GPU is used only by the local X/Server. You said you have a headless server, so there isn't any local X/Server.  What you have is an X/Client, which is completely different.  The X/Server runs on the workstation you are sitting behind.

Perhaps Wayland has a method?

---

### Post by BicyclerBoy on 2024-01-18
Do any of these suggest a possible solution?
software:
xserver-xorg-video-dummy 
hardware:
dummy display plug
config:
dummy monitor in xorg.conf

---

### Post by MAFoElffen on 2024-01-20
Mine works great remotely but the difference with my Workstation and your server is that mine has a Desktop with a User logged in, so had XServer running... It is not headless.
```

mafoelffen@msi-ubuntu:~$ DISPLAY=:0 xprop -root|grep ^_NET_CLIENT_LIS
_NET_CLIENT_LIST_STACKING(WINDOW): window id # 0x1600002, 0x1400002, 0x2400002, 0x2600002, 0x2200002
_NET_CLIENT_LIST(WINDOW): window id # 0x2200002, 0x1600002, 0x1400002, 0x2400002, 0x2600002
mafoelffen@msi-ubuntu:~$ DISPLAY=:0 xwininfo -tree -root

xwininfo: Window id: 0x20c (the root window) (has no name)

  Root window id: 0x20c (the root window) (has no name)
  Parent window id: 0x0 (none)
     33 children:
     0x2a00017 "update-notifier": ("livepatch" "livepatch")  16x16+0+0  +0+0
        1 child:
        0x2a00018 (has no name): ()  1x1+-1+-1  +-1+-1
     0x2a0000c (has no name): ()  1x1+-1+-1  +-1+-1
     0x2a00001 "update-notifier": ("update-notifier" "Update-notifier")  10x10+10+10  +10+10
     0x2200009 (has no name): ()  1x1+-1+-1  +-1+-1
     0x60000a "gnome-shell": ("gnome-shell" "Gnome-shell")  1x1+-200+-200  +-200+-200
        1 child:
        0x60000b (has no name): ()  1x1+-1+-1  +-201+-201
     0x600058 (has no name): ()  358x1066+1533+24  +1533+24
        1 child:
        0x2200002 "conky (msi-ubuntu)": ("conky" "conky")  338x1011+10+45  +1543+69
     0x2600002 "conky (msi-ubuntu)": ("conky" "conky")  197x282+445+783  +445+783
     0x2400002 "conky (msi-ubuntu)": ("conky" "conky")  181x272+645+783  +645+783
     0x1400002 "conky (msi-ubuntu)": ("conky" "conky")  411x240+15+805  +15+805
     0x1600002 "conky (msi-ubuntu)": ("conky" "conky")  211x230+845+815  +845+815
     0x2000003 (has no name): ()  1x1+-1+-1  +-1+-1
     0x600035 (has no name): ()  1x1+-1+-1  +-1+-1
     0x2000001 "Software": ("org.gnome.Software" "Org.gnome.Software")  10x10+10+10  +10+10
     0x1e00001 "evolution-alarm-notify": ("evolution-alarm-notify" "Evolution-alarm-notify")  10x10+10+10  +10+10
     0x1a00003 "ibus-xim": ()  1x1+0+0  +0+0
        1 child:
        0x1a00004 (has no name): ()  1x1+-1+-1  +-1+-1
     0x1c00001 "ibus-extension-gtk3": ("ibus-extension-gtk3" "Ibus-extension-gtk3")  10x10+10+10  +10+10
     0x1a00001 "ibus-x11": ("ibus-x11" "Ibus-x11")  10x10+10+10  +10+10
     0x1000002 (has no name): ()  10x10+0+0  +0+0
     0x1800001 "gsd-media-keys": ("gsd-media-keys" "Gsd-media-keys")  10x10+10+10  +10+10
     0x1200001 "gsd-power": ("gsd-power" "Gsd-power")  10x10+10+10  +10+10
     0x1000001 "gsd-xsettings": ("gsd-xsettings" "Gsd-xsettings")  10x10+10+10  +10+10
     0xe00001 "gsd-wacom": ("gsd-wacom" "Gsd-wacom")  10x10+10+10  +10+10
     0xc00001 "gsd-color": ("gsd-color" "Gsd-color")  10x10+10+10  +10+10
     0xa00001 "gsd-keyboard": ("gsd-keyboard" "Gsd-keyboard")  10x10+10+10  +10+10
     0x600011 (has no name): ()  1x1+-100+-100  +-100+-100
     0x60000f (has no name): ()  1x1+-100+-100  +-100+-100
     0x60000e (has no name): ()  1x1+-1+-1  +-1+-1
     0x600008 (has no name): ()  1x1+-100+-100  +-100+-100
     0x600007 (has no name): ()  1x1+-100+-100  +-100+-100
     0x600006 "GNOME Shell": ()  1x1+-100+-100  +-100+-100
     0x600001 "gnome-shell": ("gnome-shell" "Gnome-shell")  10x10+10+10  +10+10
     0x400007 (has no name): ()  1x1+-100+-100  +-100+-100
     0x600010 "mutter guard window": ()  1920x1080+0+0  +0+0

```

> **TheFu said:**
> Does X/Windows work that way? I didn't think it did. Seek out some other method.

Last time I checked, the GPU is used only by the local X/Server. You said you have a headless server, so there isn't any local X/Server. What you have is an X/Client, which is completely different. The X/Server runs on the workstation you are sitting behind.

You know better. How many decades do both you and I have with XServer on Unix and Linux? I think you just had a one of those moments about the wording of that. lol.

That is a "Sort-Of"... Where there are some things that do have to happen, and be running if you want to do that as headless.

You are headless right?

What does this say?
```

ps -e | grep -E 'Xorg'

```
For what you want to do... XServer has to be running, and if NVidia, you have to have the driver running, and since Tesla, it has to be detached from a screen session. In fact if you look at an NVidia Tesla P4, it has no display ports. If you want to use it for rendering, the onlt way to use it is remotely, or for virtual rendering.

There is some tricks for that, but you are going to have to create an xorg.conf file for it...

In these section include these options:
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Tesla P4"
    BusID          "PCI:1:0:0" # Adjust this to what yours is in...
    Option         "AllowEmptyInitialConfiguration" "true" # Allowed since driver 460.32.03
EndSection

```
[Driver]
Set user user on your server to autologin. Search my userid o this forum for those instructions on Server Edition...

That will allow the NVIDIA X driver to succeed when launching the XServer even if there are no display devices connected.

I have other workarounds for older drivers with headless servers using "Option UseEDID FALSE"" or "Option UseDisplayDevice none"...

Reason you need something like this?:
By default an NVidia driver probes the ports and looks for an attached display by probe ports, then searching for the EDID of the attached display... When it doesn't find something, it's default behavior to to turn off the ports.

---

### Post by TheFu on 2024-01-21
> **MAFoElffen said:**
>  
You know better. How many decades do both you and I have with XServer on Unix and Linux? I think you just had a one of those moments about the wording of that. lol.
 

Perhaps it could be worded better.

My understanding was that the OP had some high-end GPU on a remote computer that he wanted to make use of.  X/Windows has a client and a server.  The server is on the physical machine we are typing on and the client is the remote system, in his case, with the hot, fast, GPU.  That remote GPU doesn't become involved with performance on the local workstation.  THAT was what I was trying to say.  It is only the local GPU, whatever it might be, that controls the GPU performance. The remote GPU has no connection at all.

I can't really show differences easily, since my two hardware systems have the exact same APU. So the reported GPU regardless of local or remote would be the same.

By forcing the DISPLAY to :0, you do show the local X/Server on your "remote" system, but that's because you installed it, not because it will be used by the workstation you sit behind.

This is the way it works by default. I understand there are gaming solutions that use a different protocol for specific nVidia GPUs that can be used remotely.  These are typically for paid, online, games.  I'm thinking about the failed Google Stadia.  There are others too.

Am I wrong or misreading the OPs intent?

BTW, I can run glxgears both locally and remotely over an ssh -X tunnel on the other system, but that's because I have an X/server on both systems.

Local run (I'm sitting on the computer running the program):
```
$ glxgears 
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
516 frames in 5.0 seconds = 102.999 FPS
300 frames in 5.0 seconds = 59.951 FPS
300 frames in 5.0 seconds = 59.951 FPS

```
Remote run (using an ssh -X tunnel to the computer running the program):
```
$ glxgears
765 frames in 5.0 seconds = 152.987 FPS
679 frames in 5.0 seconds = 135.720 FPS
681 frames in 5.0 seconds = 136.159 FPS
680 frames in 5.0 seconds = 135.940 FPS

```
So **my guess** is that the ssh tunnel doesn't let it know the native monitor refresh rate and because the GPU can do more frames, it does.  With the local run, it quickly determines the monitor refresh rate and doesn't bother going faster.  

Asking inxi about the Graphics environment over the ssh -X tunnel, 
The real hardware
```
$ inxi -G
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] driver: amdgpu v: kernel 
           Display: server: X.Org 1.20.13 driver: amdgpu,ati unloaded: fbdev,modesetting,vesa resolution: [COLOR="#FF0000"]1920x1200~60Hz[/COLOR] 
           **OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.2.6** 
```

The virtual hardware
```
$ [COLOR="#FF0000"]DISPLAY=:0[/COLOR] inxi -G
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] driver: amdgpu v: kernel 
           Display: server: X.org 1.20.13 driver: amdgpu,ati unloaded: fbdev,modesetting,vesa tty: [COLOR="#FF0000"]143x23[/COLOR] 
           Message: **No advanced graphics data found on this system. **
```

The local GPU on the remote system isn't used.

---

