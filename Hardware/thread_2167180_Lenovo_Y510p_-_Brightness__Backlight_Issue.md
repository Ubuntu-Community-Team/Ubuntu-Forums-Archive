---
title: "Lenovo Y510p - Brightness / Backlight Issue"
date: 2013-08-12
forum: Hardware
---

### Post by mr-gary-waters on 2013-08-12
After much fun with Windows 8 / UEFI, I finally have a dual boot for my Y510p.
It has 2 nvidia 750M gpu's in SLI mode, and I am running Ubuntu 13.04 with nvidia's drivers. 

Everything so far seems to work that I care about except brightness controls.  

I did everything here:
[http://forum.notebookreview.com/ideapad-essential/716609-tutorial-lenovo-y500-ubuntu-linux-brightness-key-fix.html](http://forum.notebookreview.com/ideapad-essential/716609-tutorial-lenovo-y500-ubuntu-linux-brightness-key-fix.html)

Downloaded nvidiabl source code.
changed nvidia-laptop.h and nvidia-gpu.h for my machine, and recompiled it and installed with and without dkms. (I am the guy on the bottom of the page in the link above).
The module loads fine and the vaules in the brightness variable in /sys/class/XXXX change, but the ACTUAL brightness of the laptop doesnt change.

The only thing that does seem to work is xbacklight, but unfortunately I can not use it in the scripts.  I think it needs to be run from X for it to work.

Does anyone know how to make nvidiabl work or how make xbacklight work from acpi's scripts?

Thanks,
G

PS - I also tried the weird acpi_osi options of " 'space' " "Linux" "!Windows2012" and acpi_backlight="vendor", no luck, it just changes what shows up in /sys/class/backlight

---

### Post by Toz on 2013-08-12
Hello and welcome to the forums.

Can you post back some more information?

1. Your current kernel command line:
```
cat /proc/cmdline
```

2. Your backlight interfaces and some of their settings:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

3. The currently running modules:
```
lsmod
```

4. You acpi brightness key codes. To do this, in a terminal, run:
```
acpi_listen
```
...then press the function+brightness+up key combination and note the codes that display in the terminal window. Do the same for function+brightness_down. Post back the results.

---

### Post by mr-gary-waters on 2013-08-13
Most definitely!

Thanks for help Toz, here you go:

-G

> **Toz said:**
> 
1. Your current kernel command line:
```
cat /proc/cmdline
```

```
 
BOOT_IMAGE=/boot/vmlinuz-3.8.0-27-generic root=UUID=b20e2a92-8826-4a04-97b6-5836cd1f824e ro nomodeset=1

```
> 
2. Your backlight interfaces and some of their settings:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

```

/sys/class/backlight/acpi_video0
0
100
/sys/class/backlight/nvidia_backlight
11
127

```

I should mention I have tried to directly update both acpi_video0's brightness and nvida_backlight's brightness via echo # > brightness, without much luck.
> 
3. The currently running modules:
```
lsmod
```

```

Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  12 
bnep                   18036  2 
binfmt_misc            17500  1 
joydev                 17377  0 
nvidia               9430062  81 
arc4                   12615  2 
iwldvm                241872  0 
mac80211              606457  1 iwldvm
snd_hda_codec_hdmi     36913  1 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
coretemp               13355  0 
snd_hda_codec_realtek    78399  1 
kvm                   443165  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          39619  5 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ideapad_laptop         18394  0 
sparse_keymap          13890  1 ideapad_laptop
nvidiabl               45400  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
btusb                  22474  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
iwlwifi               173477  1 iwldvm
snd_timer              29425  2 snd_pcm,snd_seq
bluetooth             228667  22 bnep,btusb,rfcomm
mac_hid                13205  0 
cfg80211              510937  3 iwlwifi,mac80211,iwldvm
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
alx                    67960  0 
lpc_ich                17061  0 
mei                    41158  0 
psmouse                95870  0 
lp                     17759  0 
mdio                   13807  1 alx
parport                46345  3 lp,ppdev,parport_pc
serio_raw              13215  0 
soundcore              12680  1 snd
microcode              22881  0 
vesafb                 13828  1 
nouveau               943184  0 
mxm_wmi                13021  1 nouveau
i2c_algo_bit           13413  1 nouveau
ttm                    83187  1 nouveau
wmi                    19070  2 mxm_wmi,nouveau
drm_kms_helper         49394  1 nouveau
video                  19390  1 nouveau
ahci                   25731  2 
libahci                31364  1 ahci
drm                   286028  6 ttm,drm_kms_helper,nvidia,nouveau

```

> 
4. You acpi brightness key codes. To do this, in a terminal, run:
```
acpi_listen
```
...then press the function+brightness+up key combination and note the codes that display in the terminal window. Do the same for function+brightness_down. Post back the results.
[/QUOTE]

```
 

video LCD 00000086 00000000
video LCD 00000087 00000000


```

---

### Post by Toz on 2013-08-13
A couple of things:

[LIST=1]
[*]You seem to have the nvidiabl module loaded, but I'm not seeing the nvidiabl backlight interface. Can you try manually unloading and reloading the module like this:
```
sudo modprobe -r nvidiabl
```
...then run and post back the results of:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
...then reload the module with verbose messaging:
```
sudo modprobe -v nvidiabl
```
...and post back any messages that display. As well as once again:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
[*]> I should mention I have tried to directly update both acpi_video0's brightness and nvida_backlight's brightness via echo # > brightness, without much luck.
Can I assume that you used commands like:
```
echo 50 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 75 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```

Can you try again booting with the kernel parameter **acpi_backlight=vendor**? On reboot, can you post back again the results of all of the commands from my post #2?
[*]
[/LIST]

---

### Post by mr-gary-waters on 2013-08-13
> **Toz said:**
> A couple of things:

[LIST=1]
[*]You seem to have the nvidiabl module loaded, but I'm not seeing the nvidiabl backlight interface. Can you try manually unloading and reloading the module like this:
```
sudo modprobe -r nvidiabl
```
...then run and post back the results of:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
[/LIST]

Here you go:
```

/sys/class/backlight/acpi_video0
0
100

```
> 
...then reload the module with verbose messaging:


[LIST=1]
[*]```
sudo modprobe -v nvidiabl
```
...and post back any messages that display. As well as once again:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
[/LIST]


```

Note: if my command doesnt say sudo, i am running it as root:
sudo modprobe -v nvidiabl
insmod /lib/modules/3.8.0-27-generic/updates/dkms/nvidiabl.ko 
>:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
0
100
/sys/class/backlight/nvidia_backlight
11
127

```
> 

[LIST=1]
[*]
Can I assume that you used commands like:
```
echo 50 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 75 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```
[/LIST]


I did something similar I just did as root:
```

echo 50 > /sys/class/backlight/acpi_video0/brightness
echo 75 > /sys/class/backlight/nvidia_backlight/brightness

```

Just in case, I tried your tee version and the same thing occurred, where it updated the value of brightness, but it did not affect the actual back light.
> 

[LIST=1]
[*]Can you try again booting with the kernel parameter **acpi_backlight=vendor**? On reboot, can you post back again the results of all of the commands from my post #2?
[/LIST]


Yes, be right back, I need to reboot my computer. 

I should mention I have also tried to specify things more granular as well with nvidiabl like so:
```

NVIDIABL_DECLARE_LAPTOP_MODEL("LENOVO", "20217", 0x0fe4, NVIDIABL_SC_AUTO, NVIDIABL_AUTO, NVIDIABL_AUTO, 0x1FFFF),
NVIDIABL_DECLARE_GPU_MODEL(0x0fe4, nv5x_driver_data),

```

It didnt help, but it made me feel better.
-G

---

### Post by Toz on 2013-08-13
Ok, I see. the nvidiabl seems to have changed the name of the module since the last time I had a look at it. Let me know the results after your reboot. I want to see if we can get a backlght interface that we can manipulate manually.

---

### Post by mr-gary-waters on 2013-08-13
Results
```

cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-3.8.0-27-generic root=UUID=b20e2a92-8826-4a04-97b6-5836cd1f824e ro nomodeset=1 acpi_backlight=vendor


for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/ideapad
10
16
/sys/class/backlight/nvidia_backlight
11
127


lsmod
Module                  Size  Used by
ip6table_filter        12815  0 
ip6_tables             27025  1 ip6table_filter
iptable_filter         12810  0 
ip_tables              26995  1 iptable_filter
x_tables               29803  4 ip6table_filter,ip_tables,iptable_filter,ip6_tables
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  12 
bnep                   18036  2 
binfmt_misc            17500  1 
joydev                 17377  0 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
arc4                   12615  2 
iwldvm                241872  0 
mac80211              606457  1 iwldvm
coretemp               13355  0 
kvm                   443165  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_hdmi     36913  1 
nvidia               9430062  69 
nvidiabl               45400  0 
snd_hda_codec_realtek    78399  1 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_hda_intel          39619  7 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
ideapad_laptop         18394  0 
sparse_keymap          13890  1 ideapad_laptop
snd_pcm                97451  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
iwlwifi               173477  1 iwldvm
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29425  2 snd_pcm,snd_seq
mac_hid                13205  0 
lpc_ich                17061  0 
cfg80211              510937  3 iwlwifi,mac80211,iwldvm
btusb                  22474  0 
bluetooth             228667  22 bnep,btusb,rfcomm
alx                    67960  0 
snd                    68876  23 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
psmouse                95870  0 
mdio                   13807  1 alx
mei                    41158  0 
lp                     17759  0 
serio_raw              13215  0 
parport                46345  3 lp,ppdev,parport_pc
microcode              22881  0 
soundcore              12680  1 snd
vesafb                 13828  1 
nouveau               943184  0 
mxm_wmi                13021  1 nouveau
wmi                    19070  2 mxm_wmi,nouveau
video                  19390  1 nouveau
i2c_algo_bit           13413  1 nouveau
ttm                    83187  1 nouveau
ahci                   25731  2 
libahci                31364  1 ahci
drm_kms_helper         49394  1 nouveau
drm                   286028  6 ttm,drm_kms_helper,nvidia,nouveau




acpi_listen
video LCD 00000086 00000000
video LCD 00000087 00000000


for fun:


>:~$ echo 16 | sudo tee /sys/class/backlight/ideapad/brightness 
16
>:~$ echo 1 | sudo tee /sys/class/backlight/ideapad/brightness
1


no change.

```

---

### Post by mr-gary-waters on 2013-08-13
Do you know what xbacklight manipulates? xbacklight -set ## % seems to work pretty well.

---

### Post by Toz on 2013-08-13
> **mr-gary-waters said:**
> Results
```

cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-3.8.0-27-generic root=UUID=b20e2a92-8826-4a04-97b6-5836cd1f824e ro nomodeset=1 acpi_backlight=vendor


for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/ideapad
10
16
/sys/class/backlight/nvidia_backlight
11
127


lsmod
Module                  Size  Used by
ip6table_filter        12815  0 
ip6_tables             27025  1 ip6table_filter
iptable_filter         12810  0 
ip_tables              26995  1 iptable_filter
x_tables               29803  4 ip6table_filter,ip_tables,iptable_filter,ip6_tables
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  12 
bnep                   18036  2 
binfmt_misc            17500  1 
joydev                 17377  0 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
arc4                   12615  2 
iwldvm                241872  0 
mac80211              606457  1 iwldvm
coretemp               13355  0 
kvm                   443165  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_hdmi     36913  1 
nvidia               9430062  69 
nvidiabl               45400  0 
snd_hda_codec_realtek    78399  1 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_hda_intel          39619  7 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
ideapad_laptop         18394  0 
sparse_keymap          13890  1 ideapad_laptop
snd_pcm                97451  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
iwlwifi               173477  1 iwldvm
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29425  2 snd_pcm,snd_seq
mac_hid                13205  0 
lpc_ich                17061  0 
cfg80211              510937  3 iwlwifi,mac80211,iwldvm
btusb                  22474  0 
bluetooth             228667  22 bnep,btusb,rfcomm
alx                    67960  0 
snd                    68876  23 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
psmouse                95870  0 
mdio                   13807  1 alx
mei                    41158  0 
lp                     17759  0 
serio_raw              13215  0 
parport                46345  3 lp,ppdev,parport_pc
microcode              22881  0 
soundcore              12680  1 snd
vesafb                 13828  1 
nouveau               943184  0 
mxm_wmi                13021  1 nouveau
wmi                    19070  2 mxm_wmi,nouveau
video                  19390  1 nouveau
i2c_algo_bit           13413  1 nouveau
ttm                    83187  1 nouveau
ahci                   25731  2 
libahci                31364  1 ahci
drm_kms_helper         49394  1 nouveau
drm                   286028  6 ttm,drm_kms_helper,nvidia,nouveau




acpi_listen
video LCD 00000086 00000000
video LCD 00000087 00000000


for fun:


>:~$ echo 16 | sudo tee /sys/class/backlight/ideapad/brightness 
16
>:~$ echo 1 | sudo tee /sys/class/backlight/ideapad/brightness
1


no change.

```

Interesting. Can you try enabling nvidia brightness control? As root, create the file /usr/share/X11/xorg.d/20-nvidia.conf with the following content:
```
Section "Device"
	Identifier "NVIDIA"
	Driver "nvidia"
	Option  "NoLogo" "True"
	Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```
You'll need to log out and back in again to test.

---

### Post by Toz on 2013-08-13
> **mr-gary-waters said:**
> Do you know what xbacklight manipulates? xbacklight -set ## % seems to work pretty well.

I'm not 100% sure, but I think it uses the xrandr interface. Can you also try:
```
xrandr --output  --brightness 0.5
```
```
xrandr --output  --brightness 1.0
```
...to see if that works as well?

---

### Post by Toz on 2013-08-13
> **Toz said:**
> Interesting. Can you try enabling nvidia brightness control? As root, create the file /usr/share/X11/xorg.d/20-nvidia.conf with the following content:
```
Section "Device"
	Identifier "NVIDIA"
	Driver "nvidia"
	Option  "NoLogo" "True"
	Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```
You'll need to log out and back in again to test.

I just realized that if you already have an xorg.conf file, it might be better to add:
```
	Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the Device section of that file instead.

---

### Post by mr-gary-waters on 2013-08-13
> **Toz said:**
> Interesting. Can you try enabling nvidia brightness control? As root, create the file /usr/share/X11/xorg.d/20-nvidia.conf with the following content:
```
Section "Device"
    Identifier "NVIDIA"
    Driver "nvidia"
    Option  "NoLogo" "True"
    Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```
You'll need to log out and back in again to test.

No luck.  The gui of the brightness controls always shows up, but has no effect.

---

### Post by mr-gary-waters on 2013-08-13
> **Toz said:**
> I'm not 100% sure, but I think it uses the xrandr interface. Can you also try:
```
xrandr --output  --brightness 0.5
```
```
xrandr --output  --brightness 1.0
```
...to see if that works as well?

I keep getting a help return for that command, I am still trying to figure out how to fix the command.
I think I need a display for --output.  How do I figure out the name or XID for my display ?

---

### Post by Toz on 2013-08-13
Okay, try this. With "acpi_backlght=vendor" and "EnableBrightnessControl=1" active, remove nvidiabl from /etc/modules so that it doesn't load on boot and reboot. You should then get only one interface (ideapad). Try the brightness controls now. Maybe the nvidiabl module is interfering. Usually, if you have only one backlight interface, acpi should have no problem finding it.

---

### Post by Toz on 2013-08-13
> **mr-gary-waters said:**
> I keep getting a help return for that command, I am still trying to figure out how to fix the command.
I think I need a display for --output.  How do I figure out the name or XID for my display ?

```
xrandr -q
```
...will give you that information.

---

### Post by mr-gary-waters on 2013-08-13
> **Toz said:**
> ```
xrandr -q
```
...will give you that information.

This works : 
```

 xrandr --output 'DP-0' --brightness .9

```

---

### Post by Toz on 2013-08-13
Can you try my suggestion in post #14?

---

### Post by mr-gary-waters on 2013-08-13
> **Toz said:**
> Okay, try this. With "acpi_backlght=vendor" and "EnableBrightnessControl=1" active, remove nvidiabl from /etc/modules so that it doesn't load on boot and reboot. You should then get only one interface (ideapad). Try the brightness controls now. Maybe the nvidiabl module is interfering. Usually, if you have only one backlight interface, acpi should have no problem finding it.

Ok, so I know you had me earlier update the xorg.conf.d files, but I wasnt sure if that EnableBrightnessControl was a kernel parameter or not, but I did it anyways:

```

BOOT_IMAGE=/boot/vmlinuz-3.8.0-27-generic root=UUID=b20e2a92-8826-4a04-97b6-5836cd1f824e ro nomodeset=1 acpi_backlight=vendor EnableBrightnessControl=1

```

Nvidiabl still kept loading up, even thought I had it commented out of /etc/modules, so I just removed the whole module from the kernel, and rebooted.

No luck though, the gnome3 brightness gui shows up, only to taunt me.

---

### Post by Toz on 2013-08-13
> **mr-gary-waters said:**
> Ok, so I know you had me earlier update the xorg.conf.d files, but I wasnt sure if that EnableBrightnessControl was a kernel parameter or not, but I did it anyways:

```

BOOT_IMAGE=/boot/vmlinuz-3.8.0-27-generic root=UUID=b20e2a92-8826-4a04-97b6-5836cd1f824e ro nomodeset=1 acpi_backlight=vendor EnableBrightnessControl=1

```

Nvidiabl still kept loading up, even thought I had it commented out of /etc/modules, so I just removed the whole module from the kernel, and rebooted.

No luck though, the gnome3 brightness gui shows up, only to taunt me.
Sorry, but "EnableBrightnessControl=1 should be in your xorg.conf file in the Device section (or /usr/share/X11/xorg.d/20-nvidia.conf). It doesn't go in the kernel line.

This one is a real stumper. Can you try the acpi_osi=\"!Windows 2012\" kernel parameter one more time? No nvidiabl. Remove the existing kernel parameters. Post back the regular results. Lets see what backlight interfaces show up. If you can manipulate it with xbacklight/xrandr, we should be able to get acpi access to it.

---

### Post by mr-gary-waters on 2013-08-13
> **Toz said:**
> Sorry, but "EnableBrightnessControl=1 should be in your xorg.conf file in the Device section (or /usr/share/X11/xorg.d/20-nvidia.conf). It doesn't go in the kernel line.

This one is a real stumper. Can you try the acpi_osi=\"!Windows 2012\" kernel parameter one more time? No nvidiabl. Remove the existing kernel parameters. Post back the regular results. Lets see what backlight interfaces show up. If you can manipulate it with xbacklight/xrandr, we should be able to get acpi access to it.

```
cat /proc/cmdline BOOT_IMAGE=/boot/vmlinuz-3.8.0-27-generic root=UUID=b20e2a92-8826-4a04-97b6-5836cd1f824e ro nomodeset=1 acpi_osi=!Windows2012


for loop
/sys/class/backlight/acpi_video0
100
100

```

Hm.. this acpi parameter doesnt give me anything fun in the /sys/class/backlight other than the default acpi_video.

---

### Post by mr-gary-waters on 2013-08-13
> **Toz said:**
> I just realized that if you already have an xorg.conf file, it might be better to add:
```
    Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the Device section of that file instead.

Tried that, I have it in both conf.d and the xorg.conf file now. Heheh.  I am not sure what supersede's what, but its definitely in there.

---

### Post by mr-gary-waters on 2013-08-14
So I previously tried to use xbacklight in the /etc/acpi/event scripts to change the brightness, since i know they do change the backlight at the prompt.
Unfortunately, I could not get it to work, for some reason those commands could not be run from a script.
Getting a little desperate, I tried to create a custom key binding (gnome keyboard settings) to use the Fn + brightness up and Fn + brightness down to run the commands.
For some reason those are preserved, even though the Gnome keyboard settings say I have them.. Oh well.

I changed the script to use Ctrl + Up and Ctrl Down, and it works!

Its not the solution I was looking for, but it works.  Thanks Toz for your help.  
If we figured out the issue for the nvidiabl, I would have re-committed the changes back to the git repo to share with everyone.

-G

PS - I think I messed up the default brightness control keys (XF86BrightnessUp and Brightness Down). I unset them from the gnome-keyboard settings, but I am not sure if that completely fixed it.

---

### Post by MidnightNinja on 2013-08-21
I am having similar issues getting backlight working.  I tried recompiling nvidiabl from the source and I think I did it correctly(followed the same instructions from the notebook review website), but I am not sure-the module appears to install correctly, but it doesnt seem to create the necessary files to work properly.  I'm sure I've done a ton wrong :P  I will post back in a bit when I get a chance to run all of the commands on the first page.

Also, if anyone would be willing to jump on IRC and help me out, that would be appreciated

---

### Post by mr-gary-waters on 2013-08-22
This is how I did brightness control.

Install xbacklight via apt-get or your favorite package manager.

Created 2 custom keyboard shortcuts, but I would avoid using "Fn" keys for the keyboard shortcut, I mentioned earlier that seems to be saved.

Brightness Down:
```
 /usr/bin/xbacklight -dec 10 
```
Key combo = Ctrl+Down

Brightness Up:
```
 /usr/bin/xbacklight -inc 10 
```
Key combo = Ctrl+Up

---

### Post by radenkovich on 2013-12-11
Guys,

please confirm you are experiencing the same bug here 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1258058](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1258058)

Hopefuly it will then picked up and solved.

Cheers!

---

