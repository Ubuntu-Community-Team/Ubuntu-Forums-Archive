---
title: "Ubuntu 10.10 + vpccw21fx + nvidia driver = doom"
date: 2010-10-20
forum: Hardware
---

### Post by reduz on 2010-10-20
I'm trying to run ubuntu on a vpccw21fx Sony Vaio laptop.

1) X Didn't boot on 10.04 because the nvidia binary driver couldn't find the monitor. Added the EDID to xorg.conf and it worked fine.

2) Upgraded to 10.10 because wifi driver didn't work well on 10.04.

3) On 10.10 Nvidia driver refuses to boot It won't load anymore and stays on a black screen right when X starts. 

I wish to get this working again on 10.10. I'm simply not interested in using ubuntu or linux if i can't get the binary driver working because i need 3D. Please help!

-- update --

It apears the kernel screws up when Xorg loads the nvidia driver, here's the log - 


[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 (Ubuntu 2.6.35-22.35-generic 2.6.35.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=1340ba27-b46c-41de-ad18-afe9cd977a5e ro 

[..]

[   20.259959] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.259974] nvidia 0000:01:00.0: setting latency timer to 64
[   20.259980] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   20.260182] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.12  Fri Oct  8 11:17:08 PDT 2010
[   20.861267] ppdev: user-space parallel port driver
[   21.537074] sky2 0000:04:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
[   21.537444] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.845624] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[   22.034615] EXT4-fs (sda7): re-mounted. Opts: commit=600
[   23.415031] BUG: unable to handle kernel NULL pointer dereference at (null)
[   23.415036] IP: [<(null)>] (null)
[   23.415039] PGD 112f64067 PUD 112fd7067 PMD 0 
[   23.415043] Oops: 0010 [#1] SMP 
[   23.415045] last sysfs file: /sys/bus/acpi/drivers/NVIDIA ACPI Video Driver/uevent
[   23.415048] CPU 2 
[   23.415049] Modules linked in: parport_pc ppdev binfmt_misc rfcomm sco bnep l2cap snd_hda_codec_nvhdmi joydev snd_hda_codec_realtek arc4 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm ath9k nvidia(P) snd_seq_midi snd_rawmidi ath9k_common ath9k_hw ath mac80211 snd_seq_midi_event snd_seq uvcvideo btusb snd_timer snd_seq_device videodev bluetooth v4l1_compat v4l2_compat_ioctl32 cfg80211 snd psmouse serio_raw intel_agp soundcore snd_page_alloc sony_laptop video output lp parport firewire_ohci ahci firewire_core sdhci_pci sky2 crc_itu_t libahci sdhci led_class
[   23.415076] 
[   23.415079] Pid: 1484, comm: Xorg Tainted: P            2.6.35-22-generic #35-Ubuntu VAIO/VPCCW21FX
[   23.415081] RIP: 0010:[<0000000000000000>]  [<(null)>] (null)
[   23.415084] RSP: 0018:ffff8801114c7990  EFLAGS: 00010292
[   23.415085] RAX: 0000000000000161 RBX: ffff880111626000 RCX: 0000000000000000
[   23.415087] RDX: 0000000000000001 RSI: ffff880111626000 RDI: ffff880114894000
[   23.415089] RBP: ffff8801115cdef0 R08: 0000000000000000 R09: 0000000000000000
[   23.415091] R10: 0000000000000098 R11: 0000000000000001 R12: ffff880114894000
[   23.415092] R13: ffff880114894000 R14: 0000000000000000 R15: 0000000000000000
[   23.415095] FS:  00007f3723abd840(0000) GS:ffff880001e80000(0000) knlGS:0000000000000000
[   23.415097] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   23.415099] CR2: 0000000000000000 CR3: 0000000111578000 CR4: 00000000000006e0
[   23.415101] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   23.415102] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   23.415105] Process Xorg (pid: 1484, threadinfo ffff8801114c6000, task ffff880116218000)
[   23.415106] Stack:
[   23.415107]  ffffffffa031c7b9 ffff880111626000 ffff880111626000 0000000000000000
[   23.415110] <0> ffffffffa032d050 0000000000000000 ffff880111626000 ffff880114894000
[   23.415112] <0> ffff880111626000 0000000000000000 ffffffffa032af09 ffff8801115f0000
[   23.415115] Call Trace:
[   23.415312]  [<ffffffffa031c7b9>] ? _nv021430rm+0x13/0x26 [nvidia]
[   23.415470]  [<ffffffffa032d050>] ? _nv021329rm+0xf5/0x1b9 [nvidia]
[   23.415629]  [<ffffffffa032af09>] ? _nv021186rm+0x268/0x4c6 [nvidia]
[   23.415798]  [<ffffffffa036fe07>] ? _nv009131rm+0x86/0x1b3 [nvidia]
[   23.415967]  [<ffffffffa03682fa>] ? _nv009646rm+0x1a0/0x237 [nvidia]
[   23.416162]  [<ffffffffa047e11f>] ? _nv014469rm+0x27b/0x4c9 [nvidia]
[   23.416357]  [<ffffffffa047d043>] ? _nv014749rm+0xea/0x167 [nvidia]
[   23.416448]  [<ffffffffa016f912>] ? _nv014928rm+0xd/0x12 [nvidia]
[   23.416614]  [<ffffffffa0644a3e>] ? _nv002152rm+0x160/0x26f [nvidia]
[   23.416777]  [<ffffffffa0645862>] ? _nv002146rm+0x492/0x65a [nvidia]
[   23.416941]  [<ffffffffa064b279>] ? rm_init_adapter+0x89/0xfd [nvidia]
[   23.417105]  [<ffffffffa066897e>] ? nv_kern_open+0x5ae/0x760 [nvidia]
[   23.417111]  [<ffffffff8115688a>] ? chrdev_open+0x10a/0x200
[   23.417114]  [<ffffffff81156780>] ? chrdev_open+0x0/0x200
[   23.417119]  [<ffffffff81150ce5>] ? __dentry_open+0xe5/0x330
[   23.417123]  [<ffffffff8126061f>] ? security_inode_permission+0x1f/0x30
[   23.417126]  [<ffffffff81151044>] ? nameidata_to_filp+0x54/0x70
[   23.417129]  [<ffffffff8115dbf8>] ? finish_open+0xe8/0x1d0
[   23.417132]  [<ffffffff8116687f>] ? dput+0xdf/0x1b0
[   23.417134]  [<ffffffff8115f056>] ? do_last+0x86/0x460
[   23.417137]  [<ffffffff8116138b>] ? do_filp_open+0x21b/0x660
[   23.417141]  [<ffffffff8116cb9a>] ? alloc_fd+0x10a/0x150
[   23.417144]  [<ffffffff81150a89>] ? do_sys_open+0x69/0x170
[   23.417147]  [<ffffffff81150bd0>] ? sys_open+0x20/0x30
[   23.417151]  [<ffffffff8100a0f2>] ? system_call_fastpath+0x16/0x1b
[   23.417153] Code:  Bad RIP value.
[   23.417157] RIP  [<(null)>] (null)
[   23.417159]  RSP <ffff8801114c7990>
[   23.417160] CR2: 0000000000000000
[   23.417163] ---[ end trace 5b5ed78476f34aaa ]---
[   31.593499] eth0: no IPv6 routers present

