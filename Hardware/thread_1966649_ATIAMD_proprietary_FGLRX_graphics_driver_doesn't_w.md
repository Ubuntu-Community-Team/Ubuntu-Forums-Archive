---
title: "ATI/AMD proprietary FGLRX graphics driver doesn't work"
date: 2012-04-27
forum: Hardware
---

### Post by clement.analogue on 2012-04-27
Hi,

The installation of "ATI/AMD proprietary FGLRX graphics driver (post-release updates)" doesn't work on Ubuntu x64 12.04 (and 11.10) with an ATI Radeon Mobility HD 5400 on a laptop HP Pavillon dv7-4176sf. The logs :

```
2012-04-26 17:26:57,579 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-04-26 17:27:20,726 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-26 17:27:20,727 DEBUG: fglrx_updates is not the alternative in use
2012-04-26 17:27:20,753 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-04-26 17:27:20,753 DEBUG: fglrx_updates is not the alternative in use
```If I install fglrx-updates with apt-get, then I run

```
$ sudo aticonfig --initial -f
Uninitialised file found, configuring.
PowerXpress info: Diagnostic output from /usr/lib/fglrx/switchlibglx:
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.

Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-2
```If I install the "ATI/AMD proprietary FGLRX graphics driver", There isn't error, but the 3D seems to not work anymore. For instance, I can't run gnome-shell.

```
$ fglrxinfo 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
``````
$ fgl_glxgears 
Using GLX_SGIX_pbuffer
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
```For Ubuntu 11.04, I solved the problem with the catalyst driver on AMD website. Since Ubuntu 11.10, this driver breaks everything. The installation seems to end well, but when I reboot, the system stops when the graphic session starts, no tty available. If I turn off then turn on the laptop (not simply reboot), I can run th recovery mode, but I can't uninstall the catalyst driver, so I install Ubuntu again from scratch.

```
$ lspci|grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series]
``````
$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: Manhattan [Mobility Radeon HD 5400 Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:46 memory:a0000000-afffffff memory:c4400000-c441ffff ioport:4000(size=256) memory:c4440000-c445ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:5050(size=8)

``````
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise
``````
$ uname -a
Linux laptop 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
``````
$ xrandr
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192
LVDS1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 382mm x 215mm
   1600x900       60.1*+
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by mvmacd on 2012-04-27
Doesn't work for me either [the 'post release' updated one].  Here is the log when trying to install that:
[http://pastebin.com/YgANe4hF](http://pastebin.com/YgANe4hF)

When I install the non-post-updated version, it installs.  But then I went to Youtube and it would not play in sync and was choppy.

Then I go to Settings > Details > Overview and it says 

Graphics  VESA: SUMO

I have ubuntu 12.04, HP Pavillion DV6-1149wm with A6-3400m cpu w/ Radeon graphics

edit: 
```

$ fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6520G
OpenGL version string: 4.2.11627 Compatibility Profile Context

```

---

### Post by ssm2017 on 2012-04-27
hello
im having the same problem.
trying to install the post-fixes version returns an error and when installing the release version, when restarting, no screen anymore and no tty available.

```

lspci|grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV630 [Mobility Radeon HD 2600 XT]

```

```

sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: RV630 [Mobility Radeon HD 2600 XT]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:47 memory:c0000000-cfffffff memory:d0620000-d062ffff ioport:3000(size=256) memory:d0600000-d061ffff

```

```

lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise

```

```

uname -a
Linux inux 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

```

xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192
DVI-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1680x1050+0+0 (normal left inverted right x axis y axis) 433mm x 270mm
   1680x1050      60.0*+
   1400x1050      60.0  
   1280x1024      59.9  
   1440x900       59.9  
   1280x960       59.9  
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
DIN disconnected (normal left inverted right x axis y axis)

```

---

### Post by Yellow Pasque on 2012-04-27
To OP: you have hybrid intel/AMD graphics, so you should not be installing Catalyst/fglrx

To others: the "post-fixes" fglrx-updates package is the same as the regular fglrx package since Ubuntu 12.04 was just released..

---

### Post by mvmacd on 2012-04-27
> **Temüjin said:**
> To OP: you have hybrid intel/AMD graphics, so you should not be installing Catalyst/fglrx

