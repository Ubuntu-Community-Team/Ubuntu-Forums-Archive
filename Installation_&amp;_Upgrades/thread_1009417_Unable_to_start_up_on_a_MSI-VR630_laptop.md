---
title: "Unable to start up on a MSI-VR630 laptop"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by nick_nitro on 2008-12-12
hi,

After much problems i managed to install ubuntu with a alternate install cd on a MSI-VR630 [http://global.msi.eu/index.php?func=prodtmpspec&maincat_no=135&cat2_no=&cat3_no=&prod_no=1650#menu]("http://global.msi.eu/index.php?func=prodtmpspec&maincat_no=135&cat2_no=&cat3_no=&prod_no=1650#menu") .
now after installation i can't start up ubuntu i've tried different options for vga and noapic but no luck :( .
When i trie to start the screen turns black after loading the networkcard(networkcard loads OK) and the computer locks up no hd act.

i tried other distro's but no luck debian,fedora,mandriva.
I need it to run ubuntu cos it's a portable for a linux novice and i think ubuntu is the best distro at the moment.

the only distro that runs wihtout a problem is elive(debian based) i can access the files and folders of my installed ubuntu 8.10 distro.

can sombody help me with getting ubuntu 8.10 running?

thanks

---

### Post by cssanyi on 2008-12-13
So nice to hear it. :) I say it because I also have an MSI VR630 notebook. I've bought it today, I a was very disappointed when I didn't manage to run any linux OS on it. I tryed OpenSuse, Mandriva 2008 Live, Ubuntu 8.10 and 7.10 with no success. I also managed to install Ubuntu 8.10 with an alternate cd, but it didn't start. It simply turns black, and the computer becames silent.
It stops at seeing hardware drivers. 

I've tried it with special start modes (Ubuntu Live CD 8.10). I am a beginner, so I simply turned everything off. There was something different with ACPI turned off. A prompt appeared, but I couldn't do anything there (as I said, I am a beginner).

There is a seting in BIOS/Advanced menu called AHCI DID for Linux. I do not know what does it mean. It has some connection with SATA. When I had set it to Enable nothing has changed, but Windows XP wasn't able to boot. Maybe it is not importaint, I just want to give some tips without the needed technical becground (from my side). :-(

I really hope, we will find some solution to the problem. I don't want to use Windows or Vista. It froze down several times on the first day.

---

### Post by cssanyi on 2008-12-15
No one, who could help? :confused:

---

### Post by esanya on 2008-12-16
Hi!

I got this type of notebook yesterday. I'm now downloading the elive 1.9.20. Was this the distro which run without problems?

I suspect a difference in the kernels (between ubuntu and elive)...

I have found lots of topics on the ubuntu forums with 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222176](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222176)

+etc...

Regrads,
Sandor

---

### Post by nick_nitro on 2008-12-17
> **esanya said:**
> Hi!

I got this type of notebook yesterday. I'm now downloading the elive 1.9.20. Was this the distro which run without problems?



yes that is the one that runs without problems and has al the drivers(webcam,wifi,....).

---

### Post by Bristow_69 on 2008-12-27
Hello ;)

I'm french...

I bought this laptop with ubuntu pre-installed.

I think it runs only in 64 bits. I've intrepid on it. I've only 3 littles bugs :
[LIST=1]
[*]front mic doesn't work (near webcam)
[*]when i plug headset, sound isn't mute on speakers
[*]videos of youtube "saccade" (are very slow, stop and go...)
[/LIST]

And yours ?

---

### Post by esanya on 2008-12-31
Hi!

That sounds good if the preinstalled ubuntu works, than it should be possible to run ubuntu on these laptops too. 

Could You send the output of "uname -a" and "cat /etc/*-version"?!

1) if I plug an external mic to the 2. jack than it works... the front mic for me is also problematic
2) in alsamixer you can mute the speaker
3) no problem on elive (I'm currently using elive development version), the nvidia driver is loaded when X starts. You should check the content of /var/log/Xorg.0.log file, if it shows the nvidia driver.... or grep -i nvidia /var/log/Xorg.0.log:

...
(II) NVIDIA(0): Virtual screen size determined to be 1366 x 768
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "1366x768"
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled

Regards,
Sandor

> **Bristow_69 said:**
> Hello ;)

I'm french...

I bought this laptop with ubuntu pre-installed.

I think it runs only in 64 bits. I've intrepid on it. I've only 3 littles bugs :
[LIST=1]
[*]front mic doesn't work (near webcam)
[*]when i plug headset, sound isn't mute on speakers
[*]videos of youtube "saccade" (are very slow, stop and go...)
[/LIST]