---

### Post by disappearedng on 2010-10-24
Same error I am getting here. Just so annoying. I already restored my xorg.conf and purged all nvidia*. What is going on?

---

### Post by PaulW21781 on 2010-10-24
It's an issue which appears to affect *ALL* Sony laptops with Nvidia GT Cards (2xx, 3xx and so-on...) running any 260.xx drivers from Nvidia.

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1593181](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1593181)

Fix suggested in there (way I did it):

**Make a print out of this before you continue and save anything you have open! Also, make sure you are connected to your network before you start!!**

#sudo stop gdm
*Now log in to the shell using your username & pw, yada yada*
#sudo apt-get install nvidia-current
#sudo rm /etc/X11/xorg.conf
#sudo apt-get remove nvidia-current
#wget [ftp://download.nvidia.com/XFree86/Linux-x86/256.53/NVIDIA-Linux-x86-256.53.run](ftp://download.nvidia.com/XFree86/Linux-x86/256.53/NVIDIA-Linux-x86-256.53.run)
#chmod +x NVIDIA-Linux-x86-256.53.run
#sudo ./NVIDIA-Linux-x86-256.53.run -a
#sudo nvidia-xconfig
#sudo nano /etc/X11/xorg.conf

Now, in the xorg.conf file which loads, add the following to the "Device" section:

```
    Option         "ConnectedMonitor" "DFP-0"
    Option         "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"

```(Commands for Nano are:
CTRL+X - Exit when done (will ask you if you want to save, press Y)

For reference, this is my xorg.conf

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "MS_ Nvidia Default Flat Panel"
    HorizSync       62.5 - 68.6
    VertRefresh     50.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 330M"
    Option         "ConnectedMonitor" "DFP-0"
    Option         "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```reboot, and you should be up and running.

Now, a quick note:

If you then open a terminal, and issue

#sudo apt-get autoremove

It will say there are some packages (dkms, nvidia-settings, etc etc) DON'T REMOVE THESE

Instead, write down what it is listing, and then

#sudo apt-get install (packages)

That way, those packages will stay, nvidia-current won't, and you will keep the 256.33 drivers working :)

---

### Post by jjchm on 2010-11-04
Hi, recently i installed Ubuntu 10.10 64 bits in my laptop Sony VPCCW21FX, the procedure for complet that mission are:

1) Download ISO "Alternate Mode", the normal ISO don't boot, blank screen.
2) When the cd is ready, put in your cd-drive, when the initial screen appear, activate the option "nomodeset" (F6 for view the options).
3) Continue with the process.
4) When the S.O. is ready, update your system.
5) Download the nvidia driver in the official site ([www.nvidia.com](www.nvidia.com)), the ultimate driver is the .260, but in some others threads in this forum recommends use the .253 driver. I use that version .253.
6) The procedure for install the nvidia driver is very easy:

- Ctrl+F1, use your username and password
- execute sudo /etc/init.d/gdm stop. 
- chmod +x drivernvidia.run
- ./drivernvidia.run
- Choose "YES" when the installer ask you for create de xorg.conf.

7) reboot your system, before of the initial screen for enter your user and pass, you should see the nvidia logo screen.

That's all for use ubuntu 10.10 64bits in VPCCW21FX. 

The wireless network don't work very well, packet loss (30% - 40% aproximately).
The wire network work perfect. 0% Packet Loss.

Regards.

---

