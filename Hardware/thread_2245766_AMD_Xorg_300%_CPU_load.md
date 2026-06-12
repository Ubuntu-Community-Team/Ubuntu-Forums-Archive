---
title: "AMD Xorg 300% CPU load"
date: 2014-09-25
forum: Hardware
---

### Post by andrew102 on 2014-09-25
Hi I would like to know why Xorg is idling around 12% then general tasks (firefox, desktop) is around 25% CPU.

When I use a video editing software (eg: openshot or Kazam desktop recorder) the CPU load registered by top jumps to 300% for that process.

I have attached screenshots.

---

### Post by QIII on 2014-09-25
Hello!

Which driver are you running?

---

### Post by andrew102 on 2014-09-25
Hey I just did a check and it says kernal driver: radeon 

Apparently this is the open source one? That's weird because I have "fglrx proprietry" selected in 'additional drivers'

---

### Post by QIII on 2014-09-25
Which release are you running?

---

### Post by andrew102 on 2014-09-26
Trusty - Unity

There's somthing up with it - reverts to open source somehow.

---

### Post by andrew102 on 2014-09-26
Some more info
  
*-display               
       description: VGA compatible controller
       product: Park [Mobility Radeon HD 5430/5450/5470]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:46 memory:c0000000-cfffffff memory:d0020000-d003ffff ioport:d000(size=256) memory:d0000000-d001ffff

---

### Post by QIII on 2014-09-26
Odd.

You may want to try installing the driver via the command line:

To install the driver available in the repo at the time of your release, check out the link in my signature and follow the instructions in:

2.1. Installing via the command line

When you are done, follow the instructions in:

4. Enabling Video Hardware Acceleration

---

### Post by andrew102 on 2014-09-26
OK I'm running through that now. I noticed I don't have an xorg.conf
Just:

xorg.conf.fglrx-0
xorg.conf.fglrx-1
xorg.conf.fglrx-2
xorg.conf.original-0
xorg.conf.original-1


**BTW** can you tell me if this is in** MB**?
resources: irq:46 memory:c0000000-cfffffff memory:d0020000-d003ffff ioport:d000**(size=256)** memory:d0000000-d001ffff 				

If it is only 256MB, that would be strange because it's actually 1GB onboard

---

### Post by andrew102 on 2014-09-26
I get an error:

```
sudo: aticonfig: command not found
```

```
sudo: amdconfig: command not found
```

Also it says before that is says: ```
update-initramfs: Generating /boot/initrd.img-3.13.0-36-generic
```


Shouldn't it be kernal 3.15 as I'm on 14.04.1

---

### Post by QIII on 2014-09-26
What does ```

fglrxinfo
``` return?

---

### Post by andrew102 on 2014-09-26
command not found

---

### Post by QIII on 2014-09-26
Well.  I can clearly say "Somethin' is wrong!:

:)

Let me hunt around the interwebz for a bit.  If I don't get back in a day or two, bump the thread.

---

### Post by andrew102 on 2014-09-26
Actually I think it is the kernal I am using.

```
cat /proc/version_signature
```
Ubuntu 3.13.0-36.63-generic 3.13.11.6

---

### Post by QIII on 2014-09-26
No, that's not it.

I'm using the same kernel.  That's what Trusty is up to right now.

---

### Post by andrew102 on 2014-09-26
I found this in the /var/log/Xorg.0.log
```

[    36.827] Loading extension GLX
[    36.827] (==) Matched fglrx as autoconfigured driver 0
[    36.827] (==) Matched ati as autoconfigured driver 1
[    36.827] (==) Matched fglrx as autoconfigured driver 2
[    36.827] (==) Matched ati as autoconfigured driver 3
[    36.827] (==) Matched modesetting as autoconfigured driver 4
[    36.827] (==) Matched fbdev as autoconfigured driver 5
[    36.827] (==) Matched vesa as autoconfigured driver 6
[    36.827] (==) Assigned the driver to the xf86ConfigLayout
[    36.827] (II) LoadModule: "fglrx"
[    36.880] (WW) Warning, couldn't open module fglrx
[    36.880] (II) UnloadModule: "fglrx"
[    36.880] (II) Unloading fglrx
[    36.880] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    36.880] (II) LoadModule: "ati"
[    36.880] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    36.885] (II) Module ati: vendor="X.Org Foundation"
[    36.885]    compiled for 1.15.1, module version = 7.3.0
[    36.885]    Module class: X.Org Video Driver

```

