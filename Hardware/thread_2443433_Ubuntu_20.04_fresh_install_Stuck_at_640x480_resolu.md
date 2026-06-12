---
title: "Ubuntu 20.04 fresh install Stuck at 640x480 resolution"
date: 2020-05-15
forum: Hardware
---

### Post by tklat on 2020-05-15
My system:
CPU: Intel E7200 Core2Duo
Motherboard: ECS GF7050VT-M (GeForce 7050/nForce 610i chipset)
Using onboard graphics VGA port
Samsung SyncMaster 713V monitor (capable of 640x480, 800x600, 1024x768, 1152x768, 1280x1024)
4 GB RAM
Ubuntu 20.04 installed

I am stuck with a resolution of 640 x 480. Obviously, this make using the GUI almost impossible.

To get 20.04 installed from the DVD ISO, I had to use the "nomodeset" option. Now, I can't change resolution and my monitor is listed as "Unknown Display".

Some things I have done:
```
inxi -G
```
and the result:
```

Graphics:[INDENT]Device-1: NVIDIA C73 {GeForce 7050 /nForce 610i}[/INDENT]
[INDENT]driver: N/A[/INDENT]
[INDENT]uploaded: modesetting,vesa resolution: 640x480~73Hz[/INDENT]
[INDENT]OpenGL: renderer: llvmpipe (LLVM 9.0.1 128 bits)[/INDENT]
[INDENT]v: 3.3 Messa 20.0.4[/INDENT]

```

Then I ran:
```
inxi -F
```
and the result:
```

System:[INDENT]Host: MySystem Kernel: 5.4.0-29-generic x86_64 bits: 64
Desktop: Gnome 3.36.1 Distro: Ubuntu 20.04 LTS (Focal Fossa)[/INDENT]
Machine:[INDENT]Type: Desktop Mobo: ECS model: GF7050VT-M v: 1.0
serial: <superuser/root required> BIOS: American Megatrends
v: 080015 date: 04/07/2008[/INDENT]
Graphics:[INDENT]Device-1: NVIDIA C73 [GeForce 7050 / nForce 610i] driver: N/A
Di9splay: x11 server: X.Org 1.20.8 driver: fbdev,nouveau
unloaded: modesetting,vesa resolution: 640x480~73Hz
OpenGL: renderer: llvmpipe (LLVM 9.0.1 128 bits)
v: 3.3 Messa 20.0.4
[/INDENT]

```

Next, I looked at grub:
```
sudo nano /etc/default/grub
```

and the result (*those lines that were not commented*):
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_DISTRIBUTOR='lsb_release -i -s 2> /dev/null || echo Debian'
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

Finally:
```
[COLOR=#000000][FONT=&amp]cat /proc/driver/nvidia/version[/FONT][/COLOR]
```

and the result:
```
No such file or directory
```

So, it appears that I may need to install appropriate Nvidia drivers. How do I do that?

Thanks in advance!

---

### Post by CelticWarrior on 2020-05-15
Welcome.

Yes, it needs Nvidia drivers for proper performance but unfortunately there are no such drivers still compatible with current kernels.
Nvidia dropped support for your hardware a long time ago.

---

### Post by mörgæs on 2020-05-16
You need a supported kernel which accepts the Nvidia 304 driver. Ubuntu 16.04 is an option for a little less than a year to come.

---

### Post by CelticWarrior on 2020-05-16
> **mörgæs said:**
> Ubuntu 16.04 is an option for a little less than a year to come.

Yes, but it needs to be the original one with the LTS kernel. Compatibility was broke already with 16.04.2.

IMO, the cheapest discrete graphics card you can find, even second hand on eBay, is a better solution.

---

### Post by tklat on 2020-05-16
Morgaes, 
I tried Ubuntu 16.04.6 (downloaded ISO from the Ubuntu website) last night. And, as CelticWarrior points out, it did not work. So, I purchased an Nvidia GeForce 7200 GS video card off of eBay for $5.

