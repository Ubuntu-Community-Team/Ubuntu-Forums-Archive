---
title: "How do I determine if my video settings are optimal?"
date: 2018-03-03
forum: Hardware
---

### Post by accounts0 on 2018-03-03
I have Ubuntu 16.04.3 LTS installed with a KDE desktop. On a Dell Inspiron 5559 Laptop.

I know the laptop for some reason has 2x video adapters:

1)
AMD/ATI Sun XT Radeon HD 8670A / 8670M / 8690M / R5 M330

2)
Intel Corporation Sky Lake Integrated Graphics

I don't know which I'm using, what driver it's using, or if its settings can be adjusted to do better than it is now.

For example, I get these annoying screen artifacts that look like short lines of pixels tearing away & falling back onto the screen in another place, maybe 1mm or so away. It stays jumbled until I move the page or the window or change focus. I suspect this is due to the video adapter somehow. I tried to get a video of it with all the spots on the screen wiggling like a pile of ants, but the whole thing moves a little since my phone's not on a tripod. So the wiggling artifacts can't be seen.

Google Chrome doesn't appear to be helped by using hardware acceleration or not. Also, I use a 33" LCD over HDMI while the laptop's docked. The highest resolution I can seem to get with it is 1920x1080- more would be better if possible.

My knowledge on this is limited or outdated. I remember doing...
```

X -configure

```

...long ago & hoping it worked. Nowadays apparently we don't even need an xorg.conf !

---

### Post by thehipho on 2018-03-03
Paste the output of this in a terminal window?
```
inxi -G
```

---

### Post by accounts0 on 2018-03-03
> **thehipho said:**
> Paste the output of this in a terminal window?
```
inxi -G
```

