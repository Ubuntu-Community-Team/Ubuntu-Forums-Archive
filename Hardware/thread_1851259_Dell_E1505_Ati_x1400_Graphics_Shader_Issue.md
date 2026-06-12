---
title: "Dell E1505 Ati x1400 Graphics Shader Issue"
date: 2011-09-27
forum: Hardware
---

### Post by Crzykiddo on 2011-09-27
I will start the thread with my relevant computer specs and Linux build: 


Ubuntu 11.04
Kernel Linux 2.6.38-11-generic
GNOME 2.32.1

Hardware:

2 GiB of RAM
Dual Core T2250 Processors @ 1.73GHz each
Radeon Mobility X1400 Graphics Card

------------------------

I've searched the forums for this specific issue and haven't been able to find any solutions. I am having an issue with the shader support for my graphics card. It shows it can use Shader 3.0 but any programs relying on those shaders will give me an exception saying that my graphics card is outdated. Now I have Windows 7 on the same harddrive and it can run games that require such shaders just fine, so I'm thinking this is a driver issue.

I have tried Fglrx drivers but at the ATI/AMD website it states that their drivers will only work on linux distributions older than 9.10 and thus won't work with my graphics card. I even tried installing the drivers before I knew this fact, but it wouldn't initialize and not even 3d acceleration worked. I have run a few commands in the terminal and I will post what I think are relevant items below. Do bare with me as I am very new to linux and the commands are pretty foreign to me. 

Some items I think are relevant below:


Running lshw -C display shows

WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-display               
       description: VGA compatible controller
       product: Radeon Mobility X1400
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:43 memory:d0000000-dfffffff ioport:ee00(size=256) memory:efdf0000-efdfffff memory:efd00000-efd1ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

The stuff above tells me it is using the basic opensource drivers. Do note that I get 3d acceleration just fine. Glxgears runs without issues. 

Running the "dmesg | grep drm" command I get

[   12.816911] [drm] Initialized drm 1.1.0 20060810
[   13.871798] [drm] radeon defaulting to kernel modesetting.
[   13.871802] [drm] radeon kernel modesetting enabled.
[   13.879704] [drm] initializing kernel modesetting (RV515 0x1002:0x7145).
[   13.879735] [drm] register mmio base: 0xEFDF0000
[   13.879738] [drm] register mmio size: 65536
[   13.879925] [drm] Generation 2 PCI interface, using max accessible memory
[   13.879963] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.879966] [drm] Driver supports precise vblank timestamp query.
[   13.880502] [drm] radeon: irq initialized.
[   13.881187] [drm] Detected VRAM RAM=256M, BAR=256M
[   13.881191] [drm] RAM width 64bits DDR
[   13.881628] [drm] radeon: 128M of VRAM memory ready
[   13.881637] [drm] radeon: 512M of GTT memory ready.
[   13.881670] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   13.883534] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   13.885218] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[   13.886958] [drm] Loading R500 Microcode
[   13.891548] [drm] radeon: ring at 0x0000000010001000
[   13.891587] [drm] ring test succeeded in 9 usecs
[   13.891797] [drm] radeon: ib pool ready.
[   13.893360] [drm] ib test succeeded in 0 usecs
[   13.897914] [drm] Radeon Display Connectors
[   13.897918] [drm] Connector 0:
[   13.897920] [drm]   VGA
[   13.897924] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   13.897927] [drm]   Encoders:
[   13.897929] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   13.897932] [drm] Connector 1:
[   13.897934] [drm]   LVDS
[   13.897937] [drm]   DDC: 0x7e30 0x7e30 0x7e34 0x7e34 0x7e38 0x7e38 0x7e3c 0x7e3c
[   13.897939] [drm]   Encoders:
[   13.897941] [drm]     LCD1: INTERNAL_LVTM1
[   13.897943] [drm] Connector 2:
[   13.897945] [drm]   S-video
[   13.897947] [drm]   Encoders:
[   13.897949] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[   13.993936] [drm] radeon: power management initialized
[   14.438719] [drm] fb mappable at 0xD00C0000
[   14.438723] [drm] vram apper at 0xD0000000
[   14.438725] [drm] size 4096000
[   14.438727] [drm] fb depth is 24
[   14.438729] [drm]    pitch is 5120
[   14.438851] fbcon: radeondrmfb (fb0) is primary device
[   14.439060] fb0: radeondrmfb frame buffer device
[   14.439062] drm: registered panic notifier
[   14.439072] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:00.0 on minor 0
[  490.045187] [drm:subconnector_show] *ERROR* Unable to find subconnector property
[  490.045341] [drm:select_subconnector_show] *ERROR* Unable to find select subconnector property
[  822.433319] [drm:subconnector_show] *ERROR* Unable to find subconnector property
[  822.433472] [drm:select_subconnector_show] *ERROR* Unable to find select subconnector property
[  826.165282] [drm:subconnector_show] *ERROR* Unable to find subconnector property
[  826.165434] [drm:select_subconnector_show] *ERROR* Unable to find select subconnector property
[ 1591.986214] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[ 1592.034280] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[ 1592.034347] [drm] radeon: ring at 0x0000000010001000
[ 1592.034384] [drm] ring test succeeded in 9 usecs
[ 1592.034401] [drm] ib test succeeded in 0 usecs
[ 1596.203161] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[ 4908.302078] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[ 4908.308346] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[ 4908.308443] [drm] radeon: ring at 0x0000000010001000
[ 4908.308479] [drm] ring test succeeded in 9 usecs
[ 4908.308495] [drm] ib test succeeded in 0 usecs
[ 4912.465475] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id