I know this card works as I have one in my current Ubuntu 18.04 LTS server. I was just hoping to get away with using the motherboard's on-board video but, it looks like that is a no-go. 

Thanks for all the help and I will report back once I have it up and running.:)

---

### Post by CelticWarrior on 2020-05-16
An headless server doesn't require any special graphics.
Unfortunately, the Geforce 7200GS uses the same driver that the integrated one, so same problem, but it may work better with the nouveau driver.

---

### Post by tklat on 2020-05-17
Ruh-roh...I didn't think about that. :(

My Ubuntu 18.04 LTS server with the GeForce 7200 GS does run headless. I ssh into it to do everything and, before I did, it was just text on a screen. It looks like I might be turning this machine into a headless server as well.

So that I can know better next time, how do I find out which Nvidia drivers support specific Nvidia video cards?

---

### Post by CelticWarrior on 2020-05-17
Their website nvidia.com has a search feature for all Nvidia card/chipset models. It shows the newest driver version that can be used for any given model.

As of now the oldest driver that still works with current (and supported) kernels is 340, so the oldest thing you can still use with the intended performance must be covered by that driver version.

---

### Post by tklat on 2020-05-17
OK, on Nvidia's website, i see that driver 304.137 (not 340 :() supports the Nvidia GeForce 7200 GS. I need at least an Nvidia GeForce "8" series to be able to use the 340 driver.

[https://www.nvidia.com/Download/driverResults.aspx/123709/en-us](https://www.nvidia.com/Download/driverResults.aspx/123709/en-us)

[TABLE="width: 50%"]
[TR]
[/TR]
[TR]
[TD="class: contentsummaryleft"]Version:[/TD]
[TD="class: contentsummaryright, colspan: 2"]304.137[/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]Release Date:[/TD]
[TD="class: contentsummaryright, colspan: 2"]2017.9.19[/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]Operating System:[/TD]
[TD="class: contentsummaryright, colspan: 2"]Linux 64-bit[/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]Language:[/TD]
[TD="class: contentsummaryright, colspan: 2"]English (US)[/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"]File Size:[/TD]
[TD="class: contentsummaryright, colspan: 2"]66.84 MB[/TD]
[/TR]
[/TABLE]

[COLOR=#00ff00]**GeForce 7 Series:**[/COLOR][COLOR=#000000]GeForce 7025 / NVIDIA nForce 630a, GeForce 7050 PV / NVIDIA nForce 630a, GeForce 7050 / NVIDIA nForce 610i, GeForce 7050 / NVIDIA nForce 630i, GeForce 7100 / NVIDIA nForce 630i, GeForce 7100 / NVIDIA nForce 620i, GeForce 7100 GS, GeForce 7150 / NVIDIA nForce 630i, GeForce 7300 SE / [/COLOR]**[COLOR=#ff0000]7200 GS[/COLOR]**[COLOR=#000000], GeForce 7300 LE, GeForce 7300 GS, GeForce 7300 GT, GeForce 7350 LE, GeForce 7500 LE, GeForce 7550 LE, GeForce 7600 LE, GeForce 7600 GS, GeForce 7600 GT, GeForce 7650 GS, GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 GTX, GeForce 7800 SLI, GeForce 7900 GS, GeForce 7900 GT/GTO, GeForce 7900 GTX, GeForce 7950 GT, GeForce 7950 GX2

[/COLOR]And now I see how to determine which Nvidia card will work with the 340 driver. Rumaging around in my old parts box, it looks like I have a MSI NX 8600 GTS that will work with the 340 drivers so, I guess I could use it instead. At least the eBay 7200 GS was cheap and it can always be my back-up (if the other 7200 GS currently in my 18.04 LTS server should ever die).

Note to self: Check your Nvidia card driver requirements before your next Ubuntu build.

---

### Post by mörgæs on 2020-05-18
- or go for AMD. They are generally speaking better at supporting open source.

---

