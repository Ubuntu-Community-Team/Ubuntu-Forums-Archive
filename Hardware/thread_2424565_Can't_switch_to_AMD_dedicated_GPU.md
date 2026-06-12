---
title: "Can't switch to AMD dedicated GPU"
date: 2019-08-10
forum: Hardware
---

### Post by chelseainspace on 2019-08-10
Hey there, I am running a ThinkPad E490 with an integrated Intel UHD GPU, but I would rather use my dedicated Radeon RX550 for some tasks. I found several instructions on how to use the Prime command and tried implementing it but somehow it just doesn't seem to work; in fact when I check my GPUs using
> lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA
it only shows me the Intel iGPU anymore:
> 00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:3ea0] (prog-if 00 [VGA controller])

Originally I was at least able to see the AMD GPU listed there, albeit not being the active one. During my attempts to get it running I was tinkering with the grub file as well as drivers and I am worried I somehow messed something up in the process; but ultimately I still just want to find a way to enable my dGPU so if you have any tips on what to do I'd really appreciate it :) Cheers

Edit: This is what my system info tells me:
> [FONT=arial]Graphics:  Device-1: Intel vendor: Lenovo driver: i915 v: kernel bus ID: 00:02.0             chip ID: 8086:3ea0             Device-2: AMD Lexa PRO [Radeon RX 550/550X] vendor: Lenovo driver: amdgpu v: kernel             bus ID: 03:00.0 chip ID: 1002:699f             Display: x11 server: X.Org 1.19.6 driver: ati,modesetting FAILED: amdgpu             unloaded: fbdev,vesa tty: N/A             OpenGL: renderer: Mesa DRI Intel HD Graphics (Whiskey Lake 3x8 GT2)             v: 4.5 Mesa 19.2.0-devel (git-9c59751 2019-08-10 bionic-oibaf-ppa) compat-v: 3.0             direct render: Yes[/FONT]
I don't quite understand why it shows amdgpu as "FAILED", could this have something to do with my issues?

---

### Post by mastablasta on 2019-08-12
how did you use prime and how did you implement it?

---

### Post by chelseainspace on 2019-08-12
I tried to use it as a command that is executed on game startup (added "DRI_PRIME=1 %command%" as Launcher Options in Steam properties) and use the built in option to always use the dGPU on Lutris when starting programs through that.

---

