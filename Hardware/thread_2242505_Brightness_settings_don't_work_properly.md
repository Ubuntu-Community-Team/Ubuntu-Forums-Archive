---
title: "Brightness settings don't work properly"
date: 2014-09-02
forum: Hardware
---

### Post by cyberpunk3 on 2014-09-02
On my Asus EEE 1001PXD netbook, I can't make brightness changes to work. It looks as though the system picks up whatever brightness is set when I turn on the computer, and keeps it throughout the session.

If I use Fn plus F5 or F6, the slider is displayed on the screen, but the brightness doesn't change. The same is with the slider in System Settings / Brightness & Lock.

I already tried adding acpi_osi=Linux acpi_backlight=vendor to grub setting GRUB_CMDLINE_LINUX_DEFAULT, as advised in other sources, but it doesn't change anything.

---

### Post by Toz on 2014-09-02
Lets have a closer look at some of your system settings. Open a terminal window, type in the following commands, and post back the results within **[noparse]```
 
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

---

### Post by cyberpunk3 on 2014-09-03
Update... I forgot to run "update-grub" before. Adding acpi_osi=Linux and acpi_backlight=vendor to grub setting GRUB_CMDLINE_LINUX_DEFAULT does change things. Now the slider in "Brightness & Lock" works. The F5 and F6 keys, on the other hand, don't (pressing either of them just resets brightness to full).

Do I still have to paste all the info from above, or something else now?

---

### Post by Toz on 2014-09-03
Yes please. Post the results of those commands and lets see what they say.

---

### Post by cyberpunk3 on 2014-09-06
Here is all the data you asked for:

1. Current kernel boot line:
```
BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=0f09e446-2aab-4a56-92fd-71ff87f0ba0a ro acpi_osi=Linux acpi_backlight=vendor

```
2. Information about video card:
```
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
    Subsystem: ASUSTeK Computer Inc. Device 83ac
    Kernel driver in use: i915 

```
3. Information about known backlight interfaces:
```
 /sys/class/backlight/eeepc
0
15
2816

 /sys/class/backlight/intel_backlight
11484
11484
11484  

```
4. A listing of loaded kernel modules:
```
Module                  Size  Used by
ctr                    13049  2 
ccm                    17773  2 
dm_crypt               23177  0 
asus_wmi               24191  0 
snd_hda_codec_realtek    65580  1 
snd_hda_intel          56451  3 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
coretemp               13435  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
arc4                   12608  2 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
rtl8192se              63196  0 
rtl_pci                26690  1 rtl8192se
videodev              134688  2 uvcvideo,videobuf2_core
rtlwifi                63475  2 rtl_pci,rtl8192se
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
joydev                 17381  0 
serio_raw              13462  0 
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192se
bnep                   19624  2 
rfcomm                 69160  0 
snd                    69322  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
bluetooth             391136  10 bnep,rfcomm
lpc_ich                21080  0 
cfg80211              484040  2 mac80211,rtlwifi
soundcore              12680  1 snd
eeepc_laptop           19867  0 
sparse_keymap          13948  2 eeepc_laptop,asus_wmi
parport_pc             32701  0 
ppdev                  17671  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
i915                  783805  4 
i2c_algo_bit           13413  1 i915
drm_kms_helper         53081  1 i915
psmouse               106678  0 
ahci                   25819  2 
libahci                32716  1 ahci
drm                   303102  5 i915,drm_kms_helper
atl1c                  46086  0 
video                  19476  2 i915,asus_wmi
wmi                    19177  1 asus_wmi 

```
5. /var/log/Xorg.0.log file:
Pasted at [http://pastebin.com/P6fWfJHp](http://pastebin.com/P6fWfJHp)

---

### Post by Toz on 2014-09-06
Your system identifies 2 backlight interfaces:
[LIST=1]
[*]/sys/class/backlight/intel_backlight - as provided by the intel driver and the current set of kernel parameters
[*]/sys/class/backlight/eeepc - as provided by the eeepc-wmi kernel module
[*]
[/LIST]
Most probably, there is confusion within the system as to which interface to use when pressing the function keys.

One way to force the system to use the intel_backlight interface is to create a **/usr/share/X11/xorg.conf.d/20-intel.conf** file with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"    "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
...then log out and back in again to test.

---

### Post by cyberpunk3 on 2014-09-07
I tried this. Now either of the Fn + f5/f6 keys combinations will only lower the brightness. If I go to System Settings, I can still adjust it in both directions. There's one difference, though: The screen can be dimmed completely (which is what I did at first, so I have to force shutdown it), either with the (both) keys, or the system settings slider.

---

### Post by Toz on 2014-09-07
Can you try the following kernel parameter _in place_ of "acpi_osi=Linux acpi_backlight=vendor"?
```
video.use_native_backlight=1
```

After you've rebooted, post back the same results again from my post #2 and try the function keys and slider again.

---

### Post by cyberpunk3 on 2014-09-08
Well, both sliders work now. Thanks!

I suppose the difference between the two backlight interfaces is also that the eeepc one has a "safety" minimum backlight (so you don't dim yourself out...), whereas with intel-backlight you can completely dim the screen.

---

