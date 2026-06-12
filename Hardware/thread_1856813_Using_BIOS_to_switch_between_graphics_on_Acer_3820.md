---
title: "Using BIOS to switch between graphics on Acer 3820TG"
date: 2011-10-09
forum: Hardware
---

### Post by Kakitus on 2011-10-09
Hello guys,
I've owned my ACer 3820TG for over a year now, but only recently I decided to switch to Ubuntu. I hope you will be able to help me with the following problem:

I've been using Ubuntu 11.04 on "dedicated only" mode with fglrx for over a month. Because from now on I'm planning to use the notebook on battery frequently , I followed [this guide]("http://forum.notebookreview.com/7214705-post9986.html") and unlocked the "Intel only" mode. Due to the fglrx drivers, however, the system does not boot up in IGP-mode. I just end up at a Linux terminal. Switching over to PEG (i.e. dedicated only) solves that problem. But by doing so I'm stuck with the ATI HD5650 again.

I would love to be able to choose between the two cards in BIOS. For that to work, however, the linux drivers would have to support both ATI and Intel. That does not seem to be the case with fglrx.

Do you know of any linux driver that could do that?

Solving this problem is crucial to my staying with Ubuntu.

Thank you very much in advance

---

### Post by matt_symes on 2011-10-09
Hi

This is interesting. You might be able to boot into vesa mode when using the intel card. That would get you to a desktop if you can. You can do this with a kernel line switch.

In the first instance, with the ati graphics card enabled, open a terminal and type

```
sudo lshw -c video
```Enter your password. It will not be echoed to the screen. Post the results back here between code tags.

Next, change the card to intel and reboot to the command line. This will be a pain but i am interested in this information as well.

login in and then also type

```
sudo lshw -c video
```Either type of the results manually into your next post or redirect it to a file

```
sudo lshw -c video > ~/intel_gcard_data
```You can then boot back into ATI graphics, open the file and copy  it into your next post.

[noparse]```
Remember to use code tags like this.
```[/noparse]

```
Remember to use code tags like this.
```Kind regards

---

### Post by Kakitus on 2011-10-09
Hey

this is the output I got with ATI enabled
```

  *-display               
       description: VGA compatible controller
       product: Redwood [Radeon HD 5600 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:45 memory:d0000000-dfffffff memory:cfee0000-cfefffff ioport:2000(size=256) memory:cfe00000-cfe1ffff

```

and this the one with Intel enabled:
```

  *-display               
       description: VGA compatible controller
       product: Core processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 18
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm  vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:f0000000_f03fffff d0000000-dfffffff ioport:1800(size=8)

```

Booting up in recovery mode with failsafe graphics works - without any hardware acceleration, however.

Do you suppose there's any other way to use the IGP?

Thanks in advance and best regards,

Kakitus

---

### Post by matt_symes on 2011-10-09
Hi

Well it's good because you cards are both being recognised when the other is disabled.

> Booting up in recovery mode with failsafe graphics works - without any hardware acceleration, however.That make sense because that is vesa mode. There will be no hardware acceleration but it will work on almost all cards. You can also get to that mode using a kernel command line switch.

*EDIT: Saying the above i have just noticed this driver=i915 for the intel card.*

I assume the reason it does not work with the intel card when you boot up normally is because you have an xorg.conf file.

Please post the output of

```
cat /etc/X11/xorg.conf
```> Do you suppose there's any other way to use the IGP?Maybe. Let's have a look at your xorg.conf file first (if you have one).

Kind regards

---

### Post by Kakitus on 2011-10-10
Hey

this is the output I get:

```
ari@ari-laptop:~$ cat /etc/X11/xorg.conf
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1366 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	Option	    "Monitor-DFP1" "0-DFP1"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3286 1920
		Depth     24
	EndSubSection
EndSection

```

I hope it helps

Best Regards,
Kakitus

---

### Post by matt_symes on 2011-10-10
Hi

Your xorg.conf file is specific to your ATI graphics card and loads the drivers for that.

I suspect that is why you can only run your Intel card in failsafe mode. I am not 100% sure but i suspect that failsafe mode does not read your xorg.conf file when booting and using your Intel card.

What i suspect is you may need to have is two xorg.conf files that you can switch between when you boot between your graphics cards.

I am also not sure how kernel mode setting affects this. My supposition is that kernel mode setting detects your graphics card and the xorg.conf file applies any extra settings to make your card run optimally.

We could try some things, however your system would be a test system as i am not 100% sure how to proceed without doing some research to see if it's possible.

I would highly suggest backing up your system before we even attempt any changes. You would also have to be comfortable with the command line in case things go wrong.

What are your thoughts about this ?

Also, i am very interested in the thoughts of others on this matter. If anybody has any ideas, suggestions then please don't hesitate to speak up. Your input would be most welcome here.

EDIT:

There is some interesting info here about failsafe graphics mode.

[https://wiki.ubuntu.com/BulletProofX](https://wiki.ubuntu.com/BulletProofX)

Can you, with your Intel card running, open a terminal and type
```

xrandr
``` and

```
cat /proc/cmdline
```
Please post back the results.

Kind regards

---

### Post by Kakitus on 2011-10-11
Hey

I won't be able to try out any changes this week because I am about to take part in a major exam, so I can't risk bricking my OS. Thank you for your help up to this point, however. I'll gladly try out any steps your propose next week.


Best regards,

Kakitus

---

### Post by matt_symes on 2011-10-11
Hi

I totally understand. Good luck in your exam!

Post back when you are ready. I am subscribed to this thread.

Kind regards

---

### Post by favt on 2013-03-28
Is the actually?
I have this problem and how boot in IGP with Unity3D i not found this answer. :(

---

