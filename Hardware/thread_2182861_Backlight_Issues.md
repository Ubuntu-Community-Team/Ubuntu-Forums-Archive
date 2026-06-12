---
title: "Backlight Issues"
date: 2013-10-22
forum: Hardware
---

### Post by LinuxVirgin2000 on 2013-10-22
Hi Please someone help me!!

I have a toshiba u920t convertible ultrabook, im trying to get any linux distro to work on it. I have tried Fedora, Open Suse, and now Ubuntu 13.10. Each distro has had a similar problem with the screen backlight, it is permanently on max. the slider in poweroptions has no effect and the "Fn" buttons do not change brightness either, the os dose not even show the brightness indicator going up and down when using "fn" buttons, but weirdly the brightness down button puts the computer into standby! this happened in fedora too.

I came across this webpage suggesting how to change brightness via terminal:

[http://linuxg.net/change-the-brightness-via-command-line/](http://linuxg.net/change-the-brightness-via-command-line/)

I dont really know how to use terminal so I may have done something wrong but when i pasted:

[COLOR=#555555][FONT=consolas]# echo 3 > /sys/class/backlight/acpi_video0/brightness
[/FONT][/COLOR]
into terminal absolutely nothing happens, not even a message comes up

I even tried:

[COLOR=#555555][FONT=consolas]echo 3 > /sys/class/backlight/acpi_video0/brightness
[/FONT][/COLOR]
i.e without the "#" just for the hell of it, and a message came up saying "permission denied

I tried both of the above on my other ubuntu laptop where the brightness does work and the same thing happened so i guess im just typing the command wrong :(


The only other things to mention are that the brightness works in windows 8, the ultrabook has an ambient light sensor which may be messing things up and I hate it anyway so i don't care if it doesn't work, and also when in Open Suse i navigated to the file:
 [COLOR=#555555][FONT=consolas]/sys/class/backlight/acpi_video0/brightness
[/FONT][/COLOR]the value was set to 100 and i could not change it, but i cant find this file in ubuntu

one last thing; as well as [COLOR=#555555][FONT=consolas]/sys/class/backlight/acpi_video0/brightness
[/FONT][/COLOR]there were two other files something along the lines of:
[COLOR=#555555][FONT=consolas]/sys/class/backlight/intel/brightness[/FONT][/COLOR]
which was set to 0 i think

and [COLOR=#555555][FONT=consolas]/sys/class/backlight/toshiba/brightness[/FONT][/COLOR]
which was set to something random like 1470


unfortunately i cant seem to find these files on ubuntu live usb and seeing as I deleted the open suse usb to make this ubuntu one I can't go back and check to see if i'm telling you the right things,


please someone help me solve this problem, all I want to be able to do is turn the brightness Up and down as needed, I don't care if I have to do it through terminal for ever I just need a solution! I don't wanna be stuck with crappy windows 8 just because of one tiny issue.

Thanks in advance :)

---

### Post by Toz on 2013-10-22
Lets get some detailed information about your system. Can you open a terminal window, type in the following commands, and post back the results:

1. Your current kernel boot line:
```
cat /proc/cmdline
```

2. Info about your video card(s):
```
lspci -k | grep -iA3 VGA
```

3. Your current backlight interfaces and their values:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

4. Your dmesg log file:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

5. Your Xorg log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

Note: if you get a message about pastebinit not being installed, you can install it via:
```
sudo apt-get install pastebinit
```

EDIT: Can you also post back a listing of your kernel modules:
```
lsmod
```

---

### Post by LinuxVirgin2000 on 2013-10-23
Hi thnaks so much for replying, heres the info you requested :)


1. current kernel boot line:
```
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

```

2. Info about video card(s):
```
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: Toshiba America Info Systems Device 0006
    Kernel driver in use: i915
```


3. current backlight interfaces and their values:
```
/sys/class/backlight/acpi_video0
100
100
100
/sys/class/backlight/intel_backlight
4542
4542
4542
/sys/class/backlight/toshiba
0
0
7
```


4. dmesg log file:
[http://paste.ubuntu.com/6289559/](http://paste.ubuntu.com/6289559/)


5. Xorg log file:
[http://paste.ubuntu.com/6289579/](http://paste.ubuntu.com/6289579/)

6.kernel modules:
```
Module                  Size  Used by
dm_crypt               22728  0 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138538  0 
kvm                   431315  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  3 
microread_mei          12811  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
microread              13420  1 microread_mei
gf128mul               14951  1 lrw
mei_phy                13881  1 microread_mei
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
btusb                  28267  0 
crc_ccitt              12707  1 microread
arc4                   12608  2 
hci                    44425  2 mei_phy,microread
nfc                    94614  2 hci,microread
snd_hda_codec_hdmi     41276  1 
iwldvm                237440  0 
joydev                 17377  0 
snd_hda_codec_realtek    51465  1 
mac80211              596969  1 iwldvm
snd_hda_intel          48171  3 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
uvcvideo               80885  0 
snd_hwdep              13602  1 snd_hda_codec
dm_multipath           22843  0 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
iwlwifi               165398  1 iwldvm
cp210x                 23475  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
scsi_dh                14882  1 dm_multipath
usbserial              44667  1 cp210x
rts5139               331166  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
cfg80211              479757  3 iwlwifi,mac80211,iwldvm
hid_sensor_hub         19096  0 
snd_seq_midi_event     14899  1 snd_seq_midi
hid_multitouch         17407  0 
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
microcode              23518  0 
soundcore              12680  1 snd
toshiba_acpi           22901  0 
sparse_keymap          13948  1 toshiba_acpi
wmi                    19070  1 toshiba_acpi
mei_me                 18421  0 
psmouse                97626  0 
toshiba_bluetooth      12852  0 
mei                    77692  3 mei_phy,mei_me,microread_mei
lpc_ich                21080  0 
bnep                   19564  2 
parport_pc             32701  0 
rfcomm                 69070  12 
ppdev                  17671  0 
intel_rst              12953  0 
lp                     17759  0 
serio_raw              13413  0 
mac_hid                13205  0 
parport                42299  3 lp,ppdev,parport_pc
bluetooth             371874  22 bnep,btusb,rfcomm
squashfs               47663  1 
overlayfs              27858  1 
nls_iso8859_1          12713  1 
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101512  4 hid_multitouch,hid_generic,hid_sensor_hub,usbhid
dm_mirror              22056  0 
dm_region_hash         20784  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
usb_storage            62062  1 
i915                  655752  3 
i2c_algo_bit           13413  1 i915
drm_kms_helper         52651  1 i915
drm                   296739  4 i915,drm_kms_helper
ahci                   25819  0 
libahci                31898  1 ahci
video                  19318  1 i915
```

---

### Post by Toz on 2013-10-23
> **LinuxVirgin2000 said:**
> 1. current kernel boot line:
```
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

```
How is ubuntu installed on your computer? Are you running the live cd?

> 3. current backlight interfaces and their values:
```
/sys/class/backlight/acpi_video0
100
100
100
/sys/class/backlight/intel_backlight
4542
4542
4542
/sys/class/backlight/toshiba
0
0
7
```
You have 3 current backlight interfaces. I would suggest blacklisting the toshiba_acpi module and forcing the use of the intel_backlight interface. Here is how:
1. Blacklisting toshiba_acpi:
```
sudo -i gedit /etc/modprobe.d/blacklist
```
...enter your password when prompted and add the following line to the end of the file:
```
blacklist toshiba_acpi
```
...and save the file.

2. Force the use of the intel_backlight interface:
```
sudo -i gedit  /usr/share/X11/xorg.conf.d/20-intel.conf
```
and copy/paste the following code:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
...save the file.

3. Reboot and test.

If it still doesn't work, post back the same information again as per post #2.

---

### Post by LinuxVirgin2000 on 2013-10-26
Hi, I tried the above but it won't work anyway because im running ubuntu from a live USB because i need to find an OS that works before I install it, when I was making the Live USB (using startup disk creator on my other ubuntu 12.04 laptop) the slider to select how much space to preserve for storage was grayed out, so when i have to reboot the machine as your instructions above ask all the changes are being lost I guess. The weird thing is that when i try to make a 12.04 live USB it allows me to make the USB persistent but for 13.10 it dosent let me. I would happily just use 12.04 but its refusing to boot on my ultrabook (i think its something to do with secure boot)

---

### Post by LinuxVirgin2000 on 2013-11-10
Hi Toz, i finally managed to make my live USB persistent with the kind help of people on this forum and I used your suggestion above and it works great!!!! I can't change the brightness using the Fn buttons still but atleast it can change using the slider in brightness settings. thank you very much :)

---

### Post by kurtis.pankow on 2013-11-15
2. Force the use of the intel_backlight interface:
```
sudo -i gedit  /usr/share/X11/xorg.conf.d/20-intel.conf
```
and copy/paste the following code:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
...save the file.

3. Reboot and test.

If it still doesn't work, post back the same information again as per post #2.[/QUOTE]




I've been experiencing the same issue since I installed Ubuntu about a year ago. Ran only this part, and now it works like a charm. Thanks a ton!

---

