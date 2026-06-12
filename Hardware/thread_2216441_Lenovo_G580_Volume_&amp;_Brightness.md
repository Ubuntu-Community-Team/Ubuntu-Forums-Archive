---
title: "Lenovo G580 Volume &amp; Brightness"
date: 2014-04-12
forum: Hardware
---

### Post by Adarzh on 2014-04-12
Hi,

I own a Lenovo G580 laptop. I'm having Ubuntu 13.10 installed in it with Windows 7 on dual boot. My problem is that in Ubuntu, I'm not able to change the brightness. The brightness stay as it is eventhough I can see in the notification window the value changes. Regarding volume, I can control volume but the sound output is very low in Ubuntu compared to Windows. 

Please help if anybody has any solution for it. I really like to continue on Ubuntu.

Regards,
Adarsh

---

### Post by Toz on 2014-04-12
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

---

### Post by Adarzh on 2014-04-20
I'm extremely sorry for the long delay. I just upgraded to 14.04. The issue is still present. Please see the results

1.
```

cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=23af1aab-8388-4f9b-ab01-a85742830613 ro splash quiet

```

2.
```

lspci -k | grep -iA2 VGA

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
	Subsystem: Lenovo Device 3977
	Kernel driver in use: i915

```

3.
```

for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done

 /sys/class/backlight/acpi_video0
15
15
15

 /sys/class/backlight/intel_backlight
4437
4437
4437

```

4.
```

lsmod

Module                  Size  Used by
ctr                    13049  2 
ccm                    17773  2 
nls_iso8859_1          12713  1 
rfcomm                 69160  8 
bnep                   19624  2 
snd_hda_codec_hdmi     46207  1 
snd_hda_codec_realtek    61438  1 
arc4                   12608  2 
rtl8192cu              67723  0 
rtl_usb                18448  1 rtl8192cu
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
rtlwifi                63475  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
btusb                  32412  0 
videobuf2_core         40664  1 uvcvideo
bluetooth             395423  22 bnep,btusb,rfcomm
videodev              134688  2 uvcvideo,videobuf2_core
mac80211              626489  3 rtl_usb,rtlwifi,rtl8192cu
joydev                 17381  0 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
snd_hda_intel          52355  6 
kvm                   451511  1 kvm_intel
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
crct10dif_pclmul       14289  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
crc32_pclmul           13113  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ghash_clmulni_intel    13259  0 
snd_rawmidi            30144  1 snd_seq_midi
aesni_intel            55624  4 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lib80211_crypt_tkip    17619  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
psmouse               102222  0 
serio_raw              13462  0 
lpc_ich                21080  0 
wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
snd_timer              29482  2 snd_pcm,snd_seq
cfg80211              484040  3 wl,mac80211,rtlwifi
i915                  783485  3 
snd                    69238  23 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
mei_me                 18627  0 
drm_kms_helper         52758  1 i915
mei                    82274  1 mei_me
drm                   302817  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
wmi                    19177  0 
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop
video                  19476  1 i915
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
usb_storage            62209  1 
alx                    32452  0 
mdio                   13807  1 alx


```

5.
```

pastebinit /var/log/Xorg.0.log

http://paste.ubuntu.com/7293144/

```


I had a Dell laptop before. I never had to do anything on that after installing old Ubuntus. Now nothing works. I think my Lenovo doesn't support Linux.

Regards,
Adarsh

---

### Post by Toz on 2014-04-20
>  /sys/class/backlight/acpi_video0
15
15
15

 /sys/class/backlight/intel_backlight
4437
4437
4437
You have 2 backlight interfaces and the system is probably confused.

Lets try this solution first (force the system to use the intel_backlight interface):

1. With root privileges, create the file /usr/share/X11/xorg.conf.d/20intel.conf:
```
sudo -i gedit /usr/share/X11/xorg.conf.d/20intel.conf
```

2. Copy/paste the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```

3. Save the file. Log out and back in again to check.

---

### Post by Adarzh on 2014-04-20
The solution works. Now I'm able to change the brightness. Volume issue.. its good if you have any solutions else i'm fine

Thank you, Toz

Adarsh

---

### Post by Toz on 2014-04-20
> **Adarzh said:**
> Volume issue.. its good if you have any solutions else i'm fine
You should mark this thread as SOLVED using the Thread Tools link above and create a new thread for the sound issue. There may be someone else with more experience to help you solve that issue.

---

