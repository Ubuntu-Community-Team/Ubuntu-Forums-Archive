---
title: "AMD Catalyst Legacy 13.1, Ubuntu 14.04 LTS?"
date: 2014-05-05
forum: Hardware
---

### Post by habanero2 on 2014-05-05
[COLOR=#000000][FONT=Helvetica Neue]Hi, I'm new to Ubuntu. i recently got my hands on a used laptop, wiped the Hard Drive clean and installed Ubuntu 14.04 LTS [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]Laptop: TOSHIBA Satellite L505D-ES5025 NoteBook [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]Processor: AMD Turion II Dual-Core M520 (2.3GHz) [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]RAM: 4GB DDR2 [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]HDD: 320GB [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]Graphics: ATI Radeon HD 4200 [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]the first thing i usually do with a new pc is make sure all the drivers are up to date for a smoothly operating machine. however, when i tried to download and install the Catalyst 13.1 Legacy driver via " sudo sh ./amd-driver-installer-catalyst-13.1-leg... ", it ran into this error: [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]Created directory fglrx-install.McglSS [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]Verifying archive integrity... All good. [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]Uncompressing AMD Catalyst(TM) Proprietary Driver-8.97.100.7.......................... [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue].......................................... [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]=======================================... [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]AMD Catalyst(TM) Proprietary Driver Installer/Packager [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]=======================================... [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]Generating package: Ubuntu/quantal [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]Removing temporary directory: fglrx-install.McglSS [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]could someone help me out please?[/FONT][/COLOR]

---

### Post by QIII on 2014-05-05
Hello!

Unfortunately, you are in a bad position.  AMD/ATI stopped supporting Linux drivers for anything prior to HD 5000 series GPUs.

The driver that would work with your HD 4000 series will not be updated to work with the more recent versions of X Server.

Although there are hacks that people suggest, *I would strongly recommend against them* and feel that I would be terribly irresponsible even to direct you to one.

Your options are three, with my recommendation at the top:

1.  Continue to use the open source default Radeon driver installed with Ubuntu.  This driver has gotten extremely good over the years and will continue to improve with AMD taking part in its development.

2.  Reinstall 12.04.1 or *earlier*.  12.04.2 does not work with the AMD/ATI driver.  Bear in mind that 12.04.1 is also supported until 2017.

3.  Buy an AMD product with a designation of HD 5000 or higher.  This choice costs money, so it is not mine to say you should or should not do this.

I wish I had better news for you.

Cheers!

---

### Post by habanero2 on 2014-05-05
so, you're saying i cant get the maximum performance out of this thing?
i got this laptop for free because i don't have the money to invest in a newer computer.
and i was planning on using this laptop to familiarize myself with Linux operating systems (been raised on Windows all my life), but this thing lags and has a lot of graphics issues, especially because the screen is broken (i have it docked an hooked up to a monitor)

---

### Post by QIII on 2014-05-05
What I am saying is the AMD/ATI no longer supports that card with the X Server used from Ubuntu 12.04.2 and beyond.

If the open source driver is not working well, you can consider installing Ubuntu 12.04.1 (scroll down through the list [here]("http://old-releases.ubuntu.com/releases/12.04.0/") and find the section specifying 12.04.1 images) and using the ATI fglrx driver in the Precise repo.  That will be a two year old driver, but it may perform better for you than the open source driver is now.

---

### Post by habanero2 on 2014-05-05
oh well. thanks anyways.

---

### Post by mastablasta on 2014-05-06
however that card should work well with opensource drivers. can you post result from these commands (you can copy and paste them into terminal) wrapped in code tags (# icon):

```
dmesg | egrep 'drm|radeon'


```
```
sudo apt-get install mesa-utils
LIBGL_DEBUG=verbose glxinfo
```

they only time you should notice a performance worse than with proprietary should be in games. and even then with latest drivers it's about 10-20% worse if i remember correctly. while you talk about unusable user interface.
 i have some old, some new hardware and on all (but one i am still troubelshooting) opensource drivers perform OK for system tasks.

also if it's a laptop make sure you gave it enough RAM resources and that you still have enough left for running the OS.

alternatively you can use alighter desktop that doens't use 3D acceleration just to draw windows. Xubuntu uses a light and very easy to use desktop with Ubuntu system as it's base.

---

### Post by pme 72 on 2014-05-06
If you do decide to stay with 14.04 and give the community developed open source driver a try you should look into enabling dpm, dynamic power management. dpm should allow your HD4200 to clock down to a lower performance level for regular desktop applications not requiring a high performance mode. The laptop should run cooler and use less power. The power management functionality is reported to be similar to that of the AMD/ATI proprietary driver.

---

### Post by habanero2 on 2014-05-09
here you go

```
 [    3.295555] [drm] Initialized drm 1.1.0 20060810[    3.330321] [drm] radeon kernel modesetting enabled.
[    3.330410] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
[    3.330818] [drm] initializing kernel modesetting (RS880 0x1002:0x9712 0x1179:0xFF1F).
[    3.330835] [drm] register mmio base: 0xF2300000
[    3.330837] [drm] register mmio size: 65536
[    3.331716] radeon 0000:01:05.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
[    3.331719] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    3.331724] [drm] Detected VRAM RAM=256M, BAR=256M
[    3.331725] [drm] RAM width 32bits DDR
[    3.331812] [drm] radeon: 256M of VRAM memory ready
[    3.331813] [drm] radeon: 512M of GTT memory ready.
[    3.331828] [drm] Loading RS780 Microcode
[    3.331904] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    3.338452] [drm] PCIE GART of 512M enabled (table at 0x00000000C0040000).
[    3.338558] radeon 0000:01:05.0: WB enabled
[    3.338562] radeon 0000:01:05.0: fence driver on ring 0 use gpu addr 0x00000000a0000c00 and cpu addr 0xffff8800dda88c00
[    3.338565] radeon 0000:01:05.0: fence driver on ring 3 use gpu addr 0x00000000a0000c0c and cpu addr 0xffff8800dda88c0c
[    3.338567] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.338569] [drm] Driver supports precise vblank timestamp query.
[    3.338585] [drm] radeon: irq initialized.
[    3.371114] [drm] ring test on 0 succeeded in 1 usecs
[    3.371172] [drm] ring test on 3 succeeded in 1 usecs
[    3.371280] [drm] Enabling audio 0 support
[    3.371298] [drm] ib test on ring 0 succeeded in 0 usecs
[    3.371313] [drm] ib test on ring 3 succeeded in 0 usecs
[    3.371573] [drm] Radeon Display Connectors
[    3.371575] [drm] Connector 0:
[    3.371576] [drm]   VGA-1
[    3.371578] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    3.371579] [drm]   Encoders:
[    3.371580] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    3.371582] [drm] Connector 1:
[    3.371583] [drm]   LVDS-1
[    3.371585] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    3.371586] [drm]   Encoders:
[    3.371587] [drm]     LCD1: INTERNAL_KLDSCP_LVTMA
[    3.371609] [drm] radeon: power management initialized
[    7.450504] [drm] fb mappable at 0xE0141000
[    7.450508] [drm] vram apper at 0xE0000000
[    7.450509] [drm] size 5767168
[    7.450510] [drm] fb depth is 24
[    7.450512] [drm]    pitch is 5632
[    7.450627] fbcon: radeondrmfb (fb0) is primary device
[   11.486205] radeon 0000:01:05.0: fb0: radeondrmfb frame buffer device
[   11.486208] radeon 0000:01:05.0: registered panic notifier
[   11.486323] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:05.0 on minor 0 
```

```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following NEW packages will be installed:
  mesa-utils
0 upgraded, 1 newly installed, 0 to remove and 21 not upgraded.
Need to get 34.4 kB of archives.
After this operation, 133 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe mesa-utils amd64 8.1.0-2 [34.4 kB]
Fetched 34.4 kB in 0s (67.8 kB/s)
Selecting previously unselected package mesa-utils.
(Reading database ... 206714 files and directories currently installed.)
Preparing to unpack .../mesa-utils_8.1.0-2_amd64.deb ...
Unpacking mesa-utils (8.1.0-2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up mesa-utils (8.1.0-2) ... 
```

how do i enable dpm? I'm a total noob when it comes to working with Ubuntu/Linux

also, i originally intended to run Folding@home on this machine an maybe some minor gaming like WoW, Halo: CE, Team Fortress 2, etc. I'm not expecting a miracle, but i'd like to salvage this laptop as something that's at least useful.

and basic tasks are not a problem as long as the programs i use are fully supported on Linux (i use Google Chrome and the Linux alpha release is rather wonky sometimes)

---

### Post by mastablasta on 2014-05-10
this one is seperate command from install in first line. so copy it and hit and enter:
```
LIBGL_DEBUG=verbose glxinfo
```

and post the output.


it should say level of opengl and if it's hw accelerated.

search for this part :
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string: 2.1 Mesa 8.0.4

or simialr. it should be there as apparently it means that CPU is doing the acceleration. if this is so then you are in same position as i am at one of the mashcines. i will try to find a bug for this behaviour or how to go arorund it. i am preety much beginner as well.

---

### Post by habanero2 on 2014-05-10
all i got was this, didnt say anything about OpenGL or hardware acceleration:

```
0x234 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x235 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x236 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x237 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x238 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x239 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x23a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x23b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x23c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x23d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x23e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x23f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x240 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x241 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x242 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x243 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x244 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x245 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x246 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x247 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x248 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x249 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x24a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x24b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x24c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x24d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x24e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x24f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x250 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x251 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x252 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x253 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x254 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x255 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x256 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x257 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x258 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x259 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x25a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x25b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x25c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x25d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x25e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x25f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x260 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x261 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x262 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x263 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x264 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x265 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x266 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x267 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x268 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x269 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x26a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x26b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x26c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x26d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x26e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x26f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x270 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x271 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x272 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x273 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x274 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x275 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x276 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x277 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x278 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x279 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x27a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x27b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x27c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x27d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x27e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x27f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x280 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x281 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x282 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x283 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x284 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x285 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x286 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x287 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x288 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x289 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x28a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x28b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x28c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x28d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x28e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x28f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x290 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x291 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x292 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x293 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x294 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x295 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x296 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x297 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x298 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x299 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x29a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x29b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x29c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x29d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x29e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x29f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x2a0 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x2a1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x2a2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x2a3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x2a4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x2a5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x2a6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x2a7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x2a8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x2a9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x2aa 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x2ab 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x2ac 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x2ad 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x2ae 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x2af 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x2b0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x2b1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x2b2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x2b3 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x2b4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x2b5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x2b6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x2b7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x2b8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x2b9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x2ba 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x2bb 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x2bc 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x2bd 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x2be 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x2bf 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x2c0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x2c1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x2c2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x2c3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x06e 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None


360 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x06f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x070 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x071 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x072 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x073 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x074 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x075 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x076 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x078 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x079 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x07a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x07b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x07c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x07d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x07e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x07f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x080 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x081 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x083 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x084 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x085 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x086 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x087 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x088 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x089 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x08a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x08b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x08c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x08d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x08e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x08f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x090 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x091 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x092 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x093 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x094 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x095 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x096 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x097 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x098 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x099 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x09a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x09b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x09c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x09d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x09e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x09f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x0a0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x0a1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x0a2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x0a3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0a4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x0a5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x0a6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0a7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x0a8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x0a9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x0aa 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x0ab 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ac 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ad 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ae 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0af 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0b0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0b1 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0b2 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0b3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0b4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0b5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0b6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0b7 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0b8 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0b9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ba 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0bb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0bc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0bd 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0be 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0bf 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0c0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0c1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0c2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0c3 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x0c4 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0c5 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x0c6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x0c7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0c8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x0c9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x0ca 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x0cb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x0cc 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x0cd 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x0ce 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x0cf 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x0d0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x0d1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x0d2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x0d3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x0d4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x0d5 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x0d6 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x0d7 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x0d8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x0d9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x0da 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x0db 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x0dc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x0dd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x0de 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x0df 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0e0 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x0e1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x0e2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0e3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x0e4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x0e5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x0e6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x0e7  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0e8  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0e9  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ea  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0eb  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ec  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ed  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0ee  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0ef  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0f0  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0f1  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0f2  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0f3  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f4  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f5  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f6  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f7  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f8  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f9  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0fa  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0fb  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0fc  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0fd  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0fe  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ff  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x100  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x101  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x102  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x103  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x104  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x105  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x106  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x107  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x108  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x109  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x10a  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x10b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x10c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x10d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x10e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x10f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x110  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x111  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x112  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x113  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x114  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x115  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x116  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x117  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x118  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x119  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x11a  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x11b  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x11c  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x11d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x11e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x11f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x120  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x121  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x122  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x123 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x124 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x125 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x126 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x127 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x128 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x129 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x12a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x12b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x12c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x12d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x12e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x12f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x130 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x131 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x132 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x133 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x134 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x135 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x136 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x137 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x138 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x139 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x13a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x13b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x13c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x13d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x13e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x13f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x140 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x141 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  2 1 None
0x142 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  4 1 None
0x143 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  8 1 None
0x144 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x145 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x146 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x147 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x148 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x149 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x14a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  2 1 None
0x14b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  4 1 None
0x14c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  8 1 None
0x14d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x14e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x14f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x150 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x151 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x152 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x153 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x154 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x155 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x156 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x157 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x158 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x159 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x15a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x15b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x15c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x15d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x15e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x15f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x160 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x161 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x162 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x163 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x164 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x165 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x166 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x167 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x168 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x169 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x16a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x16b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x16c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x16d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x16e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x16f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x170 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x171 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x172 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x173 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x174 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x175 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x176 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x177 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x178 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x179 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x17a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x17b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x17c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x17d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  2 1 None
0x17e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  4 1 None
0x17f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  8 1 None
0x180 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x181 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x182 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x183 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x184 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x185 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x186 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  2 1 None
0x187 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  4 1 None
0x188 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  8 1 None
0x189 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x18a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x18b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x18c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x18d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x18e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x18f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  2 1 None
0x190 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  4 1 None
0x191 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  8 1 None
0x192 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x193 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x194 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x195 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x196 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x197 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x198 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  2 1 None
0x199 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  4 1 None
0x19a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  8 1 None
0x19b  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x19c  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x19d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x19e  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x19f  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x1a0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x1a1  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x1a2  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x1a3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x1a4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x1a5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x1a6  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x1a7  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x1a8  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x1a9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x1aa  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x1ab  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x1ac  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x1ad  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x1ae  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x1af  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x1b0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x1b1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x1b2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x1b3  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x1b4  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x1b5  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x1b6  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x1b7  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x1b8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x1b9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  2 1 None
0x1ba  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  4 1 None
0x1bb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  8 1 None
0x1bc  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1bd  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1be  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x1bf  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1c0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1c1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x1c2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  2 1 None
0x1c3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  4 1 None
0x1c4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  8 1 None
0x1c5  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1c6  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1c7  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1c8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1c9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1ca  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1cb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  2 1 None
0x1cc  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  4 1 None
0x1cd  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  8 1 None
0x1ce  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1cf  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1d0  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x1d1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1d2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1d3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None
0x1d4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  2 1 None
0x1d5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  4 1 None
0x1d6  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  8 1 None



```

---

### Post by mastablasta on 2014-05-10
that's a very strange output are you sure you are on opensource drivers?

actually this looks like the last part of the command. hmm, but why the first one is not showing where it says the modes that are initialised?

by the way how to enable dpm is found here at the bottom: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by pme 72 on 2014-05-10
To access full output of LIBGL_DEBUG=verbose glxinfo in Text Editor Habanero2 probably needs to be able to scroll back further. In Text Editor go to Edit>Preferences>Scrolling and change the default setting of Scroll Back from 512 lines to something larger like 1000 lines. Re-run the command.

---

### Post by Marjan_Tanevski on 2014-08-21
@QIII - Hello there, I went with #1. My specifications are: 

Laptop - MSI CR630
CPU - AMD Athlon II Dual-Core Mobile Processors,
Memory -  DDR3 1066, 4GB
Chipset - RS880M+SB820M,
Graphics - ATI Mobility Radeon HD 4270.

I am ubuntu user and I have been investigating and trying to find a way (patched driver tried) to have the old ati drivers work on my xubuntu 14.04.1, but it always ended up with low resolution - maybe I did something wrong, but even if I did get it to work I didn't want my graphics to work with "hacked/patched" drivers, so I also strongly recommend against them. For some time I have been using xubuntu 12.04.01, but now I am using xubuntu 14.04.1 (while using the open source default Radeon drivers). I am hoping that somehow AMD will include support for these "old" graphics (I still do not consider that my graphics are that old) in the future...

---