And yours ?

---

### Post by Bristow_69 on 2009-01-01
Thanks esanya for you post.

My second problem is OK :)

For flash videos :

$  grep -i nvidia /var/log/Xorg.0.log

(--) PCI: (0@0:1:3) nVidia Corporation MCP78S [GeForce 8200] Co-Processor rev 162, Mem @ 0xfbf80000/0
(--) PCI:*(0@2:0:0) nVidia Corporation GeForce 9100M G rev 162, Mem @ 0xfc000000/0, 0xd8000000/0, 0xd6000000/0, I/O @ 0x0000cc00/0, BIOS @ 0x????????/131072
(II) Module glx: vendor="NVIDIA Corporation"
(II) NVIDIA GLX Module  177.80  Wed Oct  1 15:06:06 PDT 2008
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
(II) NVIDIA dlloader X Driver  177.80  Wed Oct  1 14:45:01 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) NVIDIA(0): Creating default Display subsection in Screen section
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 9100M G (C77) at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.77.2c.00.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 9100M G at PCI:2:0:0:
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1366 x 768
(--) NVIDIA(0): DPI set to (99, 97); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(II) NVIDIA(0): Initialized GPU GART.
(WW) NVIDIA(0): Error: Unable to find DOS (Enable/Disable output switching)
(WW) NVIDIA(0): file path under /proc/acpi/video NVIDIA X driver will not
(WW) NVIDIA(0):     be able to respond to  display change hotkey events.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled


If you see something, do not hesitate :P

Bristow

---

### Post by zombie_monkey on 2009-01-18
> **esanya said:**
> 

That sounds good if the preinstalled ubuntu works, than it should be possible to run ubuntu on these laptops too. 

Could You send the output of "uname -a" and "cat /etc/*-version"?!

1) if I plug an external mic to the 2. jack than it works... the front mic for me is also problematic
2) in alsamixer you can mute the speaker
3) no problem on elive (I'm currently using elive development version), the nvidia driver is loaded when X starts. You should check the content of /var/log/Xorg.0.log file, if it shows the nvidia driver.... or grep -i nvidia /var/log/Xorg.0.log:

Indeed, that good news because it means it's possible. Now, if you have these problems, that imples you did manage to install it then? If you did, do you mind sharing with us how you did it?

---

### Post by srd on 2009-01-24
Ubuntu 64bit

bios enable ahci
AHCI DID for Linux enable
 
boot from cd
press F6
delete quiet

then add: nosplash init=/bin/bash

You need ethernet connection 

then type

```
dhclient eth0
```
```
apt-get update
```
```
apt-get install nvidia-glx-177
```
```
depmod -a
```
```
nvidia-xconfig
```
```
/etc/init.d/dbus stop
```
```
/etc/init.d/dbus start
```
```
/etc/init.d/hal stop
```
```
/etc/init.d/hal start
```
```
gdm start
```

Maybe your touchpad will not working, You must install system with keyboard.
 
Reboot
Then press (ESC) in the grub menu
press e
then edit ro to rw
remove quiet
add nosplash init=/bin/bash

```
dhclient eth0
```
```
apt-get update
```
```
apt-get install nvidia-glx-177
```
```
depmod -a
```
```
nvidia-xconfig
```
```
reboot
```




For wireless look here:
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

Sorry for my english.

---

### Post by zombie_monkey on 2009-01-26
Thanks a lot, srd, that was just in time for me! :)

Also, I had tried with the alternate isntall cd, and of course it worked as it doesn't need a graphics driver, but after the reboot it didn't work, and I thought the problem is with scsi, sata and such. If someone installs it through the alternate install CD, they just need to add the nvidia drivers after the first reboot, after it's already installed, like you did in the second part.

After I updated, it would start loading with the graphical bar but stop in the beginning, I did the second part again, but I suppose running nvidia-xconfig again would have been enough.

---

### Post by esanya on 2009-01-27
Hi!

Thanks for the help! I have started with the latest 9.04 (alpha3). Somehow I was able to install 9.04_alpha3_amd64.

I didn't do the:
```

apt-get update
apt-get install nvidia-glx-177
depmod -a
nvidia-xconfig
```

But than I do
```
/etc/init.d/dbus stop
/etc/init.d/dbus start
/etc/init.d/hal stop
/etc/init.d/hal start
gdm start
```

Than I have loggen in with a failsafe gnome session. And I was able to install...

But now I can't start the system with: init=/bin/bash

I have pressed e for the first entry in grub, than e for the line with the kernel, deleted quiet, splash, and changed ro to rw. 