Seems like Xorg needs reconfiguring

---

### Post by andrew102 on 2014-09-26
[FONT=arial]So I went digging around in /usr/lib/xorg/modules/drivers and noticed there was no symlink to fglrx
[/FONT]
Found the solution here: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)
[B]
I've modified it for trusty[/B]

amdconfig: command not found After booting you might receive X error '(EE) Failed to load module  "fglrx" (module does not exist, 0)'. These do not necessarily indicate  that the installation has failed completely. On command line, do 
 
```
ls /usr/lib/fglrx/bin
```

and see if the command lists some Ati related programs. If they are  listed but not found from /usr/bin, it is possible that the  "update-alternatives" fglrx .deb installation does has been ignored. See  man update-alternatives for more information about the concept and  workings of alternatives. In practice, update-alternatives is supposed  to create several symbolic links to the files in the fglrx directory,  but it will be ignored if the alternatives for the very related gl_conf  entry has been set to manual. Do 

 ```
update-alternatives --get-selections | grep gl_conf
```

and see if the mode is manual instead of auto and if mesa is  mentioned instead of fglrx in the path that is printed. In this case you  need to  

 ```
sudo update-alternatives --set x86_64-linux-gnu_gl_conf_gl_conf /usr/lib/fglrx/ld.so.conf
```

to set fglrx as the active alternative. You can alternatively (no pun  intended) and additionally change the gl_conf into automatic mode  before the installation this way: 

 ```
sudo update-alternatives --auto x86_64-linux-gnu_gl_conf_gl_conf
```


Now I can run ```
sudo amdconfig --initial
```

Let's pray it works on reboot

---

### Post by andrew102 on 2014-09-26
```
Setting up fglrx (2:13.350.1-0ubuntu2) ...^M
update-alternatives:  using /usr/lib/fglrx/alt_ld.so.conf to provide  /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in  auto mode^M
Loading new fglrx-13.350.1 DKMS files...^M
First Installation: checking all kernels...^M
```

So their was still a symlink missing somewhere ask it booted into "low graphics mode" couldn't load module libatiuki.so.1



So I uninstalled and restarted again - this time I got:

```
Setting up fglrx (2:13.350.1-0ubuntu2) ...^M
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode^M
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode^M
update-initramfs: deferring update (trigger activated)^M
Loading new fglrx-13.350.1 DKMS files...^M
First Installation: checking all kernels...^M
Building only for 3.13.0-36-generic^M
Building for architecture x86_64^M
Building initial module for 3.13.0-36-generic^M
Done.^M
```

So I thought - yeah all good. Except now it boots to black screen after mounting.

Back to square one - guess I'll have to continue with the open source drivers.

---

### Post by QIII on 2014-09-26
After you installed it, did you remember to do

```
 sudo amdconfig --initial
```

Before rebooting?

If not, the black screen is not an unexpected result.

This can be corrected from recovery mode.

---

### Post by andrew102 on 2014-09-26
Yeah of course -- but even that doesn't fix up all the symbolic links for eg: had to manually make one for fglrx_dir.so

I've been using the recovery mode terminal to read the output of X.0.log and it runs into a segmentation fault (X crash). It's the same whether I use Ubuntu main or Amd 14.6 beta from their website.

Do you know how I can get R/W access from recovery mode?

---

### Post by andrew102 on 2014-09-26
Actually I'm having a similar problem as this thread except it gets to something similar to this line

```
(II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
```

EDIT: I just ctrl+c+v from the other thread - pretty sure my log was "unmapping" instead of "added"

---

