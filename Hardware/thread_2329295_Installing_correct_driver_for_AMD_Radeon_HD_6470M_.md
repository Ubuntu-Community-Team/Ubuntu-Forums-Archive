---
title: "Installing correct driver for AMD Radeon HD 6470M on Ubuntu 16.04LTS"
date: 2016-06-29
forum: Hardware
---

### Post by KageRyu on 2016-06-29
Hello guys new linux user here after 3 days of arduouse struggle trying to get my laptop to boot i finally booted it in recovery mode . I have linux 16.04 installed i want to be able to use my computer without having to start recovery mode. my gfx card is AMD Radeon HD 6470M and i know it isn't 16.04 compatible but i heard there were some open source amd drivers which driver should i install? 
I was perusing this website **([https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver))**  but it is too complicated for me to make out anything i was able to run the 
lspci -nn | grep VGA command here is the **result**.**[http://imgur.com/Xlmmz2x](http://imgur.com/Xlmmz2x)**

when i look at the additional driver app in linux it shows this ((**[http://imgur.com/ey8JrtK](http://imgur.com/ey8JrtK)**)*the resolution is bad due to recovery mode i think*) but whenever i press apply it contiues to show it and it never goes away.

thats all i think i can share 

SPECS: 
[B]Edge E425 (ThinkPad)
[/B]
Machine info
E2-3000M(1.8Ghz),  2GB RAM(4gb ram i added myself) so 6gb, 320GB 5400rpm  HD, 14in 1366x768 LCD, AMD Radeon HD 6470M,  CDRW/DVDRW, 802.11bgn  wireless, 1Gb Ethernet, UltraNav, Camera, 6c  Li-Ion

Operating System
NONE CURRENTLY(but came with
Windows 7 (64-bit))

this laptop I just formatted and decided to install Ubuntu.
ubuntu-16.04-desktop-amd64.iso



[SIZE=2](this thread is continuation from my previous thread where iwas trying to boot ubuntu)[/SIZE]
[http://ubuntuforums.org/showthread.php?t=2329130](http://ubuntuforums.org/showthread.php?t=2329130)

---

### Post by QIII on 2016-06-29
Hello!

The installer will decide at install time what the best driver is and install that for you.  For 16.04, that will be either the AMDGPU driver (if your hardware is supported) or the Radeon driver.

There is nothing further for you to install.

---

### Post by KageRyu on 2016-06-29
Hello the installer did not download the correct files because i could not boot ubuntu at all normally i have to boot through recovery mode . 2.  i am limited to a very low resolution .
AMDGPU driver (if your hardware is supported) or the Radeon driver. which of these should i download and how to download them (i am a very unexperienced ubuntu user. thank you for your time

---

### Post by QIII on 2016-06-29
The installer did download and install the driver.  It is part of the kernel.  There is likely a setting to fix.  On my cell right now, so hopefully someone will jump in.

---

### Post by oldfred on 2016-06-29
From terminal:
 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices 


 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
xrandr -q
xrandr --q1
#What is installed
dkms status

---

### Post by KageRyu on 2016-06-29
@ QIII well My beginning question and problems still persist , looking forward to any solutions thank you

@OldFred: I'm sorry but i  really don't understand how that solves the question of  **"AMDGPU driver (if your hardware is supported) or the Radeon driver"** which of these should i download and how do i download and install them?

---

### Post by QIII on 2016-06-29
Again:  Unless there is something very wrong, you do not need to download or install anything.  Normally, both Radeon and AMDGPU are present in the source code and one or the other is inserted into the kernel at install time depending on the hardware.

My guess at this point is that this is a laptop with hybrid Intel/AMD graphics (the "M" in the model designation is for mobile) -- and that is causing the problem.  A lot of work has been done to make these systems work, but depending on the age of the laptop there still may be issues.  Or, it may be that the whole Radeon/AMDGPU choice is muddled in hybrid systems.

Edit:  I had a moment to look up the machine and it is not one with hybrid graphics.

---

### Post by KageRyu on 2016-06-29
so i tried kubuntu 16.  ubuntu 16.  and 14 and not one of them was able to even " try" or install due to it getting stuck at splash screen. i was only able to boot my usb bootloader ubuntu 16 with the nomode set option afterward i had atrocious resolution. then it took me another two days trying to boot the ubuntu i installed without the crash at the splash screen, and i was only able to use it in recovery mode . what do you think is the problem then  is there any information that you need regarding my system or do you have any solutions?
 

EDIT:more detailed machine info:
SPECS: 
**Edge E425 (ThinkPad)**
[IMG]http://support.lenovo.com/%7E/media//Images/ProdImageLaptops/thinkpad_edge_e425[/IMG]
Serial Number
R9LXFBA
Machine type model
1198A19

Machine info
E2-3000M(1.8Ghz),  2GB RAM(4gb ram i added myself) so 6gb, 320GB 5400rpm  HD, 14in 1366x768 LCD, AMD Radeon HD 6470M,  CDRW/DVDRW, 802.11bgn  wireless, 1Gb Ethernet, UltraNav, Camera, 6c  Li-Ion

---

### Post by Bucky Ball on 2016-06-30
Seeing as you have this:

AMD Radeon HD 6470M

I guess it's the Radeon driver. You'll find it in the repositories. You may also find that it is already installed.

---

### Post by kurt18947 on 2016-06-30
I would think the command "lsmod" from a terminal would tell you if there is a video driver loaded. You should see some reference to Radeon (what I see on a machine with 4200HD graphics), I'm not sure what you'd see if AMDGPU were loaded. Another place to look would be 'additional drivers'. If there's a proprietary driver available it should be listed there.

This is one of the differences between Windows and Linux. The recommended fix for almost any Windows hardware problem is "download the latest driver". That solution is seldom appropriate for Linux where hardware drivers are usually included.

---

### Post by KageRyu on 2016-06-30
heres how my desktop looks like(still in recovery mode guys )   

[http://imgur.com/a/2Y62g](http://imgur.com/a/2Y62g)
2nd image shows my additional drivers screen. there is a driver there but it says its not working and whenever i press apply to download it it either freezes or straight out does nothing.


@BuckyBall: Hi thanks where do i find these "repositories and which version should i download for my graphics card thank you.


@Kurt: HI i did lsmod and here is the result

```
ryu@KageFang:~$ lsmod
Module                  Size  Used by
ctr                    16384  1
ccm                    20480  1
nls_iso8859_1          16384  1
arc4                   16384  2
uvcvideo               90112  0
rtl8192ce              57344  0
videobuf2_vmalloc      16384  1 uvcvideo
rtl_pci                28672  1 rtl8192ce
videobuf2_memops       16384  1 videobuf2_vmalloc
rtl8192c_common        53248  1 rtl8192ce
videobuf2_v4l2         28672  1 uvcvideo
kvm                   536576  0
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
rtlwifi                77824  3 rtl_pci,rtl8192c_common,rtl8192ce
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
mac80211              737280  3 rtl_pci,rtlwifi,rtl8192ce
irqbypass              16384  1 kvm
media                  24576  2 uvcvideo,videodev
joydev                 20480  0
input_leds             16384  0
serio_raw              16384  0
snd_hda_codec_hdmi     53248  1
cfg80211              565248  2 mac80211,rtlwifi
snd_hda_codec_conexant    24576  1
snd_hda_codec_generic    77824  1 snd_hda_codec_conexant
snd_hda_intel          36864  5
snd_seq_midi           16384  0
snd_hda_codec         135168  4 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_hda_core           73728  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
k10temp                16384  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_hwdep              16384  1 snd_hda_codec
thinkpad_acpi          86016  1
nvram                  16384  1 thinkpad_acpi
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
i2c_piix4              24576  0
shpchp                 36864  0
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  22 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
soundcore              16384  1 snd
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
drbg                   32768  1
ansi_cprng             16384  0
xts                    16384  1
gf128mul               16384  1 xts
algif_skcipher         20480  0
af_alg                 16384  1 algif_skcipher
dm_crypt               28672  1
uas                    24576  0
usb_storage            69632  1 uas
psmouse               126976  0
sdhci_pci              28672  0
i2c_algo_bit           16384  0
sdhci                  45056  1 sdhci_pci
ttm                    98304  0
drm_kms_helper        139264  0
r8169                  81920  0
mii                    16384  1 r8169
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
ahci                   36864  3
sysimgblt              16384  1 drm_kms_helper
libahci                32768  1 ahci
fb_sys_fops            16384  1 drm_kms_helper
drm                   360448  2 ttm,drm_kms_helper
fjes                   28672  0
video                  40960  1 thinkpad_acpi
```

quick update i was able to install the unknown driver in the additional drivers app and after restart it again got stuck so had to use recovery mode again but this time when i opened addition drivers i saw this . [http://imgur.com/zTDTOtp](http://imgur.com/zTDTOtp)

---

### Post by kurt18947 on 2016-06-30
This is probably a case of the blind leading the blind but I wonder what function uvcvideo has on your system? A quick google seems to indicate that it's primarily intended as an input driver such as from a web cam rather than a display driver. Would it be causing things to 'get crossways' somehow? For lack of a better idea I'd probably blacklist it in /etc/modprobe.d/blacklist.conf and reboot just to see if it makes any difference. It probably won't but you don't know 'til you try. I don't see any indication of an ATI/AMD driver of any sort.

---

### Post by KageRyu on 2016-06-30
Hi Kurt i can try to blacklist it . but you said that there is no indication of an ati or amd driver. how am i supposed to find the correct driver and install it.
and the blacklisting procedure are you sure it wont brick my installation?

Edit:  tried the command no success : [http://imgur.com/8letqar](http://imgur.com/8letqar)

---

### Post by oldfred on 2016-06-30
Did you ever run commands in post #5 that show resolution and current driver?

---

### Post by deadflowr on 2016-06-30
uvcvideo is normally related to a camera or any capture device., nothing to do with a display.

Anyway, the problem at hand might have to do with the fact that you have two AMD cards, and I do not know how well the radeon driver handles that.

But that's just my rambling thought on it.

---

### Post by KageRyu on 2016-06-30
@ OldFred Hi when you posted that previously i had asked what those codes were but after some fiddling figured them out. here are the answers to every single code you put there :

edit: this is how i was able to boot ubuntu [http://m.imgur.com/jHgHR83](http://m.imgur.com/jHgHR83)


CODE:

```
ryu@KageFang:~$ ubuntu-drivers devices 
== cpu-microcode.py ==
driver   : amd64-microcode - distro non-free
```

```
ryu@KageFang:~$ sudo lshw -c display
[sudo] password for ryu: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Sumo [Radeon HD 6380G]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff ioport:5000(size=256) memory:f0c00000-f0c3ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Seymour [Radeon HD 6400M/7400M Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff memory:f0b00000-f0b1ffff ioport:4000(size=256) memory:f0b20000-f0b3ffff
```
```
ryu@KageFang:~$ sudo lshw | grep -A 11 display
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Sumo [Radeon HD 6380G]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:d0000000-dfffffff ioport:5000(size=256) memory:f0c00000-f0c3ffff
--
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Seymour [Radeon HD 6400M/7400M Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller cap_list
                configuration: latency=0
                resources: memory:e0000000-efffffff memory:f0b00000-f0b1ffff ioport:4000(size=256) memory:f0b20000-f0b3ffff
```
```
ryu@KageFang:~$ lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Sumo [Radeon HD 6380G]
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series]
```
```
ryu@KageFang:~$ xwininfo -root

xwininfo: Window id: 0x25d (the root window) (has no name)

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 640
  Height: 480
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 640x480+0+0
```

```
ryu@KageFang:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected primary 640x480+0+0 0mm x 0mm
   640x480       73.00* 
ryu@KageFang:~$ xrandr --q1
 SZ:    Pixels          Physical       Refresh
*0    640 x 480    ( 169mm x 127mm )  *73  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none
ryu@KageFang:~$ dkms status 
The program 'dkms' is currently not installed. You can install it by typing:
sudo apt install dkms
```

---

### Post by oldfred on 2016-06-30
Install dkms just to see what is installed and rerun command.

But I think deadflower is correct. You have two similar AMD video drivers and that confuses things. Ca you set one on or off in BIOS?

---

### Post by QIII on 2016-06-30
Yes.  AMD calls this a "dual GPU" arrangement rather than the hybrid Intel/AMD system.

If you were able to run fglrx (which you can't with 16.04), you would be able to initialize both GPUs.  Here, I suspect oldfred is right: disable one or the other in BIOS.  You'll likely have to insert the Radeon module manually, but we can help you with that after you tell us you can disable one of the GPUs.

---

### Post by KageRyu on 2016-06-30
after from BIOS- Settings-Display-  I changed switchable graphics to integrated graphics here and ubuntu booted normally without any problems after a week of effort its finally over Thank you everyone for your support.


@OldFred    i installed dkms but i couldnt run it .

**```
**ryu@KageFang:~$ sudo apt-get install dkms
[sudo] password for ryu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 67,4 kB of archives.
After this operation, 270 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 dkms all 2.2.0.3-2ubuntu11 [67,4 kB]
Fetched 67,4 kB in 0s (110 kB/s)
Preconfiguring packages ...
Selecting previously unselected package dkms.
(Reading database ... 208023 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-2ubuntu11_all.deb ...
Unpacking dkms (2.2.0.3-2ubuntu11) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up dkms (2.2.0.3-2ubuntu11) ...
ryu@KageFang:~$ dkms status
ryu@KageFang:~$ dkms status
ryu@KageFang:~$ run dkms
No command 'run' found, did you mean:**
```**




Thanks everyone . mods you may mark as solved (if oyu kindly show me how to put the code tags on code and how to mark my post as solved i wont bother you with that anymore.

---

### Post by oldfred on 2016-06-30
That is now working is what is important.

That dkms status returns nothing is that you have no proprietary drivers installed.

---

### Post by Bucky Ball on 2016-06-30
> **KageRyu said:**
> mods you may mark as solved (if oyu kindly show me how to put the code tags on code and how to mark my post as solved i wont bother you with that anymore.

Thread Tools at top right to mark as solved. You can also see the blue second link in my signature at bottom of this post.

There is also a green link for how to use code tags in my signature. Thanks.

Bother us as much as you like (within reason!). Good luck.

---

### Post by KageRyu on 2016-07-02
done and done thanks !

---

