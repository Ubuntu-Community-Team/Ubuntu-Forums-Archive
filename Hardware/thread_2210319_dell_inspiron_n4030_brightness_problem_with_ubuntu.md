---
title: "dell inspiron n4030 brightness problem with ubuntu 13.10"
date: 2014-03-10
forum: Hardware
---

### Post by amith3 on 2014-03-10
when i press keys to increse or dectease brightness. ubuntu freezes and only option is power off.how can i solve this

---

### Post by Toz on 2014-03-10
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

### Post by amith3 on 2014-03-10
kernal bootline
```

BOOT_IMAGE=/boot/vmlinuz-3.11.0-18-generic root=UUID=91bf7537-d5df-4c61-ae86-d2ef73ac66a3 ro quiet splash vt.handoff=7

```
VIDEO CARD
```

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
    Subsystem: Dell Device 0466
    Kernel driver in use: i915


```
BACKLIGHT
```


 /sys/class/backlight/acpi_video0
15
15
15

 /sys/class/backlight/intel_backlight
1531
4882
488

```
KERNEL MODULES
```

Module                  Size  Used by
rndis_host             14087  0 
cdc_ether              13967  1 rndis_host
usbnet                 37607  2 rndis_host,cdc_ether
mii                    13654  1 usbnet
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18959  2 
rfcomm                 53664  0 
joydev                 17097  0 
binfmt_misc            13140  1 
intel_powerclamp       14239  0 
coretemp               13195  0 
snd_hda_codec_idt      44605  1 
kvm_intel             128218  0 
kvm                   368975  1 kvm_intel
arc4                   12536  2 
brcmsmac              529716  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
b43                   356429  0 
mac80211              517444  2 b43,brcmsmac
btusb                  23443  0 
bluetooth             323656  11 bnep,btusb,rfcomm
cfg80211              401762  3 b43,brcmsmac,mac80211
ssb                    51596  1 b43
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
dell_laptop            17161  0 
dcdbas                 14383  1 dell_laptop
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
videodev              107508  2 uvcvideo,videobuf2_core
snd_hda_intel          42658  3 
snd_hda_codec         164003  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
microcode              18894  0 
psmouse                90642  0 
i915                  594442  8 
serio_raw              13189  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
intel_ips              18055  0 
lpc_ich                16864  0 
drm_kms_helper         46867  1 i915
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
drm                   242400  4 i915,drm_kms_helper
snd_timer              24447  2 snd_pcm,snd_seq
mei_me                 13933  0 
bcma                   40966  3 b43,brcmsmac
snd                    60790  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei                    66411  1 mei_me
i2c_algo_bit           13197  1 i915
soundcore              12600  1 snd
wmi                    18590  1 dell_wmi
video                  18777  1 i915
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
ums_realtek            17733  0 
usb_storage            48294  1 ums_realtek
ahci                   25579  1 
atl1c                  40949  0 
libahci                26619  1 ahci


```
LOG FILE
[http://paste.ubuntu.com/7068547/](http://paste.ubuntu.com/7068547/)

---

### Post by Toz on 2014-03-10
First, try creating the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content (you need root privileges to do so, try "sudo -i gedit /usr/share/X11/xorg.conf.d/20-intel.conf"):
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
Log out and in again to test.

If that doesn't work, then try following the "Temporarily Add a Kernel Boot Parameter for Testing" instructions from the [Kernel Boot Parameters]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") wiki to test the **acpi_backlight=vendor** kernel parameter.

---

### Post by amith3 on 2014-03-11
I tried creating the config file. but after reboot, i can only see a black screen. now i deleted the file i created and things are back as usual. how do i test the acpi backlight? i didn't fully understand what to do from the link you gave.

---

### Post by Toz on 2014-03-11
> **amith3 said:**
> I tried creating the config file. but after reboot, i can only see a black screen.
Did you try adjusting your brightness keys? Perhaps the brightness was at its lowest value.
> how do i test the acpi backlight? i didn't fully understand what to do from the link you gave.
Try re-reading the instructions. I don't think I can make it any clearer than what is already there. It offers you the opportunity to test the parameter for one boot only. If it fails, simply reboot to get your system back to its original state.

---

### Post by amith3 on 2014-03-11
i did try incresing the brightness. it didn't help. i use a dual boot system. if i change things in grub will it affect windows?

---

### Post by amith3 on 2014-03-11
i changed in grub like this
linux /boot/....... ro quiet splas\h $vt_handoff acpi_backlight=vendor
when i pressed ctrl x , a black screen appeared. i tried to increase brightness but screen was still black.
what to do next?

---

### Post by Toz on 2014-03-11
Boot back to a working system. Which of the following commands change brightness:
```
echo 2441 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...or...
```
echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

----------------------

Then, try enabling the **/usr/share/X11/xorg.conf.d/20-intel.conf** file from post #4 again, but this time, also add the following commands to **/etc/rc.local** (_above_ the *exit 0*) command:
```
echo 0 > /sys/class/backlight/intel_backlight/brightness
echo 4882 > /sys/class/backlight/intel_backlight/brightness
*exit 0   #this should already be in the file*
```
...then reboot and see.

---

### Post by Ed_Childers on 2014-08-04
Toz, Thanks, 20-intel-conf fixed my problem with a Dell Inspiron 15 5000 series 5547, Ubuntu 14.04. I could not adjust brightness. Now I can.

---

