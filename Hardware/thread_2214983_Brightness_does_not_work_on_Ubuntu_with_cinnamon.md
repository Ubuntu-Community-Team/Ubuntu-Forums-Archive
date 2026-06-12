---
title: "Brightness does not work on Ubuntu with cinnamon"
date: 2014-04-04
forum: Hardware
---

### Post by Vinay Balraj on 2014-04-04
Hi, guys.. I've completely moved away from windows, but have dual booted with windows 8.1 as some apps like CAD wont run on linux and need to turn back to windows.
However, I'm facing few glitches with Ubuntu..

Well, coming to my issue, I own a Dell 15R 5521 laptop with Intel i7, 8GB RAM, 1TB HDD, which has an onboard Intel HD 4000 graphics. And I've also using cinnamon here as the interface is much neater.

Everything's working fine, except for 2 issues-

1> the brightness control.
2> Unable to mount windows partitions
--------------------------------------------------------------------------------------------------------------------------------
for brightness control, I've tried-


1> Installing the open source drivers from Intel itself
2> "http://forums.linuxmint.com/viewtopic.php?f=49&t=155564"
3> "http://forums.linuxmint.com/viewtopic.php?f=49&t=155527"
4> "http://ubuntuforums.org/showthread.php?t=1979932"
5> "http://askubuntu.com/questions/49778/display-brightness-adjustment-not-working"
6> tried editing the boot options from grub to add vendor to check if it works, but it did not... Instead it just goes to the boot logo and gets stuck there. Then restoring the backup and updating grub will fix it back to default. But still doesnt work.


However the hotkeys seems to work fine and the brightness icon comes up, but nothing happens..


I saw a few posts that many people have the same issue where most were fixed after installed either properitery drivers, or updating BIOS or editing the xorg server files..
I've mostly tried everything posted above.. If there is something else that i've missed out, please let me know.. I'd like this to fix this as the screen is very bright in the dark and I'm unable to use the laptop because of this..
------------------------------------------------------------------------------------------------------------------------------------------------------

And for mounting partitions, this is what comes up when i try to mount

"Unable to mount partition

Error mounting /dev/sda3 at /media/vinay/New Volume: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda3" "/media/vinay/New Volume"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda3': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option."

I have tried booting to windows to make sure it was shut down and not locked. But still no vain.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
I've had issues with touchpad not registering taps, that was fixed after editing the synaptics xorg file and adding a few lines, and the fan always used to run at max rpm regardless of the cpu load, that was finally fixed after a BIOS update, previous to which, had tried setting max and min fan speeds in both BIOS and Ubuntu, which did not help..


Mentioning that just to let you know if I've done something wrong.. Thanks for the help in advance..

---

### Post by Toz on 2014-04-04
With respect to the brightness, lets have a closer look at some of your system settings. Open a terminal window, type in the following commands, and post back the results within **[noparse]```
 
```[/noparse]** tags:

1. Your current kernel boot line:
```
cat /proc/cmdline
```
2. Information about your video card(s):
```
lspci -k | grep -iA2 VGA
```
3. Information about your known backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
4. A listing of your loaded kernel modules:
```
lsmod
```
5. Your /var/log/Xorg.0.log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

Note: It would probably be best to create a separate thread for the Windows mounting issue, otherwise it will get confusing in here.

---

### Post by Vinay Balraj on 2014-04-08
Hi, @TOZ, sorry for the late reply.. here are the things you wanted.. The log file is quite huge, I hope you dont mind... :D

1> kernel boot line:
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=bfcf7d92-a0ac-4eaf-a131-db0b4fec8458 ro quiet splash vt.handoff=7
```

2> information on Video card:
```
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: Dell Device 0597
    Kernel driver in use: i915
```

3> known backlight interfaces"
```
/sys/class/backlight/acpi_video0
99
99
99


 /sys/class/backlight/intel_backlight