To others: the "post-fixes" fglrx-updates package is the same as the regular fglrx package since Ubuntu 12.04 was just released..

Are you talking about the 'post-release updates' driver in the "Additional Drivers" ?
They can't be the same because only the non-post-release driver will install.

Also, even if it was, would that explain why Youtube plays back worse than when I was on 11.04?  Also the effects are kind of choppy, and google maps is quirky.

---

### Post by clement.analogue on 2012-04-29
I updated some informations in the first message.

> **Temüjin said:**
> To OP: you have hybrid intel/AMD graphics, so you should not be installing Catalyst/fglrx

You mean I should ...
Actually, without the Catalyst driver, both graphic cards are on, so the battery empties very quickly. On Ubuntu 11.04, it worked fine. With the Catalyst driver, I could chose only one card. That's why I want to install the proprietary driver.

---

### Post by analyzer123 on 2012-04-29
See this topic:

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

it works for me. See my post in that topic near the end.

---

### Post by clement.analogue on 2012-04-29
I tired the how to of the first message, but it doesn't work with ATI 5000 graphic cards.

---

### Post by clement.analogue on 2012-05-27
up

---

### Post by clement.analogue on 2012-06-08
up

---

### Post by clement.analogue on 2012-06-10
Nobody ?

---

### Post by clement.analogue on 2012-07-28
I opened a bug on launchpad:

[https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/1021024](https://bugs.launchpad.net/xserver-xorg-driver-ati/+bug/1021024)

---

### Post by Icarus315 on 2012-07-29
I made the mistake of installing both fglrx and then installing fglrx updates through Jockey (Additional Drivers).  It thoroughly broke my system.  Neither could be uninstalled or reinstalled properly.  Luckily I had just installed Ubuntu so I just reinstalled it and then when it came time to add graphics drivers I just went with the .run driver package off of AMD's site.  I used the build package method with that one and it has since worked absolutely fine for myself.

In Jockey it should be made very clear that you should not have both of them installed at the same time.  It is not obvious when one is labeled as "updates."

---

### Post by QIII on 2012-07-29
Unforutunately, the -updates install often does not work properly.

Also unfortunately, jockey often does not work properly.

Installing fglrx (not fglrx-updates) via the command line generally works for ATI and ATI/ATI hybrids.  But Intel/ATI hybrid graphics are a can of worms.  Bot nVIDIA and ATI users have no end of problems with Intel hybrid graphics.

I have seen one thread on the forums where a user was able to get hybrid Intel/ATI to work, but other posters in the thread have not had good luck.

If you are interested in checking it out, the thread can be found [here](http://ubuntuforums.org/showthread.php?t=1930450/).

Don't hold your breath.

---

### Post by clement.analogue on 2012-07-29
[]("http://ubuntuforums.org/member.php?u=628170")In the thread you're talking about, it is specified that "[FONT=Arial][SIZE=2] The solution seems not to work with ATI 5xxx graphic cards, try at your own risk.". Well, that's true, it doesn't.[/SIZE][/FONT]

---

### Post by clement.analogue on 2012-07-29
I tried installation via jockey, command line, .run. Nothing works for me :/

---

### Post by QIII on 2012-07-29
> **clement.analogue said:**
> In the thread you're talking about, it is specified that "[FONT=Arial][SIZE=2] The solution seems not to work with ATI 5xxx graphic cards, try at your own risk.". Well, that's true, it doesn't.[/SIZE][/FONT]

True, that.  I apologize that I did not catch that earlier in one of your previous posts.  There are others with other cards for whom it does not work, too.

The fact still remains:  There seems to be a wide-spread problem in Intel hybrids for both users of ATI and nVidia graphics.  This is not specific to Ubuntu.  I've seen it on Arch and Gentoo forums as well.  There are users having problems with Intel/nVIDIA using Optimus.

Intel/ATI is not even Linux specific, as some Windows users are having the same problem.

The most workable solution in the general case for Linux seems to be using the open source Radeon driver and vga_switcheroo, which is probably what Temujin was getting at.

---

### Post by clement.analogue on 2012-07-29
Thank you very much. I didn't know vga_switcheroo!

---

### Post by Ruedii on 2013-02-27
You need to use the VGA switcher in aticonfig

For more information on how to do this type in the console:
aticonfig --help

---

