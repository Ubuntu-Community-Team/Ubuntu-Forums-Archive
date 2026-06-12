---
title: "ATI Radeon HD 5450 not working"
date: 2010-04-05
forum: Hardware
---

### Post by SB9784 on 2010-04-05
Having used Jaunty on and off for a while now on my laptop, I decided to install a fresh build of Karmic on my new desktop PC. I've had a few problems with this (the most annoying being the WLAN card not working!) but most of them I've fixed now after trawling for answers in the forums, but this one I just can't solve :-(...

Karmic doesn't appear to handle my graphics card very well (in fact it's pretty dire): I can't set the resolution higher than 1280x1024 (which looks seriously ugly on a monitor with a native resolution of 1920x1080) and I can't turn on any desktop effects (I think because the drivers aren't supporting it). Here's the output of lspci:

```
$ lspci | grep -i '\<ati\>'
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68f9
01:00.1 Audio device: ATI Technologies Inc Device aa68

```If I go to Preferences->display I get the following message:

> It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?...and trying to use the proprietary tool gives this error:

[ATTACH]152434[/ATTACH]

... and trying to run aticonfig gives this:

```

$ sudo aticonfig --initial
aticonfig: No supported adapters detected

```(I also get the same without the --initial option).

According to Administration->Hardware Drivers, my current active driver is a proprietary one called rt3090sta.

Many of the forums (fora?) I've seen on this sort of subject mention xorg.conf. I don't know anything about this file, except that I don't have one:

```

$ sudo find / -name 'xorg.conf'
$

```Any ideas? I'm fresh out (not to mention really disappointed in my first impression of Karmic!).

---

### Post by N92 on 2010-04-17
OK first what you need to do is go to ATI's site [here]("http://support.amd.com/us/gpudownload/Pages/index.aspx").
Then once you have downloaded the driver open the folder that it is in.
Then open the terminal and type _sudo nautilus_ you may need to type in your password.
next drag the file in the root folder.
Right click in the file then select permissions next click on the make executable box.
now double click on the file select run and follow the steps.

ps DO NOT ACTIVATE THE DRIVERS IN SYSTEM<ADMINISTRATION<HARDWARE DRIVERS!
this messes up the other driver you just installed.

Hope this helps

---

### Post by Yellow Pasque on 2010-04-17
Yeah, you'll need to install the Catalyst package from ATI's site, but since you just did a fresh install, I would recommend trying again, but using Lucid this time. The ATI proprietary driver that comes with Lucid is more current than anything offered to the general public.

> According to Administration->Hardware Drivers, my current active driver is a proprietary one called rt3090sta.
That's a driver for a wireless device, not a video driver.

---

### Post by SB9784 on 2010-04-18
Thanks for your replies - I downloaded the ATI Catalyst package as mentioned in the earlier posts and ran it from a terminal as root. After following the instructions I was prompted for a restart - and everything worked fine after that!

---

### Post by xefyr on 2010-04-21
I have the same card (same entries in lspci). I've downloaded the driver file as described but I'm presented with an error when running it:
> ERROR: vcdk is missing. Installation aborted.
Is anyone familiar with this error and it's resolution? I've not found anything of interest from web searches.

Thanks.

---

### Post by xefyr on 2010-04-21
I found this post [1], translated it. I now have a working install of 9.10 with a radeon hd 5450 using the ati catalyst driver 10.3.

[1] [http://forum.ubuntu-it.org/index.php/topic,155477.msg1030020.html#msg1030020](http://forum.ubuntu-it.org/index.php/topic,155477.msg1030020.html#msg1030020)

---

### Post by DrSkylaser on 2010-11-11
I followed the steps in 2, but something went wrong. . . install-log says

[Error] Kernel Module : Failed to build fglrx-8.732 with DKMS
[Error] Kernel Module : Removing fglrx-8.732 from DKMS

so what d'I do now?

---

### Post by petebarchetta on 2012-02-28
Can anyone confirm this as working in 11.04 / 11.10?

---

### Post by collisionystm on 2012-02-28
> **petebarchetta said:**
> Can anyone confirm this as working in 11.04 / 11.10?


Download a Live-CD and give it a shot.

There have been alot of Radeon HD problems but they will be sorted out in 12.04.

---

### Post by ahallubuntu on 2012-02-28
> **petebarchetta said:**
> Can anyone confirm this as working in 11.04 / 11.10?

I recently picked up an HD 5450 (Asus card) for a home media server running Ubuntu 10.10 32 bit.  It had previously been running an ATI 4350 card successfully using AMD's proprietary driver, and this same driver worked automatically for the 5450.  

So I assume 11.04 will work for sure.  11.10?  Maybe - with the 3.0 kernel who knows if the proprietary driver still works/has been updated/is even needed anymore?

---

### Post by bambrozio on 2012-05-23
...

---

### Post by bambrozio on 2012-05-23
First, sorry for my terrible English, I'm learning yet...

So, I updated my Ubuntu (11) for latest version (12), but my monitors stopped working correctly...

I have two monitors whose both are connected on my CPU by DVI port with 2 VGA cable (1DVI on PC to 2 ports VGA (monitors))
Before I install this OS, was working good, but now, they are only in mirror form... I can't use extensible..

I alrady did what you put here about the drivers, but the problem remains...

Some util information:

> $ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Cedar PRO [Radeon HD 5450]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:49 memory:d0000000-dfffffff memory:fe620000-fe63ffff ioport:e000(size=256) memory:fe600000-fe61ffff

> $ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Cedar PRO [Radeon HD 5450] [1002:68f9]

> $ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1280x960       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       75.0     60.0  
   1280x720       75.0     60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
CRT2 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0 +   75.0* 
   1280x960       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       75.0     60.0  
   1280x720       75.0     60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9

Some try and errors which I had:

in "All Settings" > "Displays":

When I remove the Mirror displays' option, the errors occurs:

fist one:

> The selected configuration for displays could not be applied
required virtual size does not fit available size: requested=(2560, 1024), minimum=(320, 200), maximum=(1600, 1600)

And when I clik on close button, other one:
> Failed to apply configuration:%s
GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3: required virtual size does not fit available size: requested=(2560, 1024), minimum=(320, 200), maximum=(1600, 1600)

No matter if I change the "Resolution" options in any monitors configurations...

When I selected the "Additional Drivers", is showed 2 options to be activated:

> ATI/AMD proprietary FGLRX graphics driver (post-release updates)
ATI/AMD proprietary FGLRX graphics driver

The second ok, but when I active the first one, reboot my OS, a error occours:

> Sorry, installation of this driver failed.
Please have a look at the log file for details: /var/log/jockey.log

And in the file jockey.log:

> 2012-05-23 08:36:53,900 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-23 08:36:53,900 DEBUG: fglrx_updates is not the alternative in use
2012-05-23 08:36:53,922 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-23 08:36:53,922 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-23 08:36:54,057 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-23 08:36:54,057 DEBUG: fglrx_updates is not the alternative in use
2012-05-23 08:36:54,092 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-23 08:36:54,093 DEBUG: fglrx_updates is not the alternative in use
2012-05-23 08:36:54,116 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-23 08:36:54,116 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-23 08:36:56,149 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-23 08:36:56,149 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2012-05-23 08:36:56,632 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-23 08:36:56,632 DEBUG: fglrx_updates is not the alternative in use
2012-05-23 08:36:58,112 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-23 08:36:58,113 DEBUG: fglrx_updates is not the alternative in use
2012-05-23 08:37:01,329 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2012-05-23 08:37:19,822 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-23 08:37:19,822 DEBUG: fglrx_updates is not the alternative in use
2012-05-23 08:37:19,835 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-05-23 08:37:19,835 DEBUG: fglrx_updates is not the alternative in use

Does anyone know what might be going wrong?

thanks!

---

### Post by bambrozio on 2012-05-24
Hi folks!
I found the answer!

In my case, there was a thing that passed me by unnoticed!
So, the displayer configuration shouldn't be by "System Settings >All Settings > Displays", but by "AMD Catalyst Control Center (Administrative)".

When you active the "ATI/AMD proprietary FGLRX graphics drive" (it's no necessary (and in my case, impossible) active the "post release update" version) this software will be installed!

So, all that you need to do is configure the displays as well other options which you wish.

---

