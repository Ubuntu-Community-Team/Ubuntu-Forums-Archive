---
title: "Brightness control not working for Toshiba Satellite C75D-A"
date: 2014-04-11
forum: Hardware
---

### Post by raisen on 2014-04-11
The brightness control functions aren't working (I can't turn the brightness up and down) for a Toshiba Satellite C75D-A under Ubuntu 13.10, any ideas?

---

### Post by Toz on 2014-04-11
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

### Post by raisen on 2014-04-11
1.
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-18-generic.efi.signed root=UUID=1a921958-a6f8-4d11-a007-4a96e9e3c055 ro quiet splash acpi_backlight=vendor vt.handoff=7
```

2.
```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8400]
    Subsystem: Toshiba America Info Systems Device fa85
    Kernel driver in use: fglrx_pci



```

3.
```
 /sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory

```
4.
```
Module                  Size  Used by
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19704  2 
rfcomm                 69130  0 
bluetooth             372041  10 bnep,rfcomm
nls_iso8859_1          12713  1 
joydev                 17377  0 
amd_freq_sensitivity    12589  0 
kvm_amd                59987  0 
kvm                   431754  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  3 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
snd_hda_codec_conexant    57441  1 
snd_hda_codec_hdmi     41154  1 
snd_hda_intel          52267  7 
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
arc4                   12608  2 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
microcode              23656  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
rtl8188ee              89658  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
rtl_pci                26641  1 rtl8188ee
rtlwifi                63229  2 rtl_pci,rtl8188ee
psmouse                97655  0 
serio_raw              13413  0 
mac80211              597268  3 rtl_pci,rtlwifi,rtl8188ee
fam15h_power           13119  0 
fglrx                6732964  369 
snd                    69141  24 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
k10temp                13126  0 
i2c_piix4              22106  0 
edac_core              62342  0 
edac_mce_amd           22617  0 
cfg80211              480503  2 mac80211,rtlwifi
amd_iommu_v2           19054  1 fglrx
soundcore              12680  1 snd
toshiba_acpi           22901  0 
sparse_keymap          13948  1 toshiba_acpi
wmi                    19070  1 toshiba_acpi
video                  19318  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101762  2 hid_generic,usbhid
ahci                   25819  4 
alx                    32452  0 
libahci                32009  1 ahci
mdio                   13807  1 alx

```


5.
[http://paste.ubuntu.com/7237755/](http://paste.ubuntu.com/7237755/)

---

### Post by raisen on 2014-04-11
Something else I found out is that none of the FN keys work, ie: volume control, wifi toggle, etc.

---

### Post by Toz on 2014-04-12
> [QUOTE]/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory[/QUOTE]
Your system is not exposing any backlight interfaces, hence the reason why the backlight controls don't work. 

I'd be interested in seeing the results of the same commands above under the following conditions:

1. Remove the    **acpi_backlight=vendor**    kernel parameter.
2. Try the    **acpi_osi=**    kernel parameter
3. Try the    **acpi_osi='!Windows 2012'**    kernel parameter.

In all instances, don't forget to run "sudo update-grub" before rebooting, post back the results of the above commands, and try your function keys.

---

### Post by raisen on 2014-04-12
acpi_osi=kernel
```
/sys/class/backlight/acpi_video0
100
100
100

```

acpi_osi='!Windows 2012'
 ```
/sys/class/backlight/acpi_video0
0
7
0


 /sys/class/backlight/toshiba
0
7
0



```

With the second option, whenever I tried to increase the screen brightness, the computer went into hibernate mode and was unable to restore from it. I had to hold the power button down.

---

### Post by Toz on 2014-04-12
Sorry, but it was a little confusing. The fist one should be just:

**acpi_osi=**

...(no kernel).

With this option, if there is only one backlight interface, does backlight control work?

---

### Post by raisen on 2014-04-12
With that option, **acpi_osi=  **I was unable to boot Ubuntu. I got the grub menu, pressed enter, the purple screen came on and just stayed there. The computer became unresponsive and I had to hold the power button to turn it off. I changed back to **acpi_osi=[COLOR=#000000]'!Windows 2012'[/COLOR]**  and was able to boot Ubuntu.

I noticed that with  **acpi_osi=[COLOR=#000000]'!Windows 2012' [/COLOR]**[COLOR=#000000], I'm able to control the volume using Fn+F9 and Fn+F10 which is correct, but Fn+F3 (which is supposed to increase the brightness) hibernates the machine, and Fn+F2 (decrease the brightness) does nothing.[/COLOR]**[COLOR=#000000][/COLOR]**

---

### Post by Toz on 2014-04-12
Try this combination: **acpi_osi='!Windows 2012' acpi_backlight=vendor**

Once booted with these paramters, post back:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
...and try the function keys.

---

### Post by raisen on 2014-04-12
I tried that and the same behavior happened as before: brightness function key is hibernating the computer. That's the output for that command:

 ```
/sys/class/backlight/toshiba
0
7
0
```


Also, I'm not sure if it's related, but every time the Ubuntu window manager starts, I get a bunch of errors that I have to close them down - about 8. Is there a log file that shows what those errors are about?

---

### Post by Toz on 2014-04-12
> **raisen said:**
> I tried that and the same behavior happened as before: brightness function key is hibernating the computer. That's the output for that command:

 ```
/sys/class/backlight/toshiba
0
7
0
```
Does brightness work if you use the brightness slider? And do either of these commands adjust brightness?
```
echo 4 | sudo tee /sys/class/backlight/toshiba/brightness
echo 7 | sudo tee /sys/class/backlight/toshiba/brightness
```


> Also, I'm not sure if it's related, but every time the Ubuntu window manager starts, I get a bunch of errors that I have to close them down - about 8. Is there a log file that shows what those errors are about?
In all likelihood, its because you had to manually poweroff your computer when it wouldn't boot properly. The log files should be located in /var/crash.

---

### Post by raisen on 2014-04-12
> **Toz said:**
> Does brightness work if you use the brightness slider? And do either of these commands adjust brightness?
```
echo 4 | sudo tee /sys/class/backlight/toshiba/brightness
echo 7 | sudo tee /sys/class/backlight/toshiba/brightness
```
.

No, I tried them all and didn't work. Brightness stays at the highest level all the time.

I checked the content of that brightness file and stays at 0.

---

### Post by Toz on 2014-04-12
Can you try **acpi_osi=kernel** again? What's strange about this one is that it really isn't an option, but it yielded interesting results for you. Try it again and post back:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
...as well as try:
```
echo 50 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 75 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
...as well as try the brightness slider and function keys.

---

