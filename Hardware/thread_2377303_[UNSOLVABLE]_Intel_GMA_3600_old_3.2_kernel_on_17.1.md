---
title: "[UNSOLVABLE] Intel GMA 3600: old 3.2 kernel on 17.10 for cedarview-graphics-*"
date: 2017-11-11
forum: Hardware
---

### Post by uragno on 2017-11-11
Hi all!

Recently they gave me an *Asus Eee Seashell 1011CX* (*EU version*); after reading some links[SUP]1[/SUP] around I managed to get [FONT=courier new]precise[/FONT] [FONT=courier new]i386[/FONT] working fine with [FONT=courier new]cedarview-graphics-drivers[/FONT] and kernel 3.2 ([FONT=courier new]3.2.0-126-generic #169-Ubuntu SMP[/FONT]).

After completing server-installation ([FONT=courier new]expert command-line install[/FONT], from which I could choose the exact kernel version) I installed [FONT=courier new]lubuntu-desktop[/FONT] and [FONT=courier new]gdm[/FONT] ([FONT=courier new]lightdm[/FONT] has bugs with [FONT=courier new]cedarview-graphics-drivers[/FONT] it cant' start after boot: remains stuck.)

[SIZE=2]_>>>QUESTION<<<_: I wonder if it is possible to grab 17.10 32bit, install it on 1011CX and then manually build kernel version to match [FONT=courier new]cedarview-graphics-drivers[/FONT]'s requirements and install the latter.[/SIZE]

Maybe old kernel release will need downgrading  [FONT=courier new]Xorg[/FONT]  and [FONT=courier new]systemd[/FONT], but this is not too much a problem, 'cause I stil l have rest of softwares updated to the latest versions. And anyway, the (downgraded)versions will surely be updated anyway respect to [FONT=courier new]precise[/FONT] (I hope! :lol:).


Some infos:
[COLOR=#008000]**$ uname -a**[/COLOR]
```
Linux ###myhostname### 3.2.0-126-generic #169-Ubuntu SMP Fri Mar 31 14:16:01 UTC 2017 i686 i686 i386 GNU/Linux
```

**[COLOR=#008000]$ aptitude show xserver-xorg-core[/COLOR]**
```
xserver-xorg-core                        
Stato: installato
Installato automaticamente: no
Versione: 2:1.11.4-0ubuntu10.17
Priorità: opzionale
Sezione: x11
Responsabile: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architettura: i386
Dimensione pacchetto installato: 4251 k
Dipende: xserver-common (>= 2:1.11.4-0ubuntu10.17), keyboard-configuration, udev (>= 149), libc6 (>= 2.15), libdrm2 (>= 2.3.1), libgcrypt11 (>=
         1.4.5), libpciaccess0 (>= 0.10.7), libpixman-1-0 (>= 0.30.0), libudev0 (>= 147), libxau6, libxdmcp6, libxfont1 (>= 1:1.4.2)
Raccomanda: libgl1-mesa-dri (>= 7.10.2-4)
Consiglia: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Rende difettoso: libgl1-mesa-dri (< 7.10.2-4), libgl1-mesa-dri-experimental (< 7.10.2-4), qt4-x11 (< 4:4.8.0-1ubuntu2), unity (< 5.0.0), utouch-frame
                 (< 2.1.0), utouch-geis (< 2.2.3), xserver-xorg-input, xserver-xorg-input-2, xserver-xorg-input-2.1, xserver-xorg-input-4,
                 xserver-xorg-input-7, xserver-xorg-input-joystick (<= 1:1.5.0-3), xserver-xorg-input-synaptics (<= 1.2.2-1ubuntu4),
                 xserver-xorg-input-tslib (<= 0.0.6-3), xserver-xorg-input-vmmouse (<= 1:12.6.5-4ubuntu2), xserver-xorg-input-wacom (<=
                 0.10.5+20100415-1), xserver-xorg-video, xserver-xorg-video-1.0, xserver-xorg-video-1.9, xserver-xorg-video-2, xserver-xorg-video-4,
                 xserver-xorg-video-5, xserver-xorg-video-6, xserver-xorg-video-cyrix (<= 1:1.1.0-8), xserver-xorg-video-i810 (< 2:2.4),
                 xserver-xorg-video-imstt (<= 1:1.1.0-7), xserver-xorg-video-nsc (<= 1:2.8.3-4), xserver-xorg-video-sunbw2 (<= 1:1.1.0-5),
                 xserver-xorg-video-v4l (< 1:0.2.0), xserver-xorg-video-vga (<= 1:4.1.0-8)
Fornisce: xorg-input-abi-16, xorg-video-abi-11
Fornito da: xserver-xorg-core-lts-quantal, xserver-xorg-core-lts-raring, xserver-xorg-core-lts-saucy, xserver-xorg-core-lts-trusty
Descrizione: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating systems, which is derived from the XFree86 4.x series of X servers. 
 
 The Xorg server supports most modern graphics hardware from most vendors, and supersedes all XFree86 X servers. 
 
 More information about X.Org can be found at: <URL:http://www.X.org> 
 
 This package is built from the X.org xserver module.
```

[COLOR=#008000]**$ aptitude show cedarview-graphics-drivers**[/COLOR]
```
Pacchetto: cedarview-graphics-drivers               
Stato: installato
Installato automaticamente: no
Versione: 20120717-0ubuntu1
Priorità: opzionale
Sezione: multiverse/x11
Responsabile: Jani Monoses <jani@ubuntu.com>
Architettura: i386
Dimensione pacchetto installato: 9193 k
Dipende: libc6 (>= 2.15), libdrm2 (>= 2.4.16), libgcc1 (>= 1:4.1.1), libpciaccess0, libpixman-1-0, libstdc++6 (>= 4.1.1), libudev0 (>= 147), libwsbm1,
         libx11-6, libxext6, libxfixes3, cedarview-drm, xserver-xorg-core (>= 2:1.10.99.901), xorg-video-abi-11
Pre-dipende: multiarch-support
Descrizione: Intel binary Xorg driver for GMA3600 (Cedarview) GPUs.
 This package contains the proprietary firmware and drivers needed to run hardware accelerated Open GLES 2.0 under X11 on Intel Cedarview based
 hardware.
```

**[COLOR=#008000]$ cat /etc/default/grub[/COLOR]**
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

**[COLOR=#008000]$ lspci -vvknn[/COLOR]**
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller [8086:0be1] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device [1043:84a9]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 44
    Region 0: Memory at dfc00000 (32-bit, non-prefetchable) [size=1M]
    Region 1: I/O ports at f0e0 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pvrsrvkm
    Kernel modules: cedarview_gfx
```

[COLOR=#008000]**$ lsmod**[/COLOR]
```
Module                  Size  Used by
joydev                 17393  0 
snd_hda_codec_hdmi     31823  1 
snd_hda_codec_realtek   174385  1 
rfcomm                 38139  0 
eeepc_wmi              12949  0 
asus_wmi               19624  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
bluetooth             158410  10 rfcomm,bnep
psmouse                97340  0 
serio_raw              13027  0 
snd_hda_intel          32719  0 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               67203  0 
snd_seq_midi           13132  0 
videodev               86588  1 uvcvideo
snd_rawmidi            25832  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
ath9k                 117559  0 
mac80211              444736  1 ath9k
snd_seq                51677  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28983  2 snd_pcm,snd_seq
ath9k_common           13781  1 ath9k
ath9k_hw              391626  2 ath9k,ath9k_common
cedarview_gfx         381314  4 
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178877  3 ath9k,mac80211,ath
snd                    62250  10 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_seq_device,snd_timer
ttm                    64734  1 cedarview_gfx
drm_kms_helper         32561  1 cedarview_gfx
drm                   196391  6 cedarview_gfx,ttm,drm_kms_helper
mac_hid                13077  0 
i2c_algo_bit           13199  1 cedarview_gfx
video                  19115  1 cedarview_gfx
wmi                    18744  1 asus_wmi
shpchp                 32265  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
atl1c                  36718  0
```

[COLOR=#008000]**$ lsb_release -a**[/COLOR]
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise
```

**[COLOR=#008000]$ cat /usr/share/intel-cdv/X11/xorg.conf.d/61-cdv-pvr.conf[/COLOR]** 
```
Section "Device"
        Option      "DRIDisableVSync"   "False"
        Identifier  "Card0"
        Driver      "pvr"
        BusID       "PCI:0:2:0"
        Option      "SoftEXA"           "Off"
        Option      "FlipChain"         "On"
EndSection

Section "ServerLayout"
        Identifier  "default screen"
        Option      "AIGLX"             "Off"
EndSection
```

Thanks!! ;):KS


[HR][/HR][SUP]1[/SUP]: [https://ef.gy/ubuntu-cedarview-drivers](https://ef.gy/ubuntu-cedarview-drivers) - [https://askubuntu.com/questions/290515/how-to-install-intel-cedarview-drivers-on-ubuntu-12-10-or-higher](https://askubuntu.com/questions/290515/how-to-install-intel-cedarview-drivers-on-ubuntu-12-10-or-higher)

---

### Post by Yellow Pasque on 2017-11-13
> will need downgrading Xorg

Yes, it will, downgrading to Xserver 1.11 and that sounds like a dependency nightmare.

---

### Post by uragno on 2017-11-16
Ok, maybe it will be a mess, but I'd like to try anyway. 

So.. What are the correct steps (or related links to docs/howtos) that I need to follow to get 3.2 kernel and compile/build it on 17.10 i386?

Thanks!

---

### Post by mörgæs on 2017-11-19
Why do you want to run such old kernels?

---

### Post by Yellow Pasque on 2017-11-19
> **mörgæs said:**
> Why do you want to run such old kernels?

To use the old closed source Cedarview graphics driver: [https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1132584](https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1132584)
Intel used PowerVR graphics on some Atoms instead of their own Intel graphics. PowerVR never open-sourced or updated their drivers though, so Linux users were, well, screwed.

---

### Post by mörgæs on 2017-11-19
Thanks for info.

---

### Post by uragno on 2017-11-19
... So... No way to get old kernel on 17.10 i386, then?

---

### Post by Yellow Pasque on 2017-11-19
*Shrug* You can try it, but if it breaks, you keep the pieces.
Install the headers and images package.
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.95/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.95/)

That's not even half the battle though. Building the old Xserver and getting it to play nicely with the existing Xserver packages is the tough part. I don't have any advice for you. It feels quixotic to me. I feel like you've got a gun pointed at your foot and are asking for ammo.

---

### Post by Yellow Pasque on 2017-11-21
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-4.15-Kernel-Boot-Time](https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-4.15-Kernel-Boot-Time)

> Linux 4.6 through 4.15 Git was chosen since that's as far back as the mainline kernel would work with this Ubuntu 17.10 user-space. Linux 4.5 and older would fail to boot. 

---

### Post by uragno on 2017-11-28
I was planning towork t that this weekend but... :mad: ... So... I'll make this thread UNSOLVED. :(

Thanks for your time [**[COLOR=#000000]Temüjin[/COLOR]**]("https://ubuntuforums.org/member.php?u=327594")

---

### Post by mörgæs on 2017-11-28
I don't know if it counts as a solution but you could install an old unsupported Buntu on it and use it for web surfing only. No e-mail reading or other things that demand a password.

---