I don't know if any of these errors above will provide you with any relevant information, but please feel free to post some commands that would help you guys get more information on my problem.

Thanks in advance,
Crzykiddo

---

### Post by diasf on 2011-09-28
The proprietary drivers do not support that board anymore.
The open drivers do not support all the features of this board yet.

Sad, i know, I have the exact same pc :(

---

### Post by Crzykiddo on 2011-09-29
So am I forced to downgrade to an earlier Ubuntu build? Or is there something else I can do?


EDIT: I was roaming around trying to fix this on my own and found that glxgears should report in the 1000+ range. I only get this:


301 frames in 5.0 seconds = 60.074 FPS
298 frames in 5.0 seconds = 59.590 FPS
299 frames in 5.0 seconds = 59.597 FPS
299 frames in 5.0 seconds = 59.609 FPS
299 frames in 5.0 seconds = 59.624 FPS
299 frames in 5.0 seconds = 59.612 FPS


I don't know if that is an issue but I checked to see if my graphics card does direct rendering and it does. In the troubleshooting area it stated TODO options and having low frames in glxgears with direct rendering was on the todo list. I'm wondering if there is a solution to this problem.

---

### Post by Veikk0 on 2011-09-29
Since your card definitely supports Shader Model 3.0 I'm betting the open source drivers in Ubuntu 11.04 don't have some features required for SM3 support. This could be because the drivers are simply too old: to ensure stability, Ubuntu releases receive only security updates, no new features. Ubuntu 11.04 was released about 6 months ago and it's development was started six months before that, so your current graphics drivers are probably from ~12 months old.

It's also possible that the drivers had the features required for SM3 at the time when Ubuntu 11.04 development was started, but Ubuntu devs have had to disable some of those features because of patent concerns (I've read of a texture compression algorithm called S3TC that's patented, and because Canonical probably doesn't want to be sued into oblivion by the owner of the patent, Ubuntu most likely has disabled S3TC).

Anyway, if your issue is caused by graphics drivers the solution is to install newer ones. I recommend using this Personal Package Archive (PPA): [https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/). The PPA is maintained by a member of the Phoronix forums (see the thread for the PPA here [http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers](http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers)).

I recommend you install the package "ppa-purge" in case the updated drivers mess up your graphics somehow and you need to remove the PPA without graphical inveronment, using command line only. This has never happended to me though, and I've been using this PPA for many months now. My card is also from the X1000 series, though mine is a desktop card (the Radeon X1950 Pro).

Now for the instructions. I recommend you follow the instructions at the Phoronix forum thread. I'm only going to add here the commands I always use in new Ubuntu installations to install the drivers.

First install ppa-purge:
```
sudo apt-get install ppa-purge
```

Then add the PPA to software sources, reload the package list and update the packages:
```
sudo add-apt-repository ppa:oibaf/graphics-drivers && sudo apt-get update && sudo apt-get upgrade
```

(The guide at the Phoronix forums uses "apt-get dist-upgrade" instead of "apt-get upgrade" but I've had no trouble with "upgrade" only. Dunno if it makes any difference.)

EDIT:Oh yeah, forgot to mention how to revert back to original drivers.

If you find your graphics don't work correctly after upgrading, do this:
```
sudo ppa-purge ppa:oibaf/graphics-drivers
```

I hope this helps :)

About glxgears framerate: I don't know why, but in recent Ubuntu releases glxgears syncs its framerate with the monitor refresh rate. To see your maximum framerate you can try "vblank_mode=0 glxgears" or try running "vblank_mode=0" first and then glxgears after that.

---

### Post by Crzykiddo on 2011-09-30
Thank you, I finally got one step farther. The program in question I am trying to run is Eveonline. I finally managed to get it working with your method (although I had to do the distro-upgrade flag thing for it to work). Only issue I have now is it thinks my graphics card is an x700 SE 1 for some reason, not to mention that any graphic in the game is just pure black. I'm guessing the textures aren't loading. Anyway, thanks for getting me this far, I'm just not sure how to get those textures to load :P. This is what I get using the 
"glxinfo | grep OpenGL" command:


OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RV515
OpenGL version string: 2.1 Mesa 7.12-devel
OpenGL shading language version string: 1.20
OpenGL extensions:


I notice I am now using the 2.1 Mesa 7.12-devel which is the only figure
that changed as far as I know. Again, thank you so much. I have spent
hours searching for a solution on how to start the damn thing. At least
now it starts :).

Note: I tried installing the experimental drivers on the phoronix page but it hasn't seemed to load or it didn't do anything. Either way, I'll be trying some more possible solutions.

EDIT: After uninstalling the graphics drivers and reinstalling the same package I now get textures on objects. Another game (Civilization 4) has some 3d aspects disappeared. Like the leaders not appearing XD. I guess I'll have to wait and see with the new ubuntu build coming up in a couple weeks to see if support for my graphics card is further enhanced. I'm also noticing a major performance reduction compared to windows, but either way I'm glad I at least have it working :).

---