But I don't know where to add init=/bin/bash, it doesn't work for me... If I put it to a wrong place, my laptop restarts, if I put it to an other place it starts the init program, not the bash...

Any Idea?

Thanks,
Sandor


> **srd said:**
> Ubuntu 64bit

bios enable ahci
AHCI DID for Linux enable
 
boot from cd
press F6
delete quiet

then add: nosplash init=/bin/bash

You need ethernet connection 

then type

```
dhclient eth0
```
```
apt-get update
```
```
apt-get install nvidia-glx-177
```
```
depmod -a
```
```
nvidia-xconfig
```
```
/etc/init.d/dbus stop
```
```
/etc/init.d/dbus start
```
```
/etc/init.d/hal stop
```
```
/etc/init.d/hal start
```
```
gdm start
```

Maybe your touchpad will not working, You must install system with keyboard.
 
Reboot
Then press (ESC) in the grub menu
press e
then edit ro to rw
remove quiet
add nosplash init=/bin/bash

```
dhclient eth0
```
```
apt-get update
```
```
apt-get install nvidia-glx-177
```
```
depmod -a
```
```
nvidia-xconfig
```
```
reboot
```




For wireless look here:
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

Sorry for my english.

---

### Post by srd on 2009-01-28
Second entry  in the grub
look like this 
rw nosplash init=/bin/bash

---

### Post by esanya on 2009-01-28
Thanks!

I was able to start ubuntu 9.04 (a3)_amd64... :) With an other trick.

The boot always was blocked after the loading of ath_hal, and ath_pci, so I have mounted the ubuntu partition from elive, and deleted all of these modules from the ubuntu /lib dir... 

Now I don't have wireless, but the OS at least starts...

Now I have the nvidia problem, which is reported/discussed at ubuntu bugs...

Which CD, version did You used?

ubuntu 8.04, and alternate install? 

Does nvidia works for You?

Thanks!

---

### Post by srd on 2009-01-29
I used Ubuntu 8.10 64bit Live CD.
Nvidia drivers nvidia-glx-177 works with Ubuntu 8.10 64bit Live CD.
Nvidia drivers (nvidia-glx-177 and nvidia-glx-180) does not work with my Kubuntu 9.04 alternate 64bit alpha 3, but after installation I update kernel and Kubuntu started in desktop with no problems, resolution is 1280x720, without nvidia drivers. Only problem is xorg with cpu usage.

---

### Post by e-Claude on 2009-05-07
Hi everybody !

I'm new to Ubuntu and wanted to share my personal experience about the problem of installing it to a MSI VR630 laptop.

I've got the machine since a few months and bought it to install Linux on it, to do some office work for the scouts of my village (Bousval in Belgium). I chose Ubuntu because it seemed the best choice possible when you come from m$ Windoze.

My disapointment was big when neither Ubuntu "Interpid Ibex" nor windoze XP (tried 32 and 64 bits versions of both) were able to boot the machine. I finally tried some M$ V***a and it went through the installation procedure without any problem. Grrrrrrr ! I hated that ...

I decided to try everything humanly possible to install something else than V***a and tried Ubuntu, Mint, Fedora, OpenSuse, Windoze XP home and Pro, an old Me ... Nothing booted but FreeDOS ... no big deal. I finally left the V***a crap on it (75 Gb out of 250 on the harddisk)

I burnt some BIOS release 1.0H from MSI because I read about that somewhere, tried all settings for AHCI, ... nuts ! Tried all the versions again, ... no success ...

Today, I downloaded Ubuntu 9.04 "Jaunty Jackalope" and installed the FRench version with BElgian keyboard layout (I'm from Belgium) and everything went OK !

I had some cold sweat when the machine slowed down suddenly during install, but the process went without problem to the end.

I was asked for some ientifier and password and ... I saw the magnificent desktop from JJ ! I really like it !

I tried some videos, pictures viewing, I got the sound ... updates happend without problem from the internet (everything functional "out of the box"). Although the pictures are stored on the NTFS part of the drive the viewing occurs smoothly and at my satisfaction !

I didn't try WiFi, webcam, hearphones, mike, and so on yet.

I wanted to thank all the people concerned by Ubuntu dev. NICE PIECE OF WORK and greetings from the heart to all the people that contributed to solve the HDD controller problem (as far as I understand what was going wrong in the previous versions)

CHEERS from Belgium.

Claude

---

### Post by adeii on 2010-03-15
Ubuntu 9.10 Netbook Remix works fine with MSi VR630, even WiFi is installed. All you/we need is new nVidia GFX driver and WebCam driver.

---