```

[FONT=monospace][COLOR=#000000]$ inxi -G[/COLOR]
[COLOR=#5454FF]**Graphics: **[/COLOR][COLOR=#5454FF]**Card-1:**[/COLOR][COLOR=#B2B2B2] Intel Sky Lake Integrated Graphics[/COLOR]
[COLOR=#5454FF]**Card-2:**[/COLOR][COLOR=#B2B2B2] Advanced Micro Devices [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330][/COLOR]
[COLOR=#5454FF]**Display Server:**[/COLOR][COLOR=#B2B2B2] X.Org 1.18.4 [/COLOR][COLOR=#5454FF]**drivers:**[/COLOR][COLOR=#B2B2B2] ati,radeon,intel (unloaded: fbdev,vesa)[/COLOR]
[COLOR=#5454FF]**Resolution:**[/COLOR][COLOR=#B2B2B2] 1920x1080@60.00hz, 1920x1080@60.00hz[/COLOR]
[COLOR=#5454FF]**GLX Renderer:**[/COLOR][COLOR=#B2B2B2] Mesa DRI Intel HD Graphics 520 (Skylake GT2) [/COLOR][COLOR=#5454FF]**GLX Version:**[/COLOR][COLOR=#B2B2B2] 3.0 Mesa 17.4.0-devel

[/COLOR][/FONT]
```[FONT=monospace][COLOR=#B2B2B2]
[/COLOR]
[/FONT]

---

### Post by #&amp;thj^% on 2018-03-03
There are a few ways to see which card is currently being used and Driver:
1st. 
```
lshw -c video
```
2nd.
```
inxi -G
```
3rd. 
```
lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA
```
Ninja'd by thehipho

---

### Post by accounts0 on 2018-03-03
1st.
```
 $ lshw -c video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: Sky Lake Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:277 memory:d1000000-d1ffffff memory:b0000000-bfffffff ioport:f000(size=64) memory:c0000-dffff
  *-display
       description: Display controller
       product: Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 81
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:278 memory:c0000000-cfffffff memory:d0000000-d003ffff ioport:e000(size=256) memory:d0040000-d005ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
cb@VoyagerI:~$ sudo lshw -c video
[sudo] password for cb: 
  *-display               
       description: VGA compatible controller
       product: Sky Lake Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0                                                                                                                     
       version: 07                                                                                                                                    
       width: 64 bits                                                                                                                                 
       clock: 33MHz                                                                                                                                   
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom                                                                         
       configuration: driver=i915 latency=0                                                                                                           
       resources: irq:277 memory:d1000000-d1ffffff memory:b0000000-bfffffff ioport:f000(size=64) memory:c0000-dffff                                   
  *-display                                                                                                                                           
       description: Display controller                                                                                                                
       product: Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330]                                                                                        
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]                                                                                                 
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 81
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:278 memory:c0000000-cfffffff memory:d0000000-d003ffff ioport:e000(size=256) memory:d0040000-d005ffff

```
2nd.
```
 $ inxi -G
Graphics:  Card-1: Intel Sky Lake Integrated Graphics
           Card-2: Advanced Micro Devices [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330]
           Display Server: X.Org 1.18.4 drivers: ati,radeon,intel (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz, 1920x1080@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics 520 (Skylake GT2) GLX Version: 3.0 Mesa 17.4.0-devel

```
3rd. 
```
 $ lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Sky Lake Integrated Graphics [8086:1916] (rev 07) (prog-if 00 [VGA controller])

```

---

### Post by thehipho on 2018-03-03
I think it's Intel driver. To be sure could you also paste the output of:
```
glxinfo | grep OpenGL
```
and
```
xrandr --listproviders
```

---

### Post by accounts0 on 2018-03-03
```

[FONT=monospace][COLOR=#000000]$ glxinfo | grep OpenGL[/COLOR]
[COLOR=#FF5454]**OpenGL**[/COLOR][COLOR=#000000] vendor string: Intel Open Source Technology Center[/COLOR]
[COLOR=#FF5454]**OpenGL**[/COLOR][COLOR=#000000] renderer string: Mesa DRI Intel(R) HD Graphics 520 (Skylake GT2)  [/COLOR]
[COLOR=#FF5454]**OpenGL**[/COLOR][COLOR=#000000] core profile version string: 4.5 (Core Profile) Mesa 17.4.0-devel[/COLOR]
[COLOR=#FF5454]**OpenGL**[/COLOR][COLOR=#000000] core profile shading language version string: 4.50[/COLOR]
[COLOR=#FF5454]**OpenGL**[/COLOR][COLOR=#000000] core profile context flags: (none)[/COLOR]
[COLOR=#FF5454]**OpenGL**[/COLOR][COLOR=#000000] core profile profile mask: core profile[/COLOR]
[COLOR=#FF5454]**OpenGL**[/COLOR][COLOR=#000000] core profile extensions:[/COLOR]
[COLOR=#FF5454]**OpenGL**[/COLOR][COLOR=#000000] version string: 3.0 Mesa 17.4.0-devel[/COLOR]
[COLOR=#FF5454]**OpenGL**[/COLOR][COLOR=#000000] shading language version string: 1.30[/COLOR]
[COLOR=#FF5454]**OpenGL**[/COLOR][COLOR=#000000] context flags: (none)[/COLOR]
[COLOR=#FF5454]**OpenGL**[/COLOR][COLOR=#000000] extensions:[/COLOR]
[COLOR=#FF5454]**OpenGL**[/COLOR][COLOR=#000000] ES profile version string: [/COLOR][COLOR=#FF5454]**OpenGL**[/COLOR][COLOR=#000000] ES 3.2 Mesa 17.4.0-devel[/COLOR]
[COLOR=#FF5454]**OpenGL**[/COLOR][COLOR=#000000] ES profile shading language version string: [/COLOR][COLOR=#FF5454]**OpenGL**[/COLOR][COLOR=#000000] ES GLSL ES 3.20[/COLOR]
[COLOR=#FF5454]**OpenGL**[/COLOR][COLOR=#000000] ES profile extensions:
[/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]

[/COLOR][/FONT]```
$ xrandr --listproviders
Providers: number : 2
Provider 0: id: 0x66 cap: 0x9, Source Output, Sink Offload crtcs: 4 outputs: 3 associated providers: 1 name:Intel
Provider 1: id: 0x3f cap: 0x4, Source Offload crtcs: 0 outputs: 0 associated providers: 1 name:HAINAN @ pci:0000:01:00.0

```
[FONT=monospace]
[/FONT]

---

### Post by #&amp;thj^% on 2018-03-03
So i guess you figured from the above that Intel was being used here first.
You have a hybrid GPU set-up
Proprietary Radeon drivers are not supported in 16.04 and up. Forcing an install, or keeping them installed during an upgrade will cause issues, if you can even get them to install.

For now, 16.04 is using opensource AMD Drivers, but, they're not very good and not polished yet. Performance is also a huge issue. :(

Unfortunately for those of you using the AMD graphics, you need to wait, and use the Intel HD graphics (If you're lucky to have it>> and you do) until then.

---

### Post by accounts0 on 2018-03-03
Thanks for your help.

Is there any hope with the newer LTS upcoming this spring? You made it sound like it was on purpose that from 16.04 up the AMD driver is not going to work. Was that the explicit decision, or might it be resolved & end up working sometime in the (not so distant) future?

---

### Post by #&amp;thj^% on 2018-03-03
Well that's kind of trick question, everyone has been asking for non-proprietary video drivers, and to quote an old adage "Be careful what you wish for".
In a nut shell things are progressing to a new display server was going to be Mir now plans are for Wayland. So maybe the Term "On Purpose" might be a bit over the top.
But things are progressing slowly for the better>>>but it will be a work in progress for a short time, so high expectations might be disappointing ATM.

---

### Post by accounts0 on 2018-03-09
Is it possible to get whichever adapter I'm using to give me higher resolution than its current maximum as is displayed in the KDE System Settings? I vaguely remember years ago using boot parameters to get it higher. Framebuffer something something...

I use a 33" flatscreen over HDMI & even set to the max as it stands now, it doesn't seem as large, or spacious as I'd like it to be.

---

### Post by accounts0 on 2018-03-25
bump, but also another question.

Would it be reasonable to expect with the new LTS upcoming, that I might be able to increase the screen resolution higher than this version's current maximum? Interested in how to do that somehow...

---

