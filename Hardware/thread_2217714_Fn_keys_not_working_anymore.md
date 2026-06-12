---
title: "Fn keys not working anymore"
date: 2014-04-18
forum: Hardware
---

### Post by mastablasta on 2014-04-18
**Fn keys not working**

[COLOR=#000000][FONT=sans-serif][INDENT]I have HP Pavilion dm1 with E-450. Even before some Fn Keys didn't work, but the important ones did. I never needed the brightness keys until now when i had a presentation outside. I couldn't see anything as i had the laptop on batery and the screen brightness was autoreduced. 

I know these keys worked. Sound keys still work, but wi-fi on off key never worked (though i could toggle that in network manager). i don't know exactly when the backlight keys stopped working as i never needed them before.

when i got home i tried to troubleshoot it a bit but i can't found the culprint. 
Code:
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-19-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro quiet splash acpi_osi=linux acpi_backlight=legacy vt.handoff=7
so far i tried 
acpi_osi=linux
acpi_backlight=vendor
acpi_backlight=legacy
```

i am using fglrx drivers. 

some info on the GPU:
Code:
```
description: VGA compatible controller
product: Wrestler [Radeon HD 6320]
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
```
the touchpad off button doesn't work but i figured i could workarround this in another way.


anyway today i have a few older distros on multiboot USB key, so i though i would give them a try and find were the issue is. all were live session with defautl rradeon driver:
:
Kubuntu 13.10 live (image from January i believe) - only sound FN keys work (as it is now)
Lubuntu 13.04 live - no Fn keys work 
Xubuntu 12.04 live - all Fn keys work !!! (including the wi-fi that never worked in Kubuntu)

So any suggesitons how to find what is causing this or what is the correct setting. It appears to me to be a Kubuntu specific bug. if i am correct i need to report it in launchpad. or is this a kernel (kernel setting?!) issue?

how to troubleshoot? 

i will attempt to get 14.04 beta and see if that one works. really dissapointed at the moment [IMG]https://www.kubuntuforums.net/images/smilies/undecided.gif[/IMG]

Edit: I tried with 14.04 (live session, radeon drivers) - it is also not working. Wi-fi acts like before , sound keys work but screen brightness do not.
[/INDENT]
[/FONT][/COLOR]

---

### Post by varunendra on 2014-04-20
What about the old trick of directly writing brightness values into **/sys/class/backlight/<device>/brightness** file? If you haven't tried it yet, or are not sure what I'm talking about, please post the output of -
```
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```
..and since I am the Least reliable person on the forums these days (posting almost only on Sundays), you might wish to contact Toz (yes, the moderator) to help you out. :p

---

### Post by mastablasta on 2014-04-20
this is the output:
```

 /sys/class/backlight/acpi_video0
4
10
4


```

i will upgrade to 14.04 see if there is any kernel switch in new kernel i could use. ive now tried XUbuntu 14.04 64bit and Ubuntu 14.04 32 bit. Both act as Kubuntu oes. Sound keys work, wi-fi doesn't, brightnes doesn't. I am not sure if monitor switching key would work.why do they do this? i mean if it worked fine why change it? and if they changed it why not fix it so it works again for certian models?

---

### Post by varunendra on 2014-04-20
Whoa! You've got a whole lot of scary questions to which I've got no straight answer at the moment (probably Toz may have, although he is not a developer either as far as I know). :p

I do have a possible workaround though, please try this and see if it helps controlling the brightness -
```
echo 10 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
Does it increase the brightness to full? If yes, try echoing other integer values from 0 to 10 and see if it works as expected. If it does, we can create a simple script and bind it with a hotkey as a substitute to the dedicated hotkey. Dirty, but should be acceptable until the real solution is found.

---

### Post by Toz on 2014-04-20
Lately, I haven't had much luck with getting brightness to work with ATI cards, I'm wondering if something has happened to either the radeon/catalyst drivers or the kernel (or a combination). However, to move forward I would suggest removing any of the kernel parameters that you added to get a baseline. With no extra kernel parameters active, post back:
```
cat /proc/cmdline
lspci -k | grep -iA2 VGA
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
lsmod
```
...and try what varunendra suggests about echo'ing a value into each interface's brightness file that is a value between 0 and the contents of max_brightness.

Example:
> 
$ for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done

 /sys/class/backlight/intel_backlight
3480
3484
3480

$ echo 2440 | sudo tee /sys/class/backlight/intel_backlight/brightness 

By properly documenting the baseline, we can get an idea on how to move forward.

---

### Post by mastablasta on 2014-04-21
varunendra's suggestion crashed the deskotp. had to take the battery out to reset it.

this is the output:
```
cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro quiet splash vt.handoff=7
gregor@gregor-HP:~$ lspci -k | grep -iA2 VGA
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6320]
        Subsystem: Hewlett-Packard Company Device 3387
        Kernel driver in use: fglrx_pci
:~$ for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done

 /sys/class/backlight/acpi_video0
4
10
4
:~$ lsmod
Module                  Size  Used by
ctr                    13049  2 
ccm                    17773  2 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
joydev                 17381  0 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
ath3k                  13318  0 
btusb                  32412  0 
bnep                   19624  2 
kvm_amd                59987  0 
rfcomm                 69160  12 
bluetooth             395423  23 bnep,ath3k,btusb,rfcomm
kvm                   451511  1 kvm_amd
arc4                   12608  2 
psmouse               102222  0 
snd_hda_codec_idt      54645  1 
serio_raw              13462  0 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k_hw              453856  2 ath9k_common,ath9k
snd_rawmidi            30144  1 snd_seq_midi
snd_hda_codec_hdmi     46207  1 
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              626489  1 ath9k
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
cfg80211              484040  3 ath,ath9k,mac80211
k10temp                13126  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
sp5100_tco             13979  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29482  2 snd_pcm,snd_seq
i2c_piix4              22155  0 
binfmt_misc            17468  1 
fglrx                8085343  88 
snd                    69238  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
hp_accel               26012  0 
lis3lv02d              20156  1 hp_accel
input_polldev          13896  1 lis3lv02d
amd_iommu_v2           19054  1 fglrx
soundcore              12680  1 snd
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
ums_realtek            18029  0 
usb_storage            62209  1 ums_realtek
ahci                   25819  2 
r8169                  67581  0 
libahci                32168  1 ahci
mii                    13934  1 r8169
wmi                    19177  1 hp_wmi
video                  19476  0 

```

---

### Post by Toz on 2014-04-21
Can I see your Xorg.0.log file?

And, can you boot with the **video.use_native_backlight=1** kernel parameter (as I understand it, acpi_backlight=vendor has been changed to this parameter in the 3.13+ kernels) and post back the results again as above?

---

### Post by wieman01 on 2014-04-21
First thing you should check is whether your FN keys trigger an ACPI event. Open a terminal and type:
```
acpi_listen
```
Then press any FN key and check if it creates an output. If ACPI_LISTEN does not respond, then you are probably out of luck. Could we focus on the (screen) brightness keys first of all? I can help you get these working fairly easily.

Please post the output of ACPI_LISTEN.

---

### Post by mastablasta on 2014-04-22
first output after using the video native parameter (which didn't work):

```
cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=b8d9906e-6a55-4762-a562-6bc1c558f30d ro video.use_native_backlight=1 quiet splash vt.handoff=7
_[COLOR=#0000ff]:~$[/COLOR]_ lspci -k | grep -iA2 VGA
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6320]
        Subsystem: Hewlett-Packard Company Device 3387
        Kernel driver in use: fglrx_pci
_[COLOR=#0000ff]:~$[/COLOR]_ for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
 /sys/class/backlight/acpi_video0
4
10
1
_[COLOR=#0000ff]:~$[/COLOR]_ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
joydev                 17381  0 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
rfcomm                 69160  12 
bnep                   19624  2 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
ath3k                  13318  0 
videodev              134688  2 uvcvideo,videobuf2_core
btusb                  32412  0 
bluetooth             395423  23 bnep,ath3k,btusb,rfcomm
binfmt_misc            17468  1 
kvm_amd                59987  0 
kvm                   451511  1 kvm_amd
psmouse               102222  0 
serio_raw              13462  0 
arc4                   12608  2 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              626489  1 ath9k
sp5100_tco             13979  0 
k10temp                13126  0 
cfg80211              484040  3 ath,ath9k,mac80211
snd_hda_codec_idt      54645  1 
i2c_piix4              22155  0 
snd_hda_codec_hdmi     46207  1 
snd_hda_intel          52355  10 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
fglrx                8085343  63 
hp_accel               26012  0 
snd                    69238  31 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lis3lv02d              20156  1 hp_accel
input_polldev          13896  1 lis3lv02d
mac_hid                13205  0 
amd_iommu_v2           19054  1 fglrx
soundcore              12680  1 snd
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
usb_storage            62209  1 
r8169                  67581  0 
mii                    13934  1 r8169
ahci                   25819  2 
libahci                32168  1 ahci
wmi                    19177  1 hp_wmi
video                  19476  0 

```

here is the log:

```
 Information [    27.036] (II) Loader magic: 0x7fdc51fb4d60
 Information [    27.036] (II) Module ABI versions:
 Information [    27.036]  X.Org ANSI C Emulation: 0.4
 Information [    27.036]  X.Org Video Driver: 15.0
 Information [    27.036]  X.Org XInput driver : 20.0
 Information [    27.036]  X.Org Server Extension : 8.0
 Information [    27.039] (--) PCI:*(0:0:1:0) 1002:9806:103c:3387 rev 0, Mem @ 0x80000000/268435456, 0x90300000/262144, I/O @ 0x00004000/256
 Information [    27.039] Initializing built-in extension Generic Event Extension
 Information [    27.039] Initializing built-in extension SHAPE
 Information [    27.039] Initializing built-in extension MIT-SHM
 Information [    27.039] Initializing built-in extension XInputExtension
 Information [    27.039] Initializing built-in extension XTEST
 Information [    27.039] Initializing built-in extension BIG-REQUESTS
 Information [    27.039] Initializing built-in extension SYNC
 Information [    27.039] Initializing built-in extension XKEYBOARD
 Information [    27.040] Initializing built-in extension XC-MISC
 Information [    27.040] Initializing built-in extension SECURITY
 Information [    27.040] Initializing built-in extension XINERAMA
 Information [    27.040] Initializing built-in extension XFIXES
 Information [    27.040] Initializing built-in extension RENDER
 Information [    27.040] Initializing built-in extension RANDR
 Information [    27.040] Initializing built-in extension COMPOSITE
 Information [    27.040] Initializing built-in extension DAMAGE
 Information [    27.040] Initializing built-in extension MIT-SCREEN-SAVER
 Information [    27.040] Initializing built-in extension DOUBLE-BUFFER
 Information [    27.040] Initializing built-in extension RECORD
 Information [    27.040] Initializing built-in extension DPMS
 Information [    27.040] Initializing built-in extension Present
 Information [    27.040] Initializing built-in extension DRI3
 Information [    27.040] Initializing built-in extension X-Resource
 Information [    27.040] Initializing built-in extension XVideo
 Information [    27.040] Initializing built-in extension XVideo-MotionCompensation
 Information [    27.040] Initializing built-in extension SELinux
 Information [    27.040] Initializing built-in extension XFree86-VidModeExtension
 Information [    27.040] Initializing built-in extension XFree86-DGA
 Information [    27.040] Initializing built-in extension XFree86-DRI
 Information [    27.040] Initializing built-in extension DRI2
 Information [    27.040] (II) LoadModule: "glx"
 Information [    27.041] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
 Information [    27.041] (II) Module glx: vendor="Advanced Micro Devices, Inc."
 Information [    27.041]  compiled for 6.9.0, module version = 1.0.0
 Information [    27.042] Loading extension GLX
 Information [    27.042] (==) Matched fglrx as autoconfigured driver 0
 Information [    27.042] (==) Matched ati as autoconfigured driver 1
 Information [    27.042] (==) Matched modesetting as autoconfigured driver 2
 Information [    27.042] (==) Matched fbdev as autoconfigured driver 3
 Information [    27.042] (==) Matched vesa as autoconfigured driver 4
 Information [    27.042] (==) Assigned the driver to the xf86ConfigLayout
 Information [    27.042] (II) LoadModule: "fglrx"
 Information [    27.042] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
 Information [    27.091] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
 Information [    27.091]  compiled for 1.4.99.906, module version = 13.35.5
 Information [    27.091]  Module class: X.Org Video Driver
 Information [    27.092] (II) Loading sub module "fglrxdrm"
 Information [    27.092] (II) LoadModule: "fglrxdrm"
 Information [    27.092] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
 Information [    27.181] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
 Information [    27.181]  compiled for 1.4.99.906, module version = 13.35.5
 Information [    27.181] (II) LoadModule: "ati"
 Information [    27.202] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
 Information [    27.203] (II) Module ati: vendor="X.Org Foundation"
 Information [    27.203]  compiled for 1.15.0, module version = 7.3.0
 Information [    27.203]  Module class: X.Org Video Driver
 Information [    27.203]  ABI class: X.Org Video Driver, version 15.0
 Information [    27.203] (II) LoadModule: "radeon"
 Information [    27.203] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
 Information [    27.550] (II) Module radeon: vendor="X.Org Foundation"
 Information [    27.550]  compiled for 1.15.0, module version = 7.3.0
 Information [    27.550]  Module class: X.Org Video Driver
 Information [    27.550]  ABI class: X.Org Video Driver, version 15.0
 Information [    27.550] (II) LoadModule: "modesetting"
 Information [    27.550] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
 Information [    27.551] (II) Module modesetting: vendor="X.Org Foundation"
 Information [    27.551]  compiled for 1.15.0, module version = 0.8.1
 Information [    27.551]  Module class: X.Org Video Driver
 Information [    27.551]  ABI class: X.Org Video Driver, version 15.0
 Information [    27.551] (II) LoadModule: "fbdev"
 Information [    27.552] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
 Information [    27.552] (II) Module fbdev: vendor="X.Org Foundation"
 Information [    27.552]  compiled for 1.15.0, module version = 0.4.4
 Information [    27.552]  Module class: X.Org Video Driver
 Information [    27.552]  ABI class: X.Org Video Driver, version 15.0
 Information [    27.552] (II) LoadModule: "vesa"
 Information [    27.553] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
 Information [    27.553] (II) Module vesa: vendor="X.Org Foundation"
 Information [    27.553]  compiled for 1.15.0, module version = 2.3.3
 Information [    27.553]  Module class: X.Org Video Driver
 Information [    27.553]  ABI class: X.Org Video Driver, version 15.0
 Information [    27.553] (II) AMD Proprietary Linux Driver Version Identifier:13.35.5
 Information [    27.553] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-13.35.1005               
 Information [    27.553] (II) AMD Proprietary Linux Driver Build Date: Mar 12 2014 10:32:23
 Information [    27.553] (II) RADEON: Driver for ATI Radeon chipsets:
 Information  ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
 Information  ATI Radeon Mobility X300 (M24) 3152 (PCIE),
 Information  ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
 Information  ATI Radeon X600 (RV380) 3E50 (PCIE),
 Information  ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
 Information  ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
 Information  ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
 Information  ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
 Information  ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
 Information  ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
 Information  ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
 Information  ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
 Information  ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
 Information  ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
 Information  ATI Radeon IGP330M/340M/350M (U2) 4337,
 Information  ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
 Information  ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
 Information  ATI Radeon X800PRO (R420) JI (AGP),
 Information  ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
 Information  ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
 Information  ATI Radeon Mobility 9800 (M18) JN (AGP),
 Information  ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
 Information  ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
 Information  ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
 Information  ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
 Information  ATI Radeon Mobility M7 LW (AGP),
 Information  ATI Mobility FireGL 7800 M7 LX (AGP),
 Information  ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
 Information  ATI FireGL Mobility 9000 (M9) Ld (AGP),
 Information  ATI Radeon Mobility 9000 (M9) Lf (AGP),
 Information  ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
 Information  ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
 Information  ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
 Information  ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
 Information  ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
 Information  ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
 Information  ATI Radeon Mobility 9600 (M10) NQ (AGP),
 Information  ATI Radeon Mobility 9600 (M11) NR (AGP),
 Information  ATI Radeon Mobility 9600 (M10) NS (AGP),
 Information  ATI FireGL Mobility T2 (M10) NT (AGP),
 Information  ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
 Information  ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
 Information  ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
 Information  ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
 Information  ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
 Information  ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
 Information  ATI Radeon Mobility X300 (M22) 5460 (PCIE),
 Information  ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
 Information  ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
 Information  ATI Radeon X800PRO (R423) UI (PCIE),
 Information  ATI Radeon X800LE (R423) UJ (PCIE),
 Information  ATI Radeon X800SE (R423) UK (PCIE),
 Information  ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
 Information  ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
 Information  ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
 Information  ATI FireGL unknown (R423) UR (PCIE),
 Information  ATI FireGL unknown (R423) UT (PCIE),
 Information  ATI Mobility FireGL V5000 (M26) (PCIE),
 Information  ATI Mobility FireGL V5000 (M26) (PCIE),
 Information  ATI Mobility Radeon X700 XL (M26) (PCIE),
 Information  ATI Mobility Radeon X700 (M26) (PCIE),
 Information  ATI Mobility Radeon X700 (M26) (PCIE),
 Information  ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
 Information  ATI Radeon Mobility 9100 IGP (U3) 5835,
 Information  ATI Radeon XPRESS 200 5954 (PCIE),
 Information  ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
 Information  ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
 Information  ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
 Information  ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
 Information  ATI Radeon XPRESS 200M 5975 (PCIE),
 Information  ATI Radeon XPRESS 200 5A41 (PCIE),
 Information  ATI Radeon XPRESS 200M 5A42 (PCIE),
 Information  ATI Radeon XPRESS 200 5A61 (PCIE),
 Information  ATI Radeon XPRESS 200M 5A62 (PCIE),
 Information  ATI Radeon X300 (RV370) 5B60 (PCIE),
 Information  ATI Radeon X600 (RV370) 5B62 (PCIE),
 Information  ATI Radeon X550 (RV370) 5B63 (PCIE),
 Information  ATI FireGL V3100 (RV370) 5B64 (PCIE),
 Information  ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
 Information  ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
 Information  ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
 Information  ATI Mobility Radeon X800 XT (M28) (PCIE),
 Information  ATI Mobility FireGL V5100 (M28) (PCIE),
 Information  ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
 Information  ATI Radeon X850 XT PE (R480) (PCIE),
 Information  ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
 Information  ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
 Information  ATI Radeon X850 XT (R480) (PCIE),
 Information  ATI Radeon X800XT (R423) 5D57 (PCIE),
 Information  ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
 Information  ATI Radeon X700 PRO (RV410) (PCIE),
 Information  ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
 Information  ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
 Information  ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
 Information  ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
 Information  ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
 Information  ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
 Information  ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
 Information  ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
 Information  ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
 Information  ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
 Information  ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
 Information  ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
 Information  ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
 Information  ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
 Information  ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
 Information  ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
 Information  ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
 Information  ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
 Information  ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
 Information  ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
 Information  ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
 Information  ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
 Information  ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
 Information  ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
 Information  ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
 Information  ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
 Information  ATI Mobility Radeon X1700, ATI Radeon X2300HD,
 Information  ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
 Information  ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
 Information  ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
 Information  ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
 Information  ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
 Information  ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
 Information  ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
 Information  ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
 Information  ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
 Information  ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
 Information  ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
 Information  ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
 Information  ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
 Information  ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
 Information  ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
 Information  ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
 Information  ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
 Information  ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
 Information  ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
 Information  ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
 Information  AMD FireStream 9250, ATI FirePro V8700 (FireGL),
 Information  ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
 Information  ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
 Information  ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
 Information  ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
 Information  ATI Mobility Radeon HD 4670, ATI FirePro M5750,
 Information  ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
 Information  ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
 Information  ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
 Information  ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
 Information  ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
 Information  ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
 Information  ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
 Information  ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
 Information  ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
 Information  ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
 Information  ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
 Information  ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
 Information  ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
 Information  ATI Mobility Radeon HD 3850 X2, ATI RV670,
 Information  ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
 Information  ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
 Information  ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
 Information  ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
 Information  ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
 Information  ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
 Information  ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
 Information  ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
 Information  ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
 Information  ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
 Information  ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
 Information  ATI FireGL V3600, ATI Radeon HD 2600 LE,
 Information  ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
 Information  ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
 Information  ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
 Information  ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
 Information  ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
 Information  ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
 Information  ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
 Information  ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
 Information  ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
 Information  ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
 Information  ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
 Information  ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
 Information  ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
 Information  SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
 Information  ATI Radeon 4100, ATI Mobility Radeon HD 4200,
 Information  ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
 Information  AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
 Information  AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
 Information  AMD Radeon HD 6300 Series Graphics,
 Information  AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
 Information  ATI FirePro (FireGL) Graphics Adapter,
 Information  ATI FirePro (FireGL) Graphics Adapter,
 Information  ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
 Information  AMD Firestream 9350, ATI Radeon HD 5800 Series,
 Information  ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
 Information  ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
 Information  ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
 Information  ATI Mobility Radeon HD 5800 Series,
 Information  ATI FirePro (FireGL) Graphics Adapter,
 Information  ATI FirePro (FireGL) Graphics Adapter,
 Information  ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
 Information  ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
 Information  ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
 Information  ATI Mobility Radeon HD 5000 Series,
 Information  ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
 Information  ATI FirePro (FireGL) Graphics Adapter,
 Information  ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
 Information  ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
 Information  ATI Mobility Radeon HD 5000 Series,
 Information  ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
 Information  ATI Mobility Radeon Graphics, CEDAR,
 Information  ATI FirePro (FireGL) Graphics Adapter,
 Information  ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
 Information  ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
 Information  CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
 Information  AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
 Information  CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
 Information  BARTS, BARTS, Mobility Radeon HD 6000 Series,
 Information  Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
 Information  AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
 Information  AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
 Information  TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
 Information  TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
 Information  CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
 Information  CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
 Information  ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
 Information  ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
 Information  ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
 Information  ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
 Information  TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
 Information  TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
 Information  PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
 Information  VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
 Information  VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
 Information  VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
 Information  OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, HAINAN, HAINAN, HAINAN,
 Information  HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
 Information  BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
 Information  KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
 Information  KABINI, KABINI, KABINI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
 Information  KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
 Information  KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
 Information  HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
 Information  HAWAII, HAWAII, HAWAII, HAWAII
 Information [    27.591] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
 Information [    27.591] (II) FBDEV: driver for framebuffer: fbdev
 Information [    27.591] (II) VESA: driver for VESA chipsets: vesa
 Information [    27.591] (++) using VT number 7
 Information 
 Information [    27.591] (WW) Falling back to old probe method for fglrx
 Information [    27.611] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
 Information [    27.617] ukiDynamicMajor: found major device number 251
 Information [    27.620] (--) Assigning device section with no busID to primary device
 Information [    27.620] (--) Chipset Supported AMD Graphics Processor (0x9806) found
 Information [    27.620] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found
 Information [    27.620] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
 Information [    27.620] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
 Information [    27.620] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
 Information [    27.620] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
 Information [    27.620] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
 Information [    27.620] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
 Information [    27.620] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
 Information [    27.620] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
 Information [    27.620] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
 Information [    27.620] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:0) found
 Information [    27.620] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:1) found
 Information [    27.620] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
 Information [    27.621] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
 Information [    27.622] (II) fglrx(0): pEnt->device->identifier=0x7fdc51d4fdd7
 Information [    27.622] (WW) Falling back to old probe method for modesetting
 Information [    27.622] (EE) open /dev/dri/card0: No such file or directory
 Information [    27.622] (WW) Falling back to old probe method for fbdev
 Information [    27.622] (II) Loading sub module "fbdevhw"
 Information [    27.622] (II) LoadModule: "fbdevhw"
 Information [    27.623] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
 Information [    27.623] (II) Module fbdevhw: vendor="X.Org Foundation"
 Information [    27.623]  compiled for 1.15.1, module version = 0.0.2
 Information [    27.623]  ABI class: X.Org Video Driver, version 15.0
 Information [    27.623] (WW) Falling back to old probe method for vesa
 Information [    27.623] (II) fglrx(0): === [xdl_xs115_atiddxPreInit] === begin
 Information [    27.624] (II) Loading sub module "vgahw"
 Information [    27.624] (II) LoadModule: "vgahw"
 Information [    27.646] (II) Loading /usr/lib/xorg/modules/libvgahw.so
 Information [    27.647] (II) Module vgahw: vendor="X.Org Foundation"
 Information [    27.647]  compiled for 1.15.1, module version = 0.1.0
 Information [    27.647]  ABI class: X.Org Video Driver, version 15.0
 Information [    27.648] (II) fglrx(0): Creating default Display subsection in Screen section
 Information  "Default Screen Section" for depth/fbbpp 24/32
 Information [    27.648] (==) fglrx(0): Depth 24, (==) framebuffer bpp 32
 Information [    27.648] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
 Information [    27.648] (==) fglrx(0): Default visual is TrueColor
 Information [    27.648] (==) fglrx(0): RGB weight 888
 Information [    27.648] (II) fglrx(0): Using 8 bits per RGB 
 Information [    27.649] (==) fglrx(0): Buffer Tiling is ON
 Information [    27.649] (II) Loading sub module "fglrxdrm"
 Information [    27.649] (II) LoadModule: "fglrxdrm"
 Information [    27.649] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
 Information [    27.649] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
 Information [    27.649]  compiled for 1.4.99.906, module version = 13.35.5
 Information [    27.653] ukiDynamicMajor: found major device number 251
 Information [    27.654] ukiDynamicMajor: found major device number 251
 Information [    27.654] ukiOpenByBusid: Searching for BusID PCI:0:1:0
 Information [    27.654] ukiOpenDevice: node name is /dev/ati/card0
 Information [    27.654] ukiOpenDevice: open result is 11, (OK)
 Information [    28.248] ukiOpenByBusid: ukiOpenMinor returns 11
 Information [    28.248] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
 Information [    28.249] (**) fglrx(0): NoAccel = NO
 Information [    28.249] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
 Information [    28.249] (--) fglrx(0): Chipset: "AMD Radeon HD 6320 Graphics" (Chipset = 0x9806)
 Information [    28.249] (--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x3387)
 Information [    28.249] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
 Information [    28.249] (--) fglrx(0): Linear framebuffer (phys) at 0x80000000
 Information [    28.249] (--) fglrx(0): MMIO registers at 0x90300000
 Information [    28.249] (--) fglrx(0): I/O port at 0x00004000
 Information [    28.249] (==) fglrx(0): ROM-BIOS at 0x000c0000
 Information [    28.250] (II) fglrx(0): ATIF platform detected
 Information [    28.324] (II) fglrx(0): Battery is used
 Information [    28.330] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
 Information [    28.331] (II) Loading sub module "vbe"
 Information [    28.331] (II) LoadModule: "vbe"
 Information [    28.332] (II) Loading /usr/lib/xorg/modules/libvbe.so
 Information [    28.332] (II) Module vbe: vendor="X.Org Foundation"
 Information [    28.332]  compiled for 1.15.1, module version = 1.1.0
 Information [    28.332]  ABI class: X.Org Video Driver, version 15.0
 Information [    28.333] (II) fglrx(0): VESA BIOS detected
 Information [    28.333] (II) fglrx(0): VESA VBE Version 3.0
 Information [    28.333] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
 Information [    28.333] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
 Information [    28.333] (II) fglrx(0): VESA VBE OEM Software Rev: 12.36
 Information [    28.333] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
 Information [    28.333] (II) fglrx(0): VESA VBE OEM Product: WRESTLER
 Information [    28.333] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
 Information [    28.333] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
 Information [    28.333] (--) fglrx(0): Video RAM: 393216 kByte, Type: DDR3
 Information [    28.333] (II) fglrx(0): PCIE card detected
 Information [    28.333] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
 Information [    28.333] (WW) fglrx(0): board is an unknown third party board, chipset is supported
 Information [    28.333] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x18000000)
 Information [    28.333] (II) fglrx(0): RandR 1.2 support is enabled!
 Information [    28.333] (II) fglrx(0): RandR 1.2 rotation support is enabled!
 Information [    28.334] (II) Loading sub module "fb"
 Information [    28.334] (II) LoadModule: "fb"
 Information [    28.334] (II) Loading /usr/lib/xorg/modules/libfb.so
 Information [    28.335] (II) Module fb: vendor="X.Org Foundation"
 Information [    28.335]  compiled for 1.15.1, module version = 1.0.0
 Information [    28.335]  ABI class: X.Org ANSI C Emulation, version 0.4
 Information [    28.335] (II) fglrx(0): EDID Management option: EDID Management is enabled
 Information [    28.335] (II) Loading sub module "ddc"
 Information [    28.335] (II) LoadModule: "ddc"
 Information [    28.335] (II) Module "ddc" already built-in
 Information [    28.431] (II) fglrx(0): Output LVDS has no monitor section
 Information [    28.431] (II) fglrx(0): Output DFP1 has no monitor section
 Information [    28.432] (II) fglrx(0): Output CRT1 has no monitor section
 Information [    28.432] (II) Loading sub module "ddc"
 Information [    28.432] (II) LoadModule: "ddc"
 Information [    28.432] (II) Module "ddc" already built-in
 Information [    28.432] (II) fglrx(0): Connected Display0: LVDS
 Information [    28.432] (II) fglrx(0): Display0 EDID data ---------------------------
 Information [    28.432] (II) fglrx(0): Manufacturer: AUO  Model: 305c  Serial#: 0
 Information [    28.432] (II) fglrx(0): Year: 2009  Week: 0
 Information [    28.432] (II) fglrx(0): EDID Version: 1.3
 Information [    28.432] (II) fglrx(0): Digital Display Input
 Information [    28.432] (II) fglrx(0): Max Image Size [cm]: horiz.: 26  vert.: 14
 Information [    28.432] (II) fglrx(0): Gamma: 2.20
 Information [    28.432] (II) fglrx(0): No DPMS capabilities specified
 Information [    28.432] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
 Information [    28.432] (II) fglrx(0): First detailed timing is preferred mode
 Information [    28.432] (II) fglrx(0): redX: 0.584 redY: 0.333   greenX: 0.338 greenY: 0.571
 Information [    28.432] (II) fglrx(0): blueX: 0.158 blueY: 0.133   whiteX: 0.313 whiteY: 0.329
 Information [    28.432] (II) fglrx(0): Manufacturer's mask: 0
 Information [    28.432] (II) fglrx(0): Supported detailed timing:
 Information [    28.432] (II) fglrx(0): clock: 69.3 MHz   Image Size:  256 x 144 mm
 Information [    28.432] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1456 h_border: 0
 Information [    28.432] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 793 v_border: 0
 Information [    28.432] (II) fglrx(0): Unknown vendor-specific block f
 Information [    28.432] (II) fglrx(0):  AUO
 Information [    28.432] (II) fglrx(0):  B116XW03 V0
 Information [    28.433] (II) fglrx(0): EDID (in hex):
 Information [    28.433] (II) fglrx(0):  00ffffffffffff0006af5c3000000000
 Information [    28.433] (II) fglrx(0):  00130103801a0e780a99859555569228
 Information [    28.433] (II) fglrx(0):  22505400000001010101010101010101
 Information [    28.433] (II) fglrx(0):  010101010101121b565a500019303020
 Information [    28.433] (II) fglrx(0):  36000090100000180000000f00000000
 Information [    28.433] (II) fglrx(0):  00000000000000000020000000fe0041
 Information [    28.433] (II) fglrx(0):  554f0a202020202020202020000000fe
 Information [    28.433] (II) fglrx(0):  004231313658573033205630200a00ec
 Information [    28.433] (II) fglrx(0): End of Display0 EDID data --------------------
 Information [    28.433] (II) fglrx(0): Dynamic Surface Resizing Enabled
 Information [    28.434] (II) fglrx(0): EDID for output LVDS
 Information [    28.434] (II) fglrx(0): Manufacturer: AUO  Model: 305c  Serial#: 0
 Information [    28.434] (II) fglrx(0): Year: 2009  Week: 0
 Information [    28.434] (II) fglrx(0): EDID Version: 1.3
 Information [    28.434] (II) fglrx(0): Digital Display Input
 Information [    28.434] (II) fglrx(0): Max Image Size [cm]: horiz.: 26  vert.: 14
 Information [    28.434] (II) fglrx(0): Gamma: 2.20
 Information [    28.434] (II) fglrx(0): No DPMS capabilities specified
 Information [    28.434] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
 Information [    28.434] (II) fglrx(0): First detailed timing is preferred mode
 Information [    28.434] (II) fglrx(0): redX: 0.584 redY: 0.333   greenX: 0.338 greenY: 0.571
 Information [    28.435] (II) fglrx(0): blueX: 0.158 blueY: 0.133   whiteX: 0.313 whiteY: 0.329
 Information [    28.435] (II) fglrx(0): Manufacturer's mask: 0
 Information [    28.435] (II) fglrx(0): Supported detailed timing:
 Information [    28.435] (II) fglrx(0): clock: 69.3 MHz   Image Size:  256 x 144 mm
 Information [    28.435] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1456 h_border: 0
 Information [    28.435] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 793 v_border: 0
 Information [    28.435] (II) fglrx(0): Unknown vendor-specific block f
 Information [    28.435] (II) fglrx(0):  AUO
 Information [    28.435] (II) fglrx(0):  B116XW03 V0
 Information [    28.435] (II) fglrx(0): EDID (in hex):
 Information [    28.435] (II) fglrx(0):  00ffffffffffff0006af5c3000000000
 Information [    28.435] (II) fglrx(0):  00130103801a0e780a99859555569228
 Information [    28.435] (II) fglrx(0):  22505400000001010101010101010101
 Information [    28.435] (II) fglrx(0):  010101010101121b565a500019303020
 Information [    28.435] (II) fglrx(0):  36000090100000180000000f00000000
 Information [    28.435] (II) fglrx(0):  00000000000000000020000000fe0041
 Information [    28.435] (II) fglrx(0):  554f0a202020202020202020000000fe
 Information [    28.435] (II) fglrx(0):  004231313658573033205630200a00ec
 Information [    28.435] (II) fglrx(0): EDID vendor "AUO", prod id 12380
 Information [    28.435] (II) fglrx(0): Printing DDC gathered Modelines:
 Information [    28.435] (II) fglrx(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
 Information [    28.435] (II) fglrx(0): Printing probed modes for output LVDS
 Information [    28.435] (II) fglrx(0): Modeline "1366x768"x60.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
 Information [    28.435] (II) fglrx(0): Modeline "1360x768"x60.0   69.30  1360 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz e)
 Information [    28.435] (II) fglrx(0): Modeline "1280x768"x60.0   69.30  1280 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz e)
 Information [    28.435] (II) fglrx(0): Modeline "1280x720"x60.0   69.30  1280 1414 1446 1456  720 771 777 793 -hsync -vsync (47.6 kHz e)
 Information [    28.435] (II) fglrx(0): Modeline "1024x768"x60.0   69.30  1024 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz e)
 Information [    28.435] (II) fglrx(0): Modeline "1024x600"x60.0   69.30  1024 1414 1446 1456  600 771 777 793 -hsync -vsync (47.6 kHz e)
 Information [    28.435] (II) fglrx(0): Modeline "800x600"x60.0   69.30  800 1414 1446 1456  600 771 777 793 -hsync -vsync (47.6 kHz e)
 Information [    28.436] (II) fglrx(0): Modeline "800x480"x60.0   69.30  800 1414 1446 1456  480 771 777 793 -hsync -vsync (47.6 kHz e)
 Information [    28.436] (II) fglrx(0): Modeline "640x480"x60.0   69.30  640 1414 1446 1456  480 771 777 793 -hsync -vsync (47.6 kHz e)
 Information [    28.436] (II) fglrx(0): EDID for output DFP1
 Information [    28.436] (II) fglrx(0): EDID for output CRT1
 Information [    28.436] (II) fglrx(0): Output LVDS connected
 Information [    28.436] (II) fglrx(0): Output DFP1 disconnected
 Information [    28.436] (II) fglrx(0): Output CRT1 disconnected
 Information [    28.436] (II) fglrx(0): Using exact sizes for initial modes
 Information [    28.436] (II) fglrx(0): Output LVDS using initial mode 1366x768
 Information [    28.436] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
 Information [    28.436] (II) fglrx(0): Display dimensions: (260, 140) mm
 Information [    28.436] (II) fglrx(0): DPI set to (133, 139)
 Information [    28.436] (II) fglrx(0): Adapter AMD Radeon HD 6320 Graphics has 2 configurable heads and 1 displays connected.
 Information [    28.436] (==) fglrx(0):  PseudoColor visuals disabled
 Information [    28.436] (II) Loading sub module "ramdac"
 Information [    28.436] (II) LoadModule: "ramdac"
 Information [    28.436] (II) Module "ramdac" already built-in
 Information [    28.436] (==) fglrx(0): NoDRI = NO
 Information [    28.437] (==) fglrx(0): Capabilities: 0x00000000
 Information [    28.437] (==) fglrx(0): CapabilitiesEx: 0x00000000
 Information [    28.437] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
 Information [    28.437] (==) fglrx(0): UseFastTLS=0
 Information [    28.437] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
 Information [    28.437] (II) UnloadModule: "radeon"
 Information [    28.437] (II) Unloading radeon
 Information [    28.437] (II) UnloadModule: "modesetting"
 Information [    28.437] (II) Unloading modesetting
 Information [    28.437] (II) UnloadModule: "fbdev"
 Information [    28.437] (II) Unloading fbdev
 Information [    28.438] (II) UnloadSubModule: "fbdevhw"
 Information [    28.438] (II) Unloading fbdevhw
 Information [    28.438] (II) UnloadModule: "vesa"
 Information [    28.438] (II) Unloading vesa
 Information [    28.438] (--) Depth 24 pixmap format is 32 bpp
 Information [    28.438] Loading extension ATIFGLRXDRI
 Information [    28.438] (II) fglrx(0): doing swlDriScreenInit
 Information [    28.438] (II) fglrx(0): swlDriScreenInit for fglrx driver
 Information [    28.438] ukiDynamicMajor: found major device number 251
 Information [    28.438] ukiDynamicMajor: found major device number 251
 Information [    28.439] ukiDynamicMajor: found major device number 251
 Information [    28.439] ukiOpenByBusid: Searching for BusID PCI:0:1:0
 Information [    28.439] ukiOpenDevice: node name is /dev/ati/card0
 Information [    28.439] ukiOpenDevice: open result is 12, (OK)
 Information [    28.439] ukiOpenByBusid: ukiOpenMinor returns 12
 Information [    28.439] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
 Information [    28.439] (II) fglrx(0): [uki] DRM interface version 1.0
 Information [    28.439] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:0:1:0"
 Information [    28.439] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
 Information [    28.439] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7fdc51b5f000
 Information [    28.439] (II) fglrx(0): [uki] framebuffer handle = 0x3000
 Information [    28.439] (II) fglrx(0): [uki] added 1 reserved context for kernel
 Information [    28.439] (II) fglrx(0): swlDriScreenInit done
 Information [    28.439] (II) fglrx(0): Kernel Module Version Information:
 Information [    28.439] (II) fglrx(0):     Name: fglrx
 Information [    28.439] (II) fglrx(0):     Version: 13.35.5
 Information [    28.439] (II) fglrx(0):     Date: Mar 12 2014
 Information [    28.439] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
 Information [    28.439] (II) fglrx(0): Kernel Module version matches driver.
 Information [    28.439] (II) fglrx(0): Kernel Module Build Time Information:
 Information [    28.439] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.13.0-24-generic
 Information [    28.439] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
 Information [    28.439] (II) fglrx(0):     Build-Kernel __SMP__:            yes
 Information [    28.439] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
 Information [    28.440] (II) fglrx(0): [uki] register handle = 0x00004000
 Information [    28.441] (II) fglrx(0): DRI initialization successfull
 Information [    28.441] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01080000
 Information [    28.442] (==) fglrx(0): Backing store enabled
 Information [    28.442] Loading extension FGLRXEXTENSION
 Information [    28.442] (==) fglrx(0): DPMS enabled
 Information [    28.443] (II) fglrx(0): Initialized in-driver Xinerama extension
 Information [    28.443] (**) fglrx(0): Textured Video is enabled.
 Information [    28.443] (II) LoadModule: "glesx"
 Information [    28.443] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
 Information [    28.444] (II) Module glesx: vendor="X.Org Foundation"
 Information [    28.444]  compiled for 1.4.99.906, module version = 1.0.0
 Information [    28.444] Loading extension GLESX
 Information [    28.444] (II) fglrx(0): GLESX enableFlags = 8784
 Information [    28.444] (II) fglrx(0): GLESX is enabled
 Information [    28.445] (II) LoadModule: "amdxmm"
 Information [    28.445] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
 Information [    28.445] (II) Module amdxmm: vendor="X.Org Foundation"
 Information [    28.445]  compiled for 1.4.99.906, module version = 2.0.0
 Information [    28.465] Loading extension AMDXVOPL
 Information [    28.465] Loading extension AMDXVBA
 Information [    28.466] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
 Information [    28.471] (II) fglrx(0): Enable composite support successfully
 Information [    28.471] (II) fglrx(0): X context handle = 0x1
 Information [    28.471] (II) fglrx(0): [DRI] installation complete
 Information [    28.472] (==) fglrx(0): Silken mouse enabled
 Information [    28.472] (==) fglrx(0): Using HW cursor of display infrastructure!
 Information [    28.473] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
 Information [    28.473] (II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
 Information [    28.473] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
 Information [    29.511] (--) RandR disabled
 Information [    29.524] (II) SELinux: Disabled on system
 Information [    29.526] ukiDynamicMajor: found major device number 251
 Information [    29.526] ukiDynamicMajor: found major device number 251
 Information [    29.526] ukiOpenByBusid: Searching for BusID PCI:0:1:0
 Information [    29.526] ukiOpenDevice: node name is /dev/ati/card0
 Information [    29.527] ukiOpenDevice: open result is 13, (OK)
 Information [    29.527] ukiOpenByBusid: ukiOpenMinor returns 13
 Information [    29.527] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
 Information [    29.527] (EE) AIGLX error: failed to open /usr/X11R6/lib64/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib64/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
 Information [    29.527] (EE) AIGLX error: failed to open /usr/lib64/dri/fglrx_dri.so, error[/usr/lib64/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
 Information [    29.527] (EE) AIGLX error: failed to open /usr/X11R6/lib/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
 Information [    29.878] ukiDynamicMajor: found major device number 251
 Information [    29.878] ukiDynamicMajor: found major device number 251
 Information [    29.878] ukiDynamicMajor: found major device number 251
 Information [    29.878] ukiOpenDevice: node name is /dev/ati/card0
 Information [    29.878] ukiOpenDevice: open result is 14, (OK)
 Information [    29.878] ukiGetBusid returned 'PCI:0:1:0'
 Information [    29.878] ukiOpenDevice: node name is /dev/ati/card1
 Information [    29.878] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.878] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.878] ukiOpenDevice: Open failed
 Information [    29.878] ukiOpenDevice: node name is /dev/ati/card2
 Information [    29.878] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.878] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.878] ukiOpenDevice: Open failed
 Information [    29.879] ukiOpenDevice: node name is /dev/ati/card3
 Information [    29.879] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.879] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.879] ukiOpenDevice: Open failed
 Information [    29.879] ukiOpenDevice: node name is /dev/ati/card4
 Information [    29.879] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.879] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.879] ukiOpenDevice: Open failed
 Information [    29.879] ukiOpenDevice: node name is /dev/ati/card5
 Information [    29.879] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.879] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.879] ukiOpenDevice: Open failed
 Information [    29.879] ukiOpenDevice: node name is /dev/ati/card6
 Information [    29.879] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.879] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.879] ukiOpenDevice: Open failed
 Information [    29.879] ukiOpenDevice: node name is /dev/ati/card7
 Information [    29.879] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.879] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.879] ukiOpenDevice: Open failed
 Information [    29.879] ukiOpenDevice: node name is /dev/ati/card8
 Information [    29.879] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.879] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.879] ukiOpenDevice: Open failed
 Information [    29.879] ukiOpenDevice: node name is /dev/ati/card9
 Information [    29.880] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.880] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.880] ukiOpenDevice: Open failed
 Information [    29.880] ukiOpenDevice: node name is /dev/ati/card10
 Information [    29.880] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.880] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.880] ukiOpenDevice: Open failed
 Information [    29.880] ukiOpenDevice: node name is /dev/ati/card11
 Information [    29.880] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.880] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.880] ukiOpenDevice: Open failed
 Information [    29.880] ukiOpenDevice: node name is /dev/ati/card12
 Information [    29.880] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.880] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.880] ukiOpenDevice: Open failed
 Information [    29.880] ukiOpenDevice: node name is /dev/ati/card13
 Information [    29.880] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.880] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.880] ukiOpenDevice: Open failed
 Information [    29.880] ukiOpenDevice: node name is /dev/ati/card14
 Information [    29.880] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.880] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.881] ukiOpenDevice: Open failed
 Information [    29.881] ukiOpenDevice: node name is /dev/ati/card15
 Information [    29.881] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.881] ukiOpenDevice: open result is -1, (No such device)
 Information [    29.881] ukiOpenDevice: Open failed
 Information [    29.881] ukiDynamicMajor: found major device number 251
 Information [    29.881] ukiOpenByBusid: Searching for BusID PCI:0:1:0
 Information [    29.881] ukiOpenDevice: node name is /dev/ati/card0
 Information [    29.881] ukiOpenDevice: open result is 14, (OK)
 Information [    29.881] ukiOpenByBusid: ukiOpenMinor returns 14
 Information [    29.881] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
 Information [    30.822] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
 Information [    30.825] ukiDynamicMajor: found major device number 251
 Information [    30.825] ukiDynamicMajor: found major device number 251
 Information [    30.825] ukiDynamicMajor: found major device number 251
 Information [    30.825] ukiOpenDevice: node name is /dev/ati/card0
 Information [    30.826] ukiOpenDevice: open result is 15, (OK)
 Information [    30.826] ukiGetBusid returned 'PCI:0:1:0'
 Information [    30.826] ukiOpenDevice: node name is /dev/ati/card1
 Information [    30.826] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.826] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.826] ukiOpenDevice: Open failed
 Information [    30.826] ukiOpenDevice: node name is /dev/ati/card2
 Information [    30.826] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.826] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.826] ukiOpenDevice: Open failed
 Information [    30.826] ukiOpenDevice: node name is /dev/ati/card3
 Information [    30.826] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.826] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.826] ukiOpenDevice: Open failed
 Information [    30.826] ukiOpenDevice: node name is /dev/ati/card4
 Information [    30.826] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.826] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.826] ukiOpenDevice: Open failed
 Information [    30.826] ukiOpenDevice: node name is /dev/ati/card5
 Information [    30.826] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.826] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.826] ukiOpenDevice: Open failed
 Information [    30.827] ukiOpenDevice: node name is /dev/ati/card6
 Information [    30.827] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.827] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.827] ukiOpenDevice: Open failed
 Information [    30.827] ukiOpenDevice: node name is /dev/ati/card7
 Information [    30.827] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.827] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.827] ukiOpenDevice: Open failed
 Information [    30.827] ukiOpenDevice: node name is /dev/ati/card8
 Information [    30.827] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.827] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.827] ukiOpenDevice: Open failed
 Information [    30.827] ukiOpenDevice: node name is /dev/ati/card9
 Information [    30.827] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.827] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.827] ukiOpenDevice: Open failed
 Information [    30.827] ukiOpenDevice: node name is /dev/ati/card10
 Information [    30.827] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.827] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.827] ukiOpenDevice: Open failed
 Information [    30.827] ukiOpenDevice: node name is /dev/ati/card11
 Information [    30.827] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.827] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.827] ukiOpenDevice: Open failed
 Information [    30.828] ukiOpenDevice: node name is /dev/ati/card12
 Information [    30.828] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.828] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.828] ukiOpenDevice: Open failed
 Information [    30.828] ukiOpenDevice: node name is /dev/ati/card13
 Information [    30.828] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.828] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.828] ukiOpenDevice: Open failed
 Information [    30.828] ukiOpenDevice: node name is /dev/ati/card14
 Information [    30.828] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.828] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.828] ukiOpenDevice: Open failed
 Information [    30.828] ukiOpenDevice: node name is /dev/ati/card15
 Information [    30.828] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.828] ukiOpenDevice: open result is -1, (No such device)
 Information [    30.828] ukiOpenDevice: Open failed
 Information [    30.828] ukiDynamicMajor: found major device number 251
 Information [    30.828] ukiOpenByBusid: Searching for BusID PCI:0:1:0
 Information [    30.828] ukiOpenDevice: node name is /dev/ati/card0
 Information [    30.828] ukiOpenDevice: open result is 15, (OK)
 Information [    30.828] ukiOpenByBusid: ukiOpenMinor returns 15
 Information [    30.829] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
 Information [    30.859] (II) fglrx(0): Setting screen physical size to 361 x 203
 Information [    30.879] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
 Information [    30.886] (II) config/udev: Adding input device Power Button (/dev/input/event2)
 Information [    30.886] (**) Power Button: Applying InputClass "evdev keyboard catchall"
 Information [    30.886] (II) LoadModule: "evdev"
 Information [    30.887] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
 Information [    30.901] (II) Module evdev: vendor="X.Org Foundation"
 Information [    30.901]  compiled for 1.15.0, module version = 2.8.2
 Information [    30.901]  Module class: X.Org XInput Driver
 Information [    30.902]  ABI class: X.Org XInput driver, version 20.0
 Information [    30.902] (II) Using input driver 'evdev' for 'Power Button'
 Information [    30.902] (**) Power Button: always reports core events
 Information [    30.902] (**) evdev: Power Button: Device: "/dev/input/event2"
 Information [    30.902] (--) evdev: Power Button: Vendor 0 Product 0x1
 Information [    30.902] (--) evdev: Power Button: Found keys
 Information [    30.902] (II) evdev: Power Button: Configuring as keyboard
 Information [    30.902] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
 Information [    30.902] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
 Information [    30.902] (**) Option "xkb_rules" "evdev"
 Information [    30.902] (**) Option "xkb_model" "pc105"
 Information [    30.902] (**) Option "xkb_layout" "us"
 Information [    30.903] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
 Information [    30.903] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
 Information [    30.903] (II) Using input driver 'evdev' for 'Video Bus'
 Information [    30.903] (**) Video Bus: always reports core events
 Information [    30.903] (**) evdev: Video Bus: Device: "/dev/input/event4"
 Information [    30.904] (--) evdev: Video Bus: Vendor 0 Product 0x6
 Information [    30.904] (--) evdev: Video Bus: Found keys
 Information [    30.904] (II) evdev: Video Bus: Configuring as keyboard
 Information [    30.904] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5/event4"
 Information [    30.904] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
 Information [    30.904] (**) Option "xkb_rules" "evdev"
 Information [    30.904] (**) Option "xkb_model" "pc105"
 Information [    30.904] (**) Option "xkb_layout" "us"
 Information [    30.905] (II) config/udev: Adding input device Power Button (/dev/input/event0)
 Information [    30.905] (**) Power Button: Applying InputClass "evdev keyboard catchall"
 Information [    30.905] (II) Using input driver 'evdev' for 'Power Button'
 Information [    30.905] (**) Power Button: always reports core events
 Information [    30.905] (**) evdev: Power Button: Device: "/dev/input/event0"
 Information [    30.905] (--) evdev: Power Button: Vendor 0 Product 0x1
 Information [    30.905] (--) evdev: Power Button: Found keys
 Information [    30.905] (II) evdev: Power Button: Configuring as keyboard
 Information [    30.905] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
 Information [    30.905] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
 Information [    30.905] (**) Option "xkb_rules" "evdev"
 Information [    30.905] (**) Option "xkb_model" "pc105"
 Information [    30.905] (**) Option "xkb_layout" "us"
 Information [    30.906] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
 Information [    30.906] (II) No input driver specified, ignoring this device.
 Information [    30.906] (II) This device may have been added with another device file.
 Information [    30.907] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event6)
 Information [    30.907] (II) No input driver specified, ignoring this device.
 Information [    30.907] (II) This device may have been added with another device file.
 Information [    30.908] (II) config/udev: Adding input device HP TrueVision HD (/dev/input/event9)
 Information [    30.908] (**) HP TrueVision HD: Applying InputClass "evdev keyboard catchall"
 Information [    30.908] (II) Using input driver 'evdev' for 'HP TrueVision HD'
 Information [    30.908] (**) HP TrueVision HD: always reports core events
 Information [    30.908] (**) evdev: HP TrueVision HD: Device: "/dev/input/event9"
 Information [    30.908] (--) evdev: HP TrueVision HD: Vendor 0x5c8 Product 0x32b
 Information [    30.908] (--) evdev: HP TrueVision HD: Found keys
 Information [    30.908] (II) evdev: HP TrueVision HD: Configuring as keyboard
 Information [    30.908] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/input/input11/event9"
 Information [    30.908] (II) XINPUT: Adding extended input device "HP TrueVision HD" (type: KEYBOARD, id 9)
 Information [    30.908] (**) Option "xkb_rules" "evdev"
 Information [    30.908] (**) Option "xkb_model" "pc105"
 Information [    30.908] (**) Option "xkb_layout" "us"
 Information [    30.909] (II) config/udev: Adding input device HDA ATI SB Mic (/dev/input/event8)
 Information [    30.909] (II) No input driver specified, ignoring this device.
 Information [    30.909] (II) This device may have been added with another device file.
 Information [    30.910] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event7)
 Information [    30.910] (II) No input driver specified, ignoring this device.
 Information [    30.910] (II) This device may have been added with another device file.
 Information [    30.911] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
 Information [    30.911] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
 Information [    30.911] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
 Information [    30.911] (**) AT Translated Set 2 keyboard: always reports core events
 Information [    30.911] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
 Information [    30.911] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
 Information [    30.911] (--) evdev: AT Translated Set 2 keyboard: Found keys
 Information [    30.911] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
 Information [    30.911] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
 Information [    30.911] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
 Information [    30.911] (**) Option "xkb_rules" "evdev"
 Information [    30.911] (**) Option "xkb_model" "pc105"
 Information [    30.911] (**) Option "xkb_layout" "us"
 Information [    30.912] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event10)
 Information [    30.912] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
 Information [    30.912] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
 Information [    30.912] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
 Information [    30.912] (II) LoadModule: "synaptics"
 Information [    30.913] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
 Information [    30.913] (II) Module synaptics: vendor="X.Org Foundation"
 Information [    30.913]  compiled for 1.15.0, module version = 1.7.4
 Information [    30.913]  Module class: X.Org XInput Driver
 Information [    30.913]  ABI class: X.Org XInput driver, version 20.0
 Information [    30.913] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
 Information [    30.913] (**) SynPS/2 Synaptics TouchPad: always reports core events
 Information [    30.913] (**) Option "Device" "/dev/input/event10"
 Information [    30.932] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
 Information [    30.932] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5776 (res 55)
 Information [    30.932] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5012 (res 103)
 Information [    30.932] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
 Information [    30.932] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
 Information [    30.932] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
 Information [    30.932] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
 Information [    30.932] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
 Information [    30.932] (**) SynPS/2 Synaptics TouchPad: always reports core events
 Information [    30.944] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input10/event10"
 Information [    30.944] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
 Information [    30.944] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
 Information [    30.944] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
 Information [    30.944] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
 Information [    30.945] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
 Information [    30.945] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
 Information [    30.945] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
 Information [    30.945] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
 Information [    30.945] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
 Information [    30.946] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
 Information [    30.946] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
 Information [    30.946] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event5)
 Information [    30.946] (II) No input driver specified, ignoring this device.
 Information [    30.946] (II) This device may have been added with another device file.
 Information [    30.947] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
 Information [    30.947] (II) No input driver specified, ignoring this device.
 Information [    30.947] (II) This device may have been added with another device file.
 Information [    30.951] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event11)
 Information [    30.951] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
 Information [    30.951] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
 Information [    30.951] (**) HP WMI hotkeys: always reports core events
 Information [    30.951] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event11"
 Information [    30.951] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
 Information [    30.951] (--) evdev: HP WMI hotkeys: Found keys
 Information [    30.951] (II) evdev: HP WMI hotkeys: Configuring as keyboard
 Information [    30.951] (**) Option "config_info" "udev:/sys/devices/virtual/input/input12/event11"
 Information [    30.952] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 12)
 Information [    30.952] (**) Option "xkb_rules" "evdev"
 Information [    30.952] (**) Option "xkb_model" "pc105"
 Information [    30.952] (**) Option "xkb_layout" "us"
 Information [    30.963] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
 Information [    54.378] (II) fglrx(0): EDID vendor "AUO", prod id 12380
 Information [    54.378] (II) fglrx(0): Printing DDC gathered Modelines:
 Information [    54.378] (II) fglrx(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
 Information [    54.666] (II) fglrx(0): EDID vendor "AUO", prod id 12380
 Information [    54.666] (II) fglrx(0): Printing DDC gathered Modelines:
 Information [    54.666] (II) fglrx(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
 Information [    56.351] (II) XKB: reuse xkmfile /var/lib/xkb/server-93D136DE4969D5C2C3EE1A2C0DAD50725F4A5BC3.xkm
 Information [    57.476] (II) fglrx(0): EDID vendor "AUO", prod id 12380
 Information [    57.476] (II) fglrx(0): Printing DDC gathered Modelines:
 Information [    57.476] (II) fglrx(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
 Information [    59.060] (II) fglrx(0): EDID vendor "AUO", prod id 12380
 Information [    59.060] (II) fglrx(0): Printing DDC gathered Modelines:
 Information [    59.061] (II) fglrx(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
 Information [    59.095] (II) fglrx(0): EDID vendor "AUO", prod id 12380
 Information [    59.096] (II) fglrx(0): Printing DDC gathered Modelines:
 Information [    59.096] (II) fglrx(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)
 Information [    62.046] ukiDynamicMajor: found major device number 251
 Information [    62.046] ukiDynamicMajor: found major device number 251
 Information [    62.047] ukiDynamicMajor: found major device number 251
 Information [    62.047] ukiOpenDevice: node name is /dev/ati/card0
 Information [    62.047] ukiOpenDevice: open result is 41, (OK)
 Information [    62.047] ukiGetBusid returned 'PCI:0:1:0'
 Information [    62.047] ukiOpenDevice: node name is /dev/ati/card1
 Information [    62.047] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.047] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.047] ukiOpenDevice: Open failed
 Information [    62.047] ukiOpenDevice: node name is /dev/ati/card2
 Information [    62.047] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.047] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.047] ukiOpenDevice: Open failed
 Information [    62.047] ukiOpenDevice: node name is /dev/ati/card3
 Information [    62.047] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.047] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.047] ukiOpenDevice: Open failed
 Information [    62.047] ukiOpenDevice: node name is /dev/ati/card4
 Information [    62.047] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.047] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.047] ukiOpenDevice: Open failed
 Information [    62.047] ukiOpenDevice: node name is /dev/ati/card5
 Information [    62.047] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.047] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.048] ukiOpenDevice: Open failed
 Information [    62.048] ukiOpenDevice: node name is /dev/ati/card6
 Information [    62.048] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.048] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.048] ukiOpenDevice: Open failed
 Information [    62.048] ukiOpenDevice: node name is /dev/ati/card7
 Information [    62.048] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.048] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.048] ukiOpenDevice: Open failed
 Information [    62.048] ukiOpenDevice: node name is /dev/ati/card8
 Information [    62.048] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.048] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.048] ukiOpenDevice: Open failed
 Information [    62.048] ukiOpenDevice: node name is /dev/ati/card9
 Information [    62.048] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.048] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.048] ukiOpenDevice: Open failed
 Information [    62.048] ukiOpenDevice: node name is /dev/ati/card10
 Information [    62.048] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.048] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.048] ukiOpenDevice: Open failed
 Information [    62.048] ukiOpenDevice: node name is /dev/ati/card11
 Information [    62.049] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.049] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.049] ukiOpenDevice: Open failed
 Information [    62.049] ukiOpenDevice: node name is /dev/ati/card12
 Information [    62.049] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.049] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.049] ukiOpenDevice: Open failed
 Information [    62.049] ukiOpenDevice: node name is /dev/ati/card13
 Information [    62.049] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.049] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.049] ukiOpenDevice: Open failed
 Information [    62.049] ukiOpenDevice: node name is /dev/ati/card14
 Information [    62.049] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.049] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.049] ukiOpenDevice: Open failed
 Information [    62.049] ukiOpenDevice: node name is /dev/ati/card15
 Information [    62.049] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.049] ukiOpenDevice: open result is -1, (No such device)
 Information [    62.049] ukiOpenDevice: Open failed
 Information [    62.049] ukiDynamicMajor: found major device number 251
 Information [    62.049] ukiOpenByBusid: Searching for BusID PCI:0:1:0
 Information [    62.049] ukiOpenDevice: node name is /dev/ati/card0
 Information [    62.050] ukiOpenDevice: open result is 41, (OK)
 Information [    62.050] ukiOpenByBusid: ukiOpenMinor returns 41
 Information [    62.050] ukiOpenByBusid: ukiGetBusid reports PCI:0:1:0
 Information [    62.178] (II) fglrx(0): EDID vendor "AUO", prod id 12380
 Information [    62.178] (II) fglrx(0): Printing DDC gathered Modelines:
 Information [    62.178] (II) fglrx(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz eP)

```



and finnaly result from acpi_listen (added keys in red):

[COLOR=#ff0000]F1= [/COLOR]^[O1P
[COLOR=#ff0000]F2=
F3=
F4=
F5= this key is emtpy
F6= [/COLOR]cd/prev CDPREV 00000080 00000000 K
[COLOR=#ff0000]F7=[/COLOR] cd/play CDPLAY 00000080 00000000 K
[COLOR=#ff0000]F8=[/COLOR] cd/next CDNEXT 00000080 00000000 K
[COLOR=#ff0000]F9=[/COLOR] button/volumedown VOLDN 00000080 00000000 K
[COLOR=#ff0000]F10=[/COLOR] button/volumeup VOLUP 00000080 00000000 K
[COLOR=#ff0000]F11=[/COLOR] button/mute MUTE 00000080 00000000 K[COLOR=#ff0000]
F12=
prt sc=[/COLOR] ^[[2~
[COLOR=#ff0000]up arrow, down arrow, left arrow, right arrow=[/COLOR] ^[[H^[[5~^[[6~^[[F
[COLOR=#ff0000]right shift=
[/COLOR]
basically Fn+F2 (reduce brightness), Fn+F3 (increase brightness), Fn+F4 (change screen), Fn+F12 (wifi- on&off) and Fn+right shift (pause) do not give any output.
again note that these worked with Xubuntu 12.04 32 bit, live session, radeon drivers.

---

### Post by wieman01 on 2014-04-22
If the FN keys don't trigger an event, then we're stuck. You probably have to use another key combination (e.g. CRTL + F2/F3) and assign it using the KDE System Settings (assuming you still use Kubuntu):

[LIST]
[*]System Settings->Shortcuts and Gestures->Global Keyboard Shortcuts
[*]Select KDE Component: KDE Daemon
[*]Look for Increase/Decrease Screen Brightness & assign desired shortcut.
[/LIST]
That should do. The FN keys won't work, but you could use CRTL as an alternative.

---

### Post by Toz on 2014-04-22
[This]("http://ubuntuforums.org/showthread.php?t=2218886") was an interesting post from a fellow poster that caught my attention a short while ago. I don't see how the two can be related, but it might be worth a try.

---

### Post by mastablasta on 2014-04-23
hmm that's an interesting solution i will give it a try. i think i could use Super key (if it even works). how is monitor switching called?

another issue (might be or is not related to) is that prt sc key works when i asign it in keyboard shortcut menu but not when actually using it (ksnapshot is not launched when pressing the key). Apparently this issue is also present in Ubuntu on older model of dm1. 

what i would like to know is if all this is a kernel bug (should be reported on launchpad) or issue with firmware that has to be troubleshot on HP forums? as is right now this all smells to be a kernel bug as it all worked in 12.04, 12.10. But less and less stuff is working as i progress to 14.04. i plan to try to another distro with new kernel. possibly nondebian based. will investigate arround a bit for options and then give one of them a try see what happens with these keys.

---

### Post by mastablasta on 2014-04-23
> **Toz said:**
> [This]("http://ubuntuforums.org/showthread.php?t=2218886") was an interesting post from a fellow poster that caught my attention a short while ago. I don't see how the two can be related, but it might be worth a try.


oh just saw this after previous post. i need to give this a try first. are there any drawback when using IDE?

and i wonder if it will crash the windows 7 starter on the other partition: [http://www.sevenforums.com/installation-setup/29089-change-ide-ahci-bios-much-better-performance.html](http://www.sevenforums.com/installation-setup/29089-change-ide-ahci-bios-much-better-performance.html)

---

### Post by mastablasta on 2014-04-23
update: ive assigned metaF2, F3 and F4 to their functions - it works. nice smooth workarround. i can turn off wi-fi via network manager os thta is not such a biggy.

however what would be workarround for pause key and also i found out that prt sc key does not work. i mean it works is detected when i set it in shortcuts but does not launch ksnapshot as instructed. ksnapshot works well if launched manually.

---

### Post by wieman01 on 2014-04-23
> **mastablasta said:**
> update: ive assigned metaF2, F3 and F4 to their functions - it works. nice smooth workarround. i can turn off wi-fi via network manager os thta is not such a biggy.

however what would be workarround for pause key and also i found out that prt sc key does not work. i mean it works is detected when i set it in shortcuts but does not launch ksnapshot as instructed. ksnapshot works well if launched manually.
Sorry, I am at a loss here. The shortcuts in KDE work well in many cases, so you could play around with it a little and see if you get these keys to work. I think we sort of pointed you in the right direction. :-)

---

### Post by mastablasta on 2014-08-04
funny thing I just found out the "prt sc" key does not work in kubuntu (is ignored), but If I launch a program in wine it works in that program. it is recognised in wine but not in Linux.

---