### Post by mastablasta on 2019-08-13
[https://wiki.archlinux.org/index.php/PRIME#PRIME_GPU_offloading](https://wiki.archlinux.org/index.php/PRIME#PRIME_GPU_offloading)

it says you need to offload it.

> [FONT=sans-serif]GPU-intensive applications should be rendered on the more powerful discrete card. The command [/FONT]xrandr --setprovideroffloadsink provider sink[FONT=sans-serif] can be used to make a render offload provider send its output to the sink provider (the provider which has a display connected). The provider and sink identifiers can be numeric (0x7d, 0x56) or a case-sensitive name (Intel, radeon).[/FONT]

have you done that?

more info also here: [https://askubuntu.com/questions/1038271/intel-amd-hybrid-graphics-ubuntu-18-04](https://askubuntu.com/questions/1038271/intel-amd-hybrid-graphics-ubuntu-18-04)

---

### Post by Yellow Pasque on 2019-08-13
Can you show the entire output from lspci?
```
sudo update-pciids
lspci
```

> During my attempts to get it running I was tinkering with the grub file as well as drivers
Be more specific. Did you add any parameters to your kernel boot line in /etc/default/grub? What drivers did you install/modify (other than adding the oibaf PPA)? Did you mess with the proprietary AMD drivers?

> I don't quite understand why it shows amdgpu as "FAILED", could this have something to do with my issues? 
Yes. Try loading the module manually and see what happens:
```
sudo modprobe -v amdgpu
```

---

### Post by chelseainspace on 2019-08-14
Here's my lspci output:

> 00:00.0 Host bridge: Intel Corporation Device 3e34 (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (Whiskey Lake)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 0b)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Cannon Point-LP Thermal Controller (rev 30)
00:14.0 USB controller: Intel Corporation Cannon Point-LP USB 3.1 xHCI Controller (rev 30)
00:14.2 RAM memory: Intel Corporation Cannon Point-LP Shared SRAM (rev 30)
00:16.0 Communication controller: Intel Corporation Cannon Point-LP MEI Controller #1 (rev 30)
00:1c.0 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #1 (rev f0)
00:1c.4 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #5 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #9 (rev f0)
00:1d.2 PCI bridge: Intel Corporation Device 9db2 (rev f0)
00:1d.4 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #13 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Cannon Point-LP LPC Controller (rev 30)
00:1f.3 Audio device: Intel Corporation Cannon Point-LP High Definition Audio Controller (rev 30)
00:1f.4 SMBus: Intel Corporation Cannon Point-LP SMBus Controller (rev 30)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Point-LP SPI Controller (rev 30)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
03:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Lexa PRO [Radeon 540/540X/550/550X / RX 540X/550/550X] (rev c0)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
05:00.0 Network controller: Intel Corporation Wireless-AC 9260 (rev 29)
07:00.0 Non-Volatile memory controller: SK hynix Device 1327


As far as grub is concerned I changed the line
"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash""
to
"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amdgpu.dpm=1""

I need to mention that since then I had to restore an old Timeshift snapshot of mine and so the grub line was restored to the aforementioned default.

The thing about the drivers is, I am not entirely sure. I do think I currently have the amdgpu drivers installed (again, restoring did change some things and I did not install any additional drivers again afterwards). As far as I can tell, using "sudo modprobe -v amdgpu" did not do or change anything.

Edit: Since I had to reset the system and reinstall amdgpu drivers, they are not listed as "FAILED" in my System Info anymore.

---

### Post by Yellow Pasque on 2019-08-15
> **chelseainspace said:**
> Edit: Since I had to reset the system and reinstall amdgpu drivers, they are not listed as "FAILED" in my System Info anymore.

Okay, so the device shows up in lspci and kernel module/driver is loaded. So now, check:
```
DRI_PRIME=1 glxinfo -B
```

---

### Post by chelseainspace on 2019-08-16
okay here's the output I get from said command:

> name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: X.Org (0x1002)
    Device: Radeon 500 Series (POLARIS12, DRM 3.27.0, 5.0.0-23-generic, LLVM 9.0.0) (0x699f)
    Version: 19.2.0
    Accelerated: yes
    Video memory: 2048MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.5
    Max compat profile version: 4.5
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
Memory info (GL_ATI_meminfo):
    VBO free memory - total: 2034 MB, largest block: 2034 MB
    VBO free aux. memory - total: 3054 MB, largest block: 3054 MB
    Texture free memory - total: 2034 MB, largest block: 2034 MB
    Texture free aux. memory - total: 3054 MB, largest block: 3054 MB
    Renderbuffer free memory - total: 2034 MB, largest block: 2034 MB
    Renderbuffer free aux. memory - total: 3054 MB, largest block: 3054 MB
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 2048 MB
    Total available memory: 5120 MB
    Currently available dedicated video memory: 2034 MB
OpenGL vendor string: X.Org
OpenGL renderer string: Radeon 500 Series (POLARIS12, DRM 3.27.0, 5.0.0-23-generic, LLVM 9.0.0)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 19.2.0-devel (git-0f3768b 2019-08-12 bionic-oibaf-ppa)
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.5 (Compatibility Profile) Mesa 19.2.0-devel (git-0f3768b 2019-08-12 bionic-oibaf-ppa)
OpenGL shading language version string: 4.50
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 19.2.0-devel (git-0f3768b 2019-08-12 bionic-oibaf-ppa)
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20


Another question I have is, how would I find out which GPU an application I'm running is currently using, so I can actually double check if it worked?

---

### Post by Yellow Pasque on 2019-08-17
Yes, the output shows DRI_PRIME works. If you want to run a program on the AMD GPU, use DRI_PRIME=1 as you did with the glxinfo command.

> Another question I have is, how would I find out which GPU an application I'm running is currently using, so I can actually double check if it worked? 

There's a utility called radeontop available in the repos that should do what you want.

---

### Post by chelseainspace on 2019-08-19
> **Yellow Pasque said:**
> Yes, the output shows DRI_PRIME works. If you want to run a program on the AMD GPU, use DRI_PRIME=1 as you did with the glxinfo command.



There's a utility called radeontop available in the repos that should do what you want.

This is the output I get when starting radeontop:
> amdgpu DRM driver is used, but amdgpu VRAM size reporting is not enabled
amdgpu DRM driver is used, but amdgpu VRAM usage reporting is not enabled
Failed to get VRAM usage, kernel likely too old
Unknown Radeon card. <= R500 won't work, new cards might.
Collecting data, please wait....


In the resource screen afterwards everything stays at 0.00% when I try to run a game using PRIME; apparently my card does not work with this program as I'm using an RX550.

---

### Post by Yellow Pasque on 2019-08-20
> apparently my card does not work with this program as I'm using an RX550. 

Hmm, you may need a newer version to recognize your card, or maybe the hybrid graphics has the program confused. I wouldn't worry too much about it. As long as DRI_PRIME glxinfo shows information for the AMD GPU, you should be confident that using DRI_PRIME runs programs on the AMD GPU.

---

### Post by chelseainspace on 2019-08-21
I really am not sure about that, I tried playing League of Legends through Lutris (with DRI_PRIME enabled) and I get 40 fps on the very lowest settings in Full HD... On Windows I got 120+ fps on highest settings with the same hardware, is it really possible that the game runs more than 5 times better under Windows? I am really frustrated right because this makes literally anything unplayable, even CSGO which runs natively on Linux gets 30-40 fps at best on lowest settings, I doubt it is really using the RX550 with those results.

---

### Post by Yellow Pasque on 2019-08-21
> I tried playing League of Legends through Lutris (with DRI_PRIME enabled) and I get 40 fps on the very lowest settings in Full HD

I've read plenty of reports on poor performance using DRI_PRIME with a discrete AMD GPU. I'm sorry I don't have a solution for you.

---

