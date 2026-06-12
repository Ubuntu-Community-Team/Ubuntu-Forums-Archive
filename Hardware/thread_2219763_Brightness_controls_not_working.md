---
title: "Brightness controls not working"
date: 2014-04-25
forum: Hardware
---

### Post by gabo.cr on 2014-04-25
Hi,
I can't change the brigthness on the screen when I use the Fn option. I can see the control is changing but the brightness stays the same.
I noticed this is a very common problem, but everyone seems to have small different aspects of the issue, so I don't want to try a solution that's not correspondent to me. (I learned that lesson the hard way).
;)

I have a Dell Inspiron 15R (5521) 64bit, Intel Core i5. 
Ubuntu 14.04 fresh install.

Here is more info:

Imput:
```
cat /proc/cmdline
```
Output:
```
BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=6bcf494c-b966-428b-8b27-3799ada2af74 ro quiet splash vt.handoff=7

```

Imput:
```
lspci -k | grep -iA2 VGA
```
Output:
```
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
	Subsystem: Dell Device 0597
	Kernel driver in use: i915

```

Imput:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
Output:
```
 /sys/class/backlight/acpi_video0
99
99
99

 /sys/class/backlight/intel_backlight
1455
4882
1455

```

Imput:
```
lsmod
```
Output:
```
Module                  Size  Used by
ctr                    13049  2 
ccm                    17773  2 
bnep                   19624  2 
rfcomm                 69160  8 
snd_hda_codec_hdmi     46207  1 
joydev                 17381  0 
snd_hda_codec_realtek    61438  1 
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
rts5139               335409  0 
uvcvideo               80885  0 
intel_rapl             18773  0 
arc4                   12608  2 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
x86_pkg_temp_thermal    14205  0 
iwldvm                232285  0 
videodev              134688  2 uvcvideo,videobuf2_core
intel_powerclamp       14705  0 
mac80211              626489  1 iwldvm
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
snd_hda_intel          52355  3 
btusb                  32412  0 
crct10dif_pclmul       14289  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
iwlwifi               169932  1 iwldvm
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
bluetooth             395423  22 bnep,btusb,rfcomm
binfmt_misc            17468  1 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
mei_me                 18627  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
dell_laptop            18168  0 
aesni_intel            55624  4 
aes_x86_64             17131  1 aesni_intel
wmi                    19177  1 dell_wmi
i915                  783485  4 
lrw                    13286  1 aesni_intel
snd                    69238  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
gf128mul               14951  1 lrw
mei                    82274  1 mei_me
glue_helper            13990  1 aesni_intel
drm_kms_helper         52758  1 i915
soundcore              12680  1 snd
ablk_helper            13597  1 aesni_intel
drm                   302817  5 i915,drm_kms_helper
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
i2c_algo_bit           13413  1 i915
dcdbas                 14928  1 dell_laptop
lpc_ich                21080  0 
psmouse               102222  0 
video                  19476  1 i915
serio_raw              13462  0 
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
ahci                   25819  3 
r8169                  67581  0 
libahci                32168  1 ahci
mii                    13934  1 r8169

```

Imput:
```
pastebinit /var/log/Xorg.0.log
```

Output:
```
http://paste.ubuntu.com/7330088/
```

---

### Post by Adarzh on 2014-04-25
I had this issue in my Lenovo laptop. Seems same issue. See my question thread. 

[http://ubuntuforums.org/showthread.php?t=2216441](http://ubuntuforums.org/showthread.php?t=2216441)

---

### Post by gabo.cr on 2014-04-25
It works, thank you !

---