574
4882
574
```



4> kernel modules loaded:
```
Module                  Size  Used by
vmnet                  55933  13 
vmw_vsock_vmci_transport    26328  0 
vsock                  34895  1 vmw_vsock_vmci_transport
vmw_vmci               62962  1 vmw_vsock_vmci_transport
vmmon                  80249  0 
rfcomm                 69070  12 
bnep                   19564  2 
parport_pc             32701  0 
ppdev                  17671  0 
binfmt_misc            17468  1 
joydev                 17377  0 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  1 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
arc4                   12608  2 
iwldvm                237440  0 
mac80211              596969  1 iwldvm
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            17369  0 
dcdbas                 14847  1 dell_laptop
dm_multipath           22843  0 
scsi_dh                14882  1 dm_multipath
snd_hda_codec_hdmi     41276  1 
snd_hda_codec_realtek    51465  1 
snd_hda_intel          48171  3 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
microcode              23518  0 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
psmouse                97626  0 
serio_raw              13413  0 
uvcvideo               80885  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
videobuf2_vmalloc      13216  1 uvcvideo
btusb                  28267  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
rts5139               331166  0 
videodev              133390  2 uvcvideo,videobuf2_core
bluetooth             371874  22 bnep,btusb,rfcomm
iwlwifi               165398  1 iwldvm
cfg80211              479757  3 iwlwifi,mac80211,iwldvm
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                21080  0 
soundcore              12680  1 snd
mei_me                 18421  0 
mei                    77692  1 mei_me
mac_hid                13205  0 
coretemp               13435  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
dm_mirror              22056  0 
dm_region_hash         20784  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
i915                  655752  4 
r8169                  67341  0 
ahci                   25819  1 
libahci                31898  1 ahci
mii                    13934  1 r8169
i2c_algo_bit           13413  1 i915
drm_kms_helper         52651  1 i915
wmi                    19070  1 dell_wmi
video                  19318  1 i915
drm                   296739  5 i915,drm_kms_helper
```

5> xorg.0.log file:
Although I get this when run in terminal:
"The program 'pastebinit' can be found in the following packages: * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>"

But here is the log file details
```
[    23.012] X.Org X Server 1.14.5
Release Date: 2013-12-12
[    23.012] X Protocol Version 11, Revision 0
[    23.012] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    23.012] Current Operating System: Linux vinay-Inspiron-5521 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64
[    23.012] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=bfcf7d92-a0ac-4eaf-a131-db0b4fec8458 ro quiet splash vt.handoff=7
[    23.012] Build Date: 17 December 2013  10:06:15AM
[    23.012] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    23.012] Current version of pixman: 0.30.2
[    23.012]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    23.012] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.012] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr  8 20:03:43 2014
[    23.042] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.042] (==) No Layout section.  Using the first Screen section.
[    23.042] (==) No screen section available. Using defaults.
[    23.042] (**) |-->Screen "Default Screen Section" (0)
[    23.042] (**) |   |-->Monitor "<default monitor>"
[    23.042] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    23.042] (==) Automatically adding devices
[    23.042] (==) Automatically enabling devices
[    23.042] (==) Automatically adding GPU devices
[    23.042] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.042]     Entry deleted from font path.
[    23.042] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    23.042]     Entry deleted from font path.
[    23.042] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    23.042]     Entry deleted from font path.
[    23.042] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    23.042]     Entry deleted from font path.
[    23.042] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    23.042]     Entry deleted from font path.
[    23.042] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    23.042] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.042] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.042] (II) Loader magic: 0x7f5dc6453d20
[    23.042] (II) Module ABI versions:
[    23.042]     X.Org ANSI C Emulation: 0.4
[    23.042]     X.Org Video Driver: 14.1
[    23.042]     X.Org XInput driver : 19.1
[    23.042]     X.Org Server Extension : 7.0
[    23.042] (II) xfree86: Adding drm device (/dev/dri/card0)
[    23.043] (--) PCI:*(0:0:2:0) 8086:0166:1028:0597 rev 9, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00003000/64
[    23.043] (II) Open ACPI successful (/var/run/acpid.socket)
[    23.043] Initializing built-in extension Generic Event Extension
[    23.043] Initializing built-in extension SHAPE
[    23.043] Initializing built-in extension MIT-SHM
[    23.043] Initializing built-in extension XInputExtension
[    23.043] Initializing built-in extension XTEST
[    23.043] Initializing built-in extension BIG-REQUESTS
[    23.043] Initializing built-in extension SYNC
[    23.043] Initializing built-in extension XKEYBOARD
[    23.043] Initializing built-in extension XC-MISC
[    23.043] Initializing built-in extension SECURITY
[    23.043] Initializing built-in extension XINERAMA
[    23.043] Initializing built-in extension XFIXES
[    23.043] Initializing built-in extension RENDER
[    23.043] Initializing built-in extension RANDR
[    23.043] Initializing built-in extension COMPOSITE
[    23.043] Initializing built-in extension DAMAGE
[    23.043] Initializing built-in extension MIT-SCREEN-SAVER
[    23.043] Initializing built-in extension DOUBLE-BUFFER
[    23.043] Initializing built-in extension RECORD
[    23.043] Initializing built-in extension DPMS
[    23.043] Initializing built-in extension X-Resource
[    23.043] Initializing built-in extension XVideo
[    23.043] Initializing built-in extension XVideo-MotionCompensation
[    23.043] Initializing built-in extension SELinux
[    23.043] Initializing built-in extension XFree86-VidModeExtension
[    23.044] Initializing built-in extension XFree86-DGA
[    23.044] Initializing built-in extension XFree86-DRI
[    23.044] Initializing built-in extension DRI2
[    23.044] (II) "glx" will be loaded by default.
[    23.044] (WW) "xmir" is not to be loaded by default. Skipping.
[    23.044] (II) LoadModule: "dri2"
[    23.044] (II) Module "dri2" already built-in
[    23.044] (II) LoadModule: "glamoregl"
[    23.080] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    23.645] (II) Module glamoregl: vendor="X.Org Foundation"
[    23.645]     compiled for 1.14.2.901, module version = 0.5.1
[    23.645]     ABI class: X.Org ANSI C Emulation, version 0.4
[    23.645] (II) LoadModule: "glx"
[    23.659] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    23.659] (II) Module glx: vendor="X.Org Foundation"
[    23.659]     compiled for 1.14.5, module version = 1.0.0
[    23.659]     ABI class: X.Org Server Extension, version 7.0
[    23.659] (==) AIGLX enabled
[    23.659] Loading extension GLX
[    23.659] (==) Matched intel as autoconfigured driver 0
[    23.659] (==) Matched intel as autoconfigured driver 1
[    23.659] (==) Matched vesa as autoconfigured driver 2
[    23.659] (==) Matched modesetting as autoconfigured driver 3
[    23.659] (==) Matched fbdev as autoconfigured driver 4
[    23.659] (==) Assigned the driver to the xf86ConfigLayout
[    23.659] (II) LoadModule: "intel"
[    23.659] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    23.702] (II) Module intel: vendor="X.Org Foundation"
[    23.702]     compiled for 1.14.3, module version = 2.99.904
[    23.702]     Module class: X.Org Video Driver
[    23.702]     ABI class: X.Org Video Driver, version 14.1
[    23.702] (II) LoadModule: "vesa"
[    23.702] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.702] (II) Module vesa: vendor="X.Org Foundation"
[    23.702]     compiled for 1.14.1, module version = 2.3.2
[    23.702]     Module class: X.Org Video Driver
[    23.702]     ABI class: X.Org Video Driver, version 14.1
[    23.702] (II) LoadModule: "modesetting"
[    23.702] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    23.702] (II) Module modesetting: vendor="X.Org Foundation"
[    23.702]     compiled for 1.14.1, module version = 0.8.0
[    23.702]     Module class: X.Org Video Driver
[    23.702]     ABI class: X.Org Video Driver, version 14.1
[    23.702] (II) LoadModule: "fbdev"
[    23.702] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.702] (II) Module fbdev: vendor="X.Org Foundation"
[    23.702]     compiled for 1.14.1, module version = 0.4.3
[    23.702]     Module class: X.Org Video Driver
[    23.702]     ABI class: X.Org Video Driver, version 14.1
[    23.702] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43, HD Graphics,
    HD Graphics 2000, HD Graphics 3000, HD Graphics 2500,
    HD Graphics 4000, HD Graphics P4000, HD Graphics 4600,
    HD Graphics 5000, HD Graphics P4600/P4700, Iris(TM) Graphics 5100,
    HD Graphics 4400, HD Graphics 4200, Iris(TM) Pro Graphics 5200
