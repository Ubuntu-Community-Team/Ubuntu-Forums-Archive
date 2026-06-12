---
title: "Can't adjust brightness with ASUS X450LN in Ubuntu 14.04"
date: 2014-07-22
forum: Hardware
---

### Post by miguel-carcamo on 2014-07-22
I bought a notebook ASUS X450LN and I've installed Ubuntu 14.04 on it.

The thing is that I can't change brightness through the default keys to do it.

I've just installed Brightness controller but it doesn't work. I can change the brightness in the application but with keys I can't.

My question is: How can this be fixed?

Cheers folks!

Relevant Info:


This can change the brightness:
> sudo su
"echo 200 > /sys/class/backlight/intel_backlight/brightness"

cat /proc/cmdline:

> BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=7c476225-d36b-4290-86f4-9ee0770175f2 ro quiet splash vt.handoff=7

lspci -k | grep -A3 VGA:
> 00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 13fd
    Kernel driver in use: i915
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)

for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done:

> /sys/class/backlight/acpi_video0
100
100
100
/sys/class/backlight/acpi_video1
100
100
100
/sys/class/backlight/intel_backlight
937
937
937

pastebinit /var/log/Xorg.0.log:

[http://paste.ubuntu.com/7834768/](http://paste.ubuntu.com/7834768/)

The video card is an optimus/hybrid one: Intel/NVidia

I've installed nvidia-prime by the way.

---

### Post by bufordsf on 2014-07-22
Here is some excessive background info:
[https://wiki.archlinux.org/index.php/backlight](https://wiki.archlinux.org/index.php/backlight)

Maybe useful other posts:
[https://bbs.archlinux.org/viewtopic.php?id=178014](https://bbs.archlinux.org/viewtopic.php?id=178014)
[http://itsfoss.com/fix-brightness-ubuntu-1310](http://itsfoss.com/fix-brightness-ubuntu-1310)

To manually change it (not what you want to do), find the appropriate directory, something like
sudo sh -c echo 4882 > /sys/class/backlight/intel_backlight/brightness
where 4882 is a number between 0 and the value in max_brightness.

What worked for me may be because of my hardware. If this doesn't work, post the output of lshw and look for a disply. To fix Desktop system to get it correct:
 
```
sudo touch /usr/share/X11/xorg.conf.d/20-intel.conf
sudo gedit /usr/share/X11/xorg.conf.d/20-intel.conf
```
Insert these lines:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection
```

---

### Post by miguel-carcamo on 2014-07-22
> **bufordsf said:**
> Here is some excessive background info:
[https://wiki.archlinux.org/index.php/backlight](https://wiki.archlinux.org/index.php/backlight)

Maybe useful other posts:
[https://bbs.archlinux.org/viewtopic.php?id=178014](https://bbs.archlinux.org/viewtopic.php?id=178014)
[http://itsfoss.com/fix-brightness-ubuntu-1310](http://itsfoss.com/fix-brightness-ubuntu-1310)

[B]
This change the brightness:[/B]
To manually change it (not what you want to do), find the appropriate directory, something like
sudo sh -c echo 4882 > /sys/class/backlight/intel_backlight/brightness
where 4882 is a number between 0 and the value in max_brightness.

What worked for me may be because of my hardware. If this doesn't work, post the output of lshw and look for a disply. To fix Desktop system to get it correct:
 

**I did this without any luck, the keys doesn't do anything:**
```
sudo touch /usr/share/X11/xorg.conf.d/20-intel.conf
sudo gedit /usr/share/X11/xorg.conf.d/20-intel.conf
```
Insert these lines:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection
```

I did this before without any luck man.

It's obvious that I restarted or logged out and logged in back after doing that.

---

### Post by bufordsf on 2014-07-22
When you hit the keys, does a little window pop up showing the slider changing? Or not even that? I mean, it doesn't even change the value in brightness in the default backlight directory?

---

### Post by jeremy31 on 2014-07-22
> **bufordsf said:**
> When you hit the keys, does a little window pop up showing the slider changing? Or not even that? I mean, it doesn't even change the value in brightness in the default backlight directory?

Is there any response from the brightness keys in terminal after ```
acpi_listen
``` CTRL+c to stop acpi_listen or ```
xev
```

Have you edited /etc/default/grub to add acpi_osi=linux to the line with quiet splash

---

### Post by Toz on 2014-07-22
> for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done:
```
/sys/class/backlight/acpi_video0
100
100
100
/sys/class/backlight/acpi_video1
100
100
100
/sys/class/backlight/intel_backlight
937
937
937
```

I find this interesting. Usually when you have two acpi_video interfaces, it means there are 2 video adapters in your system, yet your lspci command and the Xorg log file only indicate one.

Since the intel_backlight interface affects backlight, in addition to @jeremy31's suggestion of trying the "acpi_osi=linux" kernel parameter, I would also suggest trying:
- **video.use_native_backlight=1** (this should remove the 2 acpi_video interfaces)
...and
- **acpi_osi='!Windows 2012'** (to let the kernel know that you are not running Windows 8 so that a different set of acpi tables can be loaded).

---

### Post by miguel-carcamo on 2014-07-22
Nothing seems to happen when I hit Fn+F5 or Fn+F6

---

### Post by miguel-carcamo on 2014-07-22
>  					[IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **bufordsf** 					[[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=13079750#post13079750") 				
 				When you hit the keys, does a little window pop  up showing the slider changing? Or not even that? I mean, it doesn't  even change the value in brightness in the default backlight directory?
 			 		 	 Is there any response from the brightness keys in terminal after  	Code:
 	acpi_listen 
 CTRL+c to stop acpi_listen or  	Code:
 	xev 
Have you edited /etc/default/grub to add acpi_osi=linux to the line with quiet splash
I did the two first terminal commands, and no, there is no response in the terminal or in the frame. However, with the audio keys there is a response.

The third thing doesn't seem to solve the problem.

---

### Post by miguel-carcamo on 2014-07-22
> **Toz said:**
> I find this interesting. Usually when you have two acpi_video interfaces, it means there are 2 video adapters in your system, yet your lspci command and the Xorg log file only indicate one.

Since the intel_backlight interface affects backlight, in addition to @jeremy31's suggestion of trying the "acpi_osi=linux" kernel parameter, I would also suggest trying:
- **video.use_native_backlight=1** (this should remove the 2 acpi_video interfaces)
...and
- **acpi_osi='!Windows 2012'** (to let the kernel know that you are not running Windows 8 so that a different set of acpi tables can be loaded).

video.use_native_backlight=1 does have a bad effect making unity very very slow.
And acpi_osi='!Windows 2012' doesn't seem to work at all.

---

### Post by jeremy31 on 2014-07-22
> **miguel-carcamo said:**
> video.use_native_backlight=1 does have a bad effect making unity very very slow.
And acpi_osi='!Windows 2012' doesn't seem to work at all.

Can you show us the result of ```
lsmod
```

I think Toz may be right about the laptop having a hybrid graphics system after googling the model

---

### Post by bufordsf on 2014-07-22
In addition to setting the correct video interfaces, I'm just wondering whether unity is getting the key presses. I had to change my Xorg config to get key presses to change the brightness, but even before that the key presses were recognized. Do you get anything like in this picture, even if the brightness doesn't change?
[ATTACH=CONFIG]254940[/ATTACH]

see also [https://wiki.ubuntu.com/Kernel/Debugging/Backlight](https://wiki.ubuntu.com/Kernel/Debugging/Backlight)

---

### Post by miguel-carcamo on 2014-07-22
> **jeremy31 said:**
> Can you show us the result of ```
lsmod
```

I think Toz may be right about the laptop having a hybrid graphics system after googling the model

This is the result:

```

miguel@miguel-X450LN:~$ lsmod
Module                  Size  Used by
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
bbswitch               13943  0 
rfcomm                 69160  0 
bnep                   19624  2 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_conexant    57441  1 
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
mxm_wmi                13021  0 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
uvcvideo               80885  0 
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          52355  5 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_hwdep              13602  1 snd_hda_codec
arc4                   12608  2 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k                 164164  0 
snd_rawmidi            30144  1 snd_seq_midi
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
serio_raw              13462  0 
lpc_ich                21080  0 
cfg80211              484040  3 ath,ath9k,mac80211
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
i915                  783805  5 
ath3k                  13318  0 
snd_timer              29482  2 snd_pcm,snd_seq
btusb                  32412  0 
bluetooth             391196  12 bnep,ath3k,btusb,rfcomm
snd                    69238  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm_kms_helper         53081  1 i915
drm                   303102  4 i915,drm_kms_helper
mei_me                 18627  0 
mei                    82276  1 mei_me
i2c_algo_bit           13413  1 i915
soundcore              12680  1 snd
wmi                    19177  2 mxm_wmi,asus_wmi
video                  19476  2 i915,asus_wmi
parport_pc             32701  0 
mac_hid                13205  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
psmouse               106678  0 
ahci                   25819  4 
alx                    32452  0 
libahci                32560  1 ahci
mdio                   13807  1 alx


```

---

### Post by miguel-carcamo on 2014-07-22
> **bufordsf said:**
> In addition to setting the correct video interfaces, I'm just wondering whether unity is getting the key presses. I had to change my Xorg config to get key presses to change the brightness, but even before that the key presses were recognized. Do you get anything like in this picture, even if the brightness doesn't change?
[ATTACH=CONFIG]254940[/ATTACH]

see also [https://wiki.ubuntu.com/Kernel/Debugging/Backlight](https://wiki.ubuntu.com/Kernel/Debugging/Backlight)

I don't get anything like in that picture, when I press the keys ONLY for brightness. If I press keys for audio and that stuff I get messages like:
```
button/volumeup VOLUP 00000080 00000000 K
button/volumeup VOLUP 00000080 00000000 K
button/volumeup VOLUP 00000080 00000000 K
button/volumeup VOLUP 00000080 00000000 K
button/volumedown VOLDN 00000080 00000000 K
button/volumedown VOLDN 00000080 00000000 K
button/volumedown VOLDN 00000080 00000000 K
button/volumedown VOLDN 00000080 00000000 K
button/volumeup VOLUP 00000080 00000000 K
button/volumeup VOLUP 00000080 00000000 K


```

But like I said, with brightness keys I can't get something in the terminal.

---

### Post by miguel-carcamo on 2014-07-23
> **bufordsf said:**
> In addition to setting the correct video interfaces, I'm just wondering whether unity is getting the key presses. I had to change my Xorg config to get key presses to change the brightness, but even before that the key presses were recognized. Do you get anything like in this picture, even if the brightness doesn't change?
[ATTACH=CONFIG]254940[/ATTACH]

see also [https://wiki.ubuntu.com/Kernel/Debugging/Backlight](https://wiki.ubuntu.com/Kernel/Debugging/Backlight)

I'm almost sure that this is a kernel bug,  because I've that last link and I quote:

"if not found with keymap, use acpi_listen to determine whether the key is coming through as an ACPI event instead of a keypress 


[LIST=1]
[*]if  there is an ACPI event but no keypress, this is a bug in the kernel  (ubuntu-bug linux) for not translating the ACPI event to an input event. 
[*]if there is neither  an ACPI event nor an input event, this is probably also a kernel bug,  though probably harder to diagnose (WMI, perhaps?) " 
[/LIST]
We are at b.

Also I found out that

echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 4 | sudo tee /sys/class/backlight/acpi_video1/brightness
echo 300 | sudo tee /sys/class/backlight/intel_backlight/brightness

The three last lines can change the brightness.

---

### Post by varunendra on 2014-07-23
Just posted a possible workaround to compensate the Fn+ key combo, although I'd love to see a proper fix, especially when Toz is handling the thread. :)

By the way, here's the workaround I just posted (without testing, instructions based on a previous test) : [http://ubuntuforums.org/showthread.php?t=2235737&p=13081007#post13081007](http://ubuntuforums.org/showthread.php?t=2235737&p=13081007#post13081007)

**PS:**
Obviously the value of the variables "INCR, MIN and MAX" in the proposed script would need to be changed based on values acceptable in your case.

---