[    23.703] (II) VESA: driver for VESA chipsets: vesa
[    23.703] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    23.703] (II) FBDEV: driver for framebuffer: fbdev
[    23.703] (++) using VT number 8


[    23.705] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.904-0ubuntu2 (Timo Aaltonen <tjaalton@ubuntu.com>)
[    23.705] (WW) Falling back to old probe method for vesa
[    23.705] (WW) Falling back to old probe method for modesetting
[    23.705] (WW) Falling back to old probe method for fbdev
[    23.705] (II) Loading sub module "fbdevhw"
[    23.705] (II) LoadModule: "fbdevhw"
[    23.705] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    23.705] (II) Module fbdevhw: vendor="X.Org Foundation"
[    23.705]     compiled for 1.14.5, module version = 0.0.2
[    23.705]     ABI class: X.Org Video Driver, version 14.1
[    23.705] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    23.705] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    23.705] (==) intel(0): RGB weight 888
[    23.705] (==) intel(0): Default visual is TrueColor
[    23.705] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4000
[    23.706] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[    23.706] (**) intel(0): Framebuffer tiled
[    23.706] (**) intel(0): Pixmaps tiled
[    23.706] (**) intel(0): "Tear free" disabled
[    23.706] (**) intel(0): Forcing per-crtc-pixmaps? no
[    23.706] (II) intel(0): Output LVDS1 has no monitor section
[    23.706] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
[    23.706] (II) intel(0): Output VGA1 has no monitor section
[    23.706] (II) intel(0): Output HDMI1 has no monitor section
[    23.706] (II) intel(0): Output DP1 has no monitor section
[    23.706] (II) intel(0): Output VIRTUAL1 has no monitor section
[    23.706] (--) intel(0): Output LVDS1 using initial mode 1366x768 on pipe 0
[    23.706] (==) intel(0): DPI set to (96, 96)
[    23.706] (II) Loading sub module "dri2"
[    23.706] (II) LoadModule: "dri2"
[    23.706] (II) Module "dri2" already built-in
[    23.706] (II) UnloadModule: "vesa"
[    23.706] (II) Unloading vesa
[    23.706] (II) UnloadModule: "modesetting"
[    23.706] (II) Unloading modesetting
[    23.706] (II) UnloadModule: "fbdev"
[    23.706] (II) Unloading fbdev
[    23.706] (II) UnloadSubModule: "fbdevhw"
[    23.706] (II) Unloading fbdevhw
[    23.706] (==) Depth 24 pixmap format is 32 bpp
[    23.706] (II) intel(0): SNA initialized with Ivybridge (gen7, gt2) backend
[    23.706] (==) intel(0): Backing store disabled
[    23.706] (==) intel(0): Silken mouse enabled
[    23.706] (II) intel(0): HW Cursor enabled
[    23.706] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    23.706] (==) intel(0): DPMS enabled
[    23.706] (II) intel(0): [DRI2] Setup complete
[    23.706] (II) intel(0): [DRI2]   DRI driver: i965
[    23.706] (II) intel(0): direct rendering: DRI2 Enabled
[    23.706] (==) intel(0): hotplug detection: "enabled"
[    23.706] (--) RandR disabled
[    23.710] (II) SELinux: Disabled on system
[    23.956] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    23.956] (II) AIGLX: enabled GLX_INTEL_swap_event
[    23.956] (II) AIGLX: enabled GLX_ARB_create_context
[    23.956] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    23.956] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    23.956] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    23.956] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    23.956] (II) AIGLX: Loaded and initialized i965
[    23.956] (II) GLX: Initialized DRI2 GL provider for screen 0
[    23.957] (II) intel(0): switch to mode 1366x768@60.0 on pipe 0 using LVDS1, position (0, 0), rotation normal
[    23.976] (II) intel(0): Setting screen physical size to 361 x 203
[    23.981] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.982] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    23.982] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.982] (II) LoadModule: "evdev"
[    23.983] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.997] (II) Module evdev: vendor="X.Org Foundation"
[    23.997]     compiled for 1.14.1, module version = 2.7.3
[    23.997]     Module class: X.Org XInput Driver
[    23.997]     ABI class: X.Org XInput driver, version 19.1
[    23.997] (II) Using input driver 'evdev' for 'Power Button'
[    23.997] (**) Power Button: always reports core events
[    23.997] (**) evdev: Power Button: Device: "/dev/input/event2"
[    23.997] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.997] (--) evdev: Power Button: Found keys
[    23.997] (II) evdev: Power Button: Configuring as keyboard
[    23.997] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    23.997] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    23.997] (**) Option "xkb_rules" "evdev"
[    23.997] (**) Option "xkb_model" "pc105"
[    23.997] (**) Option "xkb_layout" "us"
[    23.997] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    23.997] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    23.997] (II) Using input driver 'evdev' for 'Video Bus'
[    23.997] (**) Video Bus: always reports core events
[    23.997] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    23.997] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    23.997] (--) evdev: Video Bus: Found keys
[    23.997] (II) evdev: Video Bus: Configuring as keyboard
[    23.997] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4/event4"
[    23.997] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    23.997] (**) Option "xkb_rules" "evdev"
[    23.997] (**) Option "xkb_model" "pc105"
[    23.997] (**) Option "xkb_layout" "us"
[    23.998] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.998] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.998] (II) Using input driver 'evdev' for 'Power Button'
[    23.998] (**) Power Button: always reports core events
[    23.998] (**) evdev: Power Button: Device: "/dev/input/event0"
[    23.998] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.998] (--) evdev: Power Button: Found keys
[    23.998] (II) evdev: Power Button: Configuring as keyboard
[    23.998] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C0C:00/input/input0/event0"
[    23.998] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    23.998] (**) Option "xkb_rules" "evdev"
[    23.998] (**) Option "xkb_model" "pc105"
[    23.998] (**) Option "xkb_layout" "us"
[    23.998] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    23.998] (II) No input driver specified, ignoring this device.
[    23.998] (II) This device may have been added with another device file.
[    23.998] (II) config/udev: Adding drm device (/dev/dri/card0)
[    23.998] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    23.998] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD (/dev/input/event5)
[    23.998] (**) Laptop_Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[    23.998] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD'
[    23.998] (**) Laptop_Integrated_Webcam_HD: always reports core events
[    23.998] (**) evdev: Laptop_Integrated_Webcam_HD: Device: "/dev/input/event5"
[    23.998] (--) evdev: Laptop_Integrated_Webcam_HD: Vendor 0xbda Product 0x58c2
[    23.998] (--) evdev: Laptop_Integrated_Webcam_HD: Found keys
[    23.998] (II) evdev: Laptop_Integrated_Webcam_HD: Configuring as keyboard
[    23.998] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input5/event5"
[    23.998] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD" (type: KEYBOARD, id 9)
[    23.998] (**) Option "xkb_rules" "evdev"
[    23.998] (**) Option "xkb_model" "pc105"
[    23.998] (**) Option "xkb_layout" "us"
[    23.999] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event6)
[    23.999] (II) No input driver specified, ignoring this device.
[    23.999] (II) This device may have been added with another device file.
[    23.999] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event7)
[    23.999] (II) No input driver specified, ignoring this device.
[    23.999] (II) This device may have been added with another device file.
[    23.999] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event8)
[    23.999] (II) No input driver specified, ignoring this device.
[    23.999] (II) This device may have been added with another device file.
[    23.999] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    23.999] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    23.999] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    23.999] (**) AT Translated Set 2 keyboard: always reports core events
[    23.999] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    23.999] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    23.999] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    23.999] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    23.999] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    23.999] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    23.999] (**) Option "xkb_rules" "evdev"
[    23.999] (**) Option "xkb_model" "pc105"
[    23.999] (**) Option "xkb_layout" "us"
[    23.999] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event10)
[    23.999] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    23.999] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    23.999] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    23.999] (II) LoadModule: "synaptics"
[    24.000] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    24.000] (II) Module synaptics: vendor="X.Org Foundation"
[    24.000]     compiled for 1.14.2, module version = 1.7.1
[    24.000]     Module class: X.Org XInput Driver
[    24.000]     ABI class: X.Org XInput driver, version 19.1
[    24.000] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    24.000] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    24.000] (**) Option "Device" "/dev/input/event10"
[    24.020] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5674 (res 44)
[    24.020] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4754 (res 68)
[    24.020] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    24.020] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    24.020] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    24.020] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    24.020] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    24.020] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    24.032] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input10/event10"
[    24.032] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    24.032] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    24.032] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    24.032] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.037
[    24.032] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    24.032] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    24.032] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    24.032] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    24.032] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    24.032] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    24.032] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    24.033] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event9)
[    24.033] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    24.033] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    24.033] (**) Dell WMI hotkeys: always reports core events
[    24.033] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event9"
[    24.033] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    24.033] (--) evdev: Dell WMI hotkeys: Found keys
[    24.033] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    24.033] (**) Option "config_info" "udev:/sys/devices/virtual/input/input9/event9"
[    24.033] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 12)
[    24.033] (**) Option "xkb_rules" "evdev"
[    24.033] (**) Option "xkb_model" "pc105"
[    24.033] (**) Option "xkb_layout" "us"
[    24.212] (II) XKB: reuse xkmfile /var/lib/xkb/server-CB537B66032B0DBE0AE956F537017A59DB020654.xkm
[    38.073] (II) XKB: reuse xkmfile /var/lib/xkb/server-CB537B66032B0DBE0AE956F537017A59DB020654.xkm
[    38.716] (II) intel(0): EDID vendor "LGD", prod id 939
[    38.716] (II) intel(0): Printing DDC gathered Modelines:
[    38.716] (II) intel(0): Modeline "1366x768"x0.0   76.75  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    38.716] (II) intel(0): Modeline "1366x768"x0.0   51.16  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    39.126] (II) intel(0): EDID vendor "LGD", prod id 939
[    39.126] (II) intel(0): Printing DDC gathered Modelines:
[    39.126] (II) intel(0): Modeline "1366x768"x0.0   76.75  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    39.126] (II) intel(0): Modeline "1366x768"x0.0   51.16  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    39.922] (II) intel(0): EDID vendor "LGD", prod id 939
[    39.922] (II) intel(0): Printing DDC gathered Modelines:
[    39.922] (II) intel(0): Modeline "1366x768"x0.0   76.75  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    39.922] (II) intel(0): Modeline "1366x768"x0.0   51.16  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (31.6 kHz e)
[    40.103] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    40.105] (II) XKB: reuse xkmfile /var/lib/xkb/server-AC25B5D7A31535A97485B57C0DD8AA1C5B2189F5.xkm
[    43.645] (II) XKB: reuse xkmfile /var/lib/xkb/server-AC25B5D7A31535A97485B57C0DD8AA1C5B2189F5.xkm
[    43.649] (II) XKB: reuse xkmfile /var/lib/xkb/server-AC25B5D7A31535A97485B57C0DD8AA1C5B2189F5.xkm
[    43.652] (II) XKB: reuse xkmfile /var/lib/xkb/server-AC25B5D7A31535A97485B57C0DD8AA1C5B2189F5.xkm
[    43.656] (II) XKB: reuse xkmfile /var/lib/xkb/server-AC25B5D7A31535A97485B57C0DD8AA1C5B2189F5.xkm
[    43.660] (II) XKB: reuse xkmfile /var/lib/xkb/server-AC25B5D7A31535A97485B57C0DD8AA1C5B2189F5.xkm
[    43.663] (II) XKB: reuse xkmfile /var/lib/xkb/server-AC25B5D7A31535A97485B57C0DD8AA1C5B2189F5.xkm
[    43.667] (II) XKB: reuse xkmfile /var/lib/xkb/server-AC25B5D7A31535A97485B57C0DD8AA1C5B2189F5.xkm
[    43.670] (II) XKB: reuse xkmfile /var/lib/xkb/server-AC25B5D7A31535A97485B57C0DD8AA1C5B2189F5.xkm
[    59.947] (II) intel(0): EDID vendor "LGD", prod id 939
[    59.947] (II) intel(0): Printing DDC gathered Modelines:
[    59.947] (II) intel(0): Modeline "1366x768"x0.0   76.75  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[    59.947] (II) intel(0): Modeline "1366x768"x0.0   51.16  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (31.6 kHz e)
[   132.077] (II) intel(0): EDID vendor "LGD", prod id 939
[   132.078] (II) intel(0): Printing DDC gathered Modelines:
[   132.078] (II) intel(0): Modeline "1366x768"x0.0   76.75  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[   132.078] (II) intel(0): Modeline "1366x768"x0.0   51.16  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (31.6 kHz e)
[   621.610] (II) intel(0): EDID vendor "LGD", prod id 939
[   621.610] (II) intel(0): Printing DDC gathered Modelines:
[   621.610] (II) intel(0): Modeline "1366x768"x0.0   76.75  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[   621.610] (II) intel(0): Modeline "1366x768"x0.0   51.16  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (31.6 kHz e)
[  1045.668] (II) intel(0): EDID vendor "LGD", prod id 939
[  1045.668] (II) intel(0): Printing DDC gathered Modelines:
[  1045.668] (II) intel(0): Modeline "1366x768"x0.0   76.75  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[  1045.668] (II) intel(0): Modeline "1366x768"x0.0   51.16  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (31.6 kHz e)
[  1047.058] (II) intel(0): EDID vendor "LGD", prod id 939
[  1047.058] (II) intel(0): Printing DDC gathered Modelines:
[  1047.058] (II) intel(0): Modeline "1366x768"x0.0   76.75  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (47.4 kHz eP)
[  1047.058] (II) intel(0): Modeline "1366x768"x0.0   51.16  1366 1414 1446 1618  768 771 776 790 +hsync -vsync (31.6 kHz e)
```

---

### Post by Toz on 2014-04-08
Lets try this first.

With root privileges, create the file /usr/share/X11/xorg.conf.d/20-intel.conf:
```
sudo -i gedit  /usr/share/X11/xorg.conf.d/20-intel.conf
```
...with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
...and save the file.

Reboot to test.

---

### Post by Vinay Balraj on 2014-04-09
Wowww... @Toz, you're my life saver mann... This fix works like a charm, Now i can reduce brightness to values of even zero, making the display appear to be off.. :D which is unheard of in windows..

Now for the disk mount, you would suggest creating a separate thread is it? would it be possible to give me a few pointers on how to go about it?

Thanks a lott.. how do I thank you in person?

---

### Post by Toz on 2014-04-09
> **Vinay Balraj said:**
> Wowww... @Toz, you're my life saver mann... This fix works like a charm, Now i can reduce brightness to values of even zero, making the display appear to be off.. :D which is unheard of in windows..
Glad to hear it worked.

> Now for the disk mount, you would suggest creating a separate thread is it? would it be possible to give me a few pointers on how to go about it?
Yes, I believe it is best to create a new thread - it will draw the attention of those with more experience in those issues. You can copy/paste the mount content from above into a new thread in the "General Help" category with the Title "Unable to mount Windows partition"

> Thanks a lott.. how do I thank you in person?
I'm usually running down by the lakefront in Toronto Canada. Grab some running shoes and lets run a few kilometers. 
lol. (just kidding)

---

### Post by Vinay Balraj on 2014-04-09
@Toz, I would if I was either in Canada or you were in India... LOL, thanks for the help though.. :P :D

---

