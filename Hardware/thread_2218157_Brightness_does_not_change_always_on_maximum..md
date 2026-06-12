---
title: "Brightness does not change: always on maximum."
date: 2014-04-19
forum: Hardware
---

### Post by josh45 on 2014-04-19
I installed Xubuntu 14 on my computer today. The screen is very bright. Pressing the brightness up/down buttons changes the "meter" that shows brightness level (ie like volume, don't know what its called), but the actual brightness does not change. 
The brightness is always really high which is affecting my battery life.
I have a HP Pavilion 15 n268sa.

I saw somewhere that putting the following in GRUB helps:
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
But the only difference is that when I press the brightness up/down buttons now, the "meter" does not show up at all. 

Any help would be appreciated. Thank you.

---

### Post by trag on 2014-04-19
[COLOR=#333333][FONT=Helvetica Neue]Here&#8217;s a workaround by adding a[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue] [/FONT][/COLOR]**startup script which will automatically adjust screen brightness when Ubuntu boots up**[COLOR=#333333][FONT=Helvetica Neue].[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]To get started:
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]**1**. Press Ctrl+Alt+T on keyboard to open the terminal. When it opens, run the command below will give you the maximum level of your laptop backlight:
[/FONT][/COLOR]
cat /sys/class/backlight/acpi_video0/max_brightness[COLOR=#333333][FONT=Helvetica Neue]Mine is 9, so I can set backlight level from 0 to 9.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]**2**. Run the command below one by one. You&#8217;ll get the super user privilege and open the /etc/rc.local file, a script executed at the end of each multiuser runlevel, with gedit editor.
[/FONT][/COLOR]
sudo -i

gedit /etc/rc.local[COLOR=#333333][FONT=Helvetica Neue]Add the line below before the last. Change the number 0 to the brightness level you want.
[/FONT][/COLOR]
[INDENT]echo **0** > /sys/class/backlight/acpi_video0/brightness
good luck
trag


[/INDENT]

---

### Post by varunendra on 2014-04-20
To determine how many video devices your system recognizes and what are the possible brightness values it may accept, you may check (or post here) the output of the following code -
```
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```

If posting the output here, please use 'Code' tags. Please follow the "Use Code Tags" link in my signature if you need to see how to use them.

---

### Post by charles.figura on 2014-04-20
I have the same problem after updating to kubuntu 14.04 and installing the nvidia drivers.  When I run varun's code, I get:
```

 /sys/class/backlight/acpi_video0
15
15
15

```

Does this mean 15 levels?  Or that there's only one option, '15'?  I've seen a number of problems with the nvidia driver here: fonts are too big, OpenGL was disabled by default (but could be turned on), and the 'kubuntu' boot splash screen is humongous.  I suspect that it's all related!

For what it's worth, I followed the instructions on installing the nvidia drivers found here:
[http://ubuntuhandbook.org/index.php/2014/01/install-nvidia-driver-331-38-ubuntu/]("http://ubuntuhandbook.org/index.php/2014/01/install-nvidia-driver-331-38-ubuntu/")

---

### Post by varunendra on 2014-04-20
I am not an expert in brightness or graphics issues, but the value 15 indicates that you *may be* able to change the brightness using lower integer values like 6, 7, 8 etc. The command to try them can be -
```
echo 8 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
Change the echo value (8) to different values and see which ones (if any) are accepted. The current value (15) is the maximum value acceptable by this device (acpi_video0).

Also, there won't be any change if your laptop screen is using a different device, not the one represented as 'acpi_video0' (happens sometimes, especially in case of dedicated graphics). In that case, I am not sure what else you can try except some boot options as mentioned by josh45, or here : [https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)

Here on the forums, moderator **Toz** is a backlight expert who may offer better help on these issues. There may also be some others, but I personally remember only his name. :)

---

### Post by josh45 on 2014-04-20
Input:
```
[COLOR=#000000][FONT=Ubuntu Mono]for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done 
```
Output: 
```
 [/FONT][/COLOR]cat: /sys/class/backlight/*/brightness: No such file or directorycat: /sys/class/backlight/*/max_brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory

```

I tried changing /etc/rc.local as trag suggested but with no effect.

---

### Post by varunendra on 2014-04-20
Did you copy-paste the commands? Looks like some typing error in your commands. Please try it again, and if you get the same error again, copy-paste the command you used from your terminal to your post here so we can see if there is a typo.

---

### Post by josh45 on 2014-04-20
I copy and pasted it. Tried again just now by copying and pasting from your original post and got the same result. 
I used this command:
```
[COLOR=#000000][FONT=Ubuntu Mono]for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done 
```

Thank your for your quick responses! [/FONT][/COLOR]

---

### Post by varunendra on 2014-04-20
Hmm.. I am copy-pasting from your posts into my terminal here and am getting proper results as expected. Not sure what is going wrong and where.

Anyway, lets switch to manual mode :)

Please show us the output of -
```
ls -l /sys/class/backlight
```

---

### Post by charles.figura on 2014-04-20
Varun -  Thanks for the pointer.  I tried your recommendation.  The on-screen HUD changed value (same as using the function keys) but it did not actually change the screen brightness.

---

### Post by josh45 on 2014-04-20
Input: ```
 [COLOR=#000000][FONT=Ubuntu Mono]ls -l /sys/class/backlight 
```

Output: ```
 total 0 
```[/FONT][/COLOR]

---

### Post by charles.figura on 2014-04-20
Varun -

```
cfigura@nightfall:~$  ls -l /sys/class/backlight
total 0
lrwxrwxrwx 1 root root 0 Apr 20 07:01 acpi_video0 -> ../../devices/pci0000:00/0000:00:01.0/0000:01:00.0/backlight/acpi_video0
```

---

### Post by varunendra on 2014-04-21
> **josh45 said:**
> Input: ```
 [COLOR=#000000][FONT=Ubuntu Mono]ls -l /sys/class/backlight 
```

Output: ```
 total 0 
```[/FONT][/COLOR]
No video devices in class 'backlight', means no generic video device was recognized by the kernel and so we have nothing to mess with there.

I believe (and I may be wrong) your display is being controlled by the vendor specific driver which is probably using a custom xorg.conf file. While this sentence may be making me look like a very knowledgeable person in these issues, my knowledge and wits actually end here with many questions unanswered.

The only advice I can offer now is to try installing "xbacklight" package and try it to see if it can control the brightness. It is a commandline utility, so you may have to read its man page (command - "man xbacklight") to see how to use it. To install it -
```
sudo apt-get install xbacklight
```
If this doesn't help, I'm afraid I may not be of more help on this. I'll PM Toz though requesting to take a look at this thread if he has the time.


@charles.figura,
> **charles.figura said:**
> I tried your recommendation.  The on-screen HUD changed value (same as using the function keys) but it did not actually change the screen brightness.
While a generic video device (acpi_video0) is clearly detected in your laptop, your case is otherwise almost the same as above - that is, the laptop screen is not the video device that is recognized there. It is most probably under control of a vendor-specific driver, and so my suggestion for you is same as above.

Let us know if 'xbacklight' can help you out.

---

### Post by Toz on 2014-04-21
For both posters, can we get a more detailed view into your setups? Can you please post back the results to the following commands?

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

### Post by charles.figura on 2014-04-21
Varun - Thanks for your help.  Unfortunately, I can't install xbacklight without uninstalling the drivers that I have currently installed!

Toz -  Here's what I have in response to your instructions.

$cat /proc/cmdline
```
BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=c22cd571-aa0e-4ce3-ad2f-8a14f53fc0c7 ro quiet splash vt.handoff=7
cfigura@nightfall:~$ lspci -k | grep -iA2 VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [Quadro NVS 4200M] (rev a1)
        Subsystem: Lenovo Device 21ce
        Kernel driver in use: nvidia

```

$ for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done

 ```
/sys/class/backlight/acpi_video0
15
15
15
```

$ lsmod
```
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
cuse                   13445  3 
hidp                   23870  0 
hid                   106148  1 hidp
joydev                 17381  0 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse               102222  0                                                                                
serio_raw              13462  0                                                                                
btusb                  32412  0                                                                                
uvcvideo               80885  0                                                                                
videobuf2_vmalloc      13216  1 uvcvideo                                                                       
videobuf2_memops       13362  1 videobuf2_vmalloc                                                              
videobuf2_core         40664  1 uvcvideo                                                                       
videodev              134688  2 uvcvideo,videobuf2_core                                                        
snd_hda_codec_hdmi     46207  1                                                                                
nvidia              10675249  52                                                                               
bnep                   19624  2                                                                                
rfcomm                 69160  12                                                                               
bluetooth             395423  23 bnep,hidp,btusb,rfcomm
arc4                   12608  2 
thinkpad_acpi          80817  1 
nvram                  14411  1 thinkpad_acpi
snd_seq_midi           13324  0 
iwldvm                232285  0 
mac80211              626489  1 iwldvm
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_codec_conexant    57441  1 
snd_hda_intel          52355  10 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_rawmidi            30144  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
iwlwifi               169932  1 iwldvm
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
mac_hid                13205  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_pcm               102099  5 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29482  2 snd_pcm,snd_seq
drm                   302817  2 nvidia
snd                    69238  30 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
binfmt_misc            17468  1 
mei_me                 18627  0 
lpc_ich                21080  0 
mei                    82274  1 mei_me
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
ses                    17363  0 
enclosure              15368  1 ses
usb_storage            62209  0 
mmc_block              35929  0 
wmi                    19177  0 
firewire_ohci          40409  0 
ahci                   25819  2 
e1000e                254433  0 
video                  19476  0 
libahci                32168  1 ahci
firewire_core          68769  1 firewire_ohci
sdhci_pci              23172  0 
sdhci                  43015  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
ptp                    18933  1 e1000e
pps_core               19382  1 ptp

```

$ pastebinit /var/log/Xorg.0.log
[HTML]http://paste.ubuntu.com/7299306/[/HTML]

---

### Post by josh45 on 2014-04-21
Thank you for your help Varun! Unfortunately, running xbacklight in terminal yields the following result:
```
 No outputs have backlight property

```

Hi Toz, thank you for your help! Here is the information you requested:
1. Your current kernel boot line:
```
BOOT_IMAGE=/vmlinuz-3.13.0-24-generic.efi.signed root=/dev/mapper/xubuntu--vg-root ro acpi_backlight=vendor nomodeset



```
2. Information about your video card(s):
```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8610G]
	Subsystem: Hewlett-Packard Company Device 216c
	Kernel driver in use: fglrx_pci



```


3. Information about your known backlight interfaces:
```
/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory



```



4. A listing of your loaded kernel modules:
```
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69160  4 
bluetooth             395423  10 bnep,rfcomm
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
joydev                 17381  0 
kvm                   451511  0 
arc4                   12608  2 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse               102222  0 
serio_raw              13462  0 
snd_hda_codec_realtek    61438  1 
snd_hda_codec_hdmi     46207  1 
snd_hda_intel          52355  8 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_rawmidi            30144  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
rtl8188ee              89601  0 
rtl_pci                26690  1 rtl8188ee
rtsx_pci_ms            18151  0 
rtlwifi                63475  2 rtl_pci,rtl8188ee
hp_wmi                 14062  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
sparse_keymap          13948  1 hp_wmi
memstick               16966  1 rtsx_pci_ms
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
k10temp                13126  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
i2c_piix4              22155  0 
snd_timer              29482  2 snd_pcm,snd_seq
mac80211              626489  3 rtl_pci,rtlwifi,rtl8188ee
snd                    69238  27 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
fglrx                8085343  92 
cfg80211              484040  2 mac80211,rtlwifi
soundcore              12680  1 snd
amd_iommu_v2           19054  1 fglrx
wmi                    19177  1 hp_wmi
hp_accel               26012  0 
video                  19476  0 
lis3lv02d              20156  1 hp_accel
input_polldev          13896  1 lis3lv02d
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
rtsx_pci_sdmmc         23274  0 
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25819  3 
r8169                  67581  0 
libahci                32168  1 ahci
mii                    13934  1 r8169



```




5. Your /var/log/Xorg.0.log file:
```
http://paste.ubuntu.com/7300228/

```

Thanks again!

---

### Post by Toz on 2014-04-21
_@charles.figura_, Can you follow the "Temporarily Add a Kernel Boot Parameter for Testing" from the [Kernel Boot Parameters wiki]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") to boot with the **video.use_native_backlight=1** kernel parameter? Once booted with this parameter, post back the results of those commands again and check to see if you have brightness control.

---

### Post by Toz on 2014-04-21
_@josh45_, can you remove the **acpi_backlight=vendor** kernel parameter, re-run "sudo update-grub" and reboot your computer. When rebooted, please post back the results from those commands again - lets get a baseline.

---

### Post by josh45 on 2014-04-21
Ok, no problem Toz. Here are the new results. Thanks for your help!

My brightness is actually changing now. I changed the driver for my graphics card under alternative drivers in the settings manager to a proprietary one (for a different reason - I couldn't get my computer to recognise that I had plugged a TV in the HDMI slot).
However, the problem now is that whenever I press the brightness up/down button, three or four "Display" settings windows will pop up. I have taken a screenshot of the window that pops up and attached it to this post. 

1. Your current kernel boot line:
```
 BOOT_IMAGE=/vmlinuz-3.13.0-24-generic.efi.signed root=/dev/mapper/xubuntu--vg-root ro nomodeset



```
2. Information about your video card(s):
```
 00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8610G]
    Subsystem: Hewlett-Packard Company Device 216c
    Kernel driver in use: fglrx_pci



```




3. Information about your known backlight interfaces:
```
  /sys/class/backlight/acpi_video0
9
10
8


 /sys/class/backlight/acpi_video1
8
10
8



```




4. A listing of your loaded kernel modules:
```
 Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69160  4 
bluetooth             395423  10 bnep,rfcomm
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
joydev                 17381  0 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
arc4                   12608  2 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
psmouse               102222  0 
serio_raw              13462  0 
rtsx_pci_ms            18151  0 
memstick               16966  1 rtsx_pci_ms
snd_hda_codec_realtek    61438  1 
snd_hda_codec_hdmi     46207  1 
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
k10temp                13126  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
rtl8188ee              89601  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
i2c_piix4              22155  0 
rtl_pci                26690  1 rtl8188ee
rtlwifi                63475  2 rtl_pci,rtl8188ee
snd_timer              29482  2 snd_pcm,snd_seq
mac80211              626489  3 rtl_pci,rtlwifi,rtl8188ee
snd                    69238  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cfg80211              484040  2 mac80211,rtlwifi
fglrx                8085343  87 
soundcore              12680  1 snd
amd_iommu_v2           19054  1 fglrx
wmi                    19177  1 hp_wmi
video                  19476  0 
hp_accel               26012  0 
lis3lv02d              20156  1 hp_accel
input_polldev          13896  1 lis3lv02d
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
rtsx_pci_sdmmc         23274  0 
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25819  3 
r8169                  67581  0 
libahci                32168  1 ahci
mii                    13934  1 r8169



```





5. Your /var/log/Xorg.0.log file:
```
 http://paste.ubuntu.com/7301127/



```

---

### Post by Toz on 2014-04-21
@josh45,
> However, the problem now is that whenever I press the brightness up/down button, three or four "Display" settings windows will pop up. I have taken a screenshot of the window that pops up and attached it to this post. 
Sounds like the keyboard mapping is wrong. 
What is the make and model of your laptop?
Also, do these commands affect brightness:
```
xdotool key XF86MonBrightnessUp
xdotool key XF86MonBrightnessDown
```
...note: you'll need to install the xdotool package to get them to work:
```
sudo apt-get install xdotool
```

---

### Post by josh45 on 2014-04-21
I have a HP Pavilion 15 n268sa. 

Yep, those terminal commands work fine without the display window popping up. How do I change the keyboard mapping?

Cheers Toz

---

### Post by Toz on 2014-04-21
> **josh45 said:**
> Yep, those terminal commands work fine without the display window popping up. How do I change the keyboard mapping?
Try this. Go to Settings Manager -> Keyboard -> Application Shortcuts, and click on the "Add" button.
For the command, enter:
```
bash -c 'xdotool key XF86MonBrightnessUp'
```
...click "Okay" and at the next prompt, press the Function+Brightness Up key combination.

Repeat for Function+Brightness Down key combination, but instead use this command:
```
bash -c 'xdotool key XF86MonBrightnessDown'
```

Test to see if it works.

---

### Post by josh45 on 2014-04-21
Ok, just did that but the "Display" windows still pops up when I press the buttons

---

### Post by Toz on 2014-04-21
> **josh45 said:**
> Ok, just did that but the "Display" windows still pops up when I press the buttons

Have a look at [this post]("http://ubuntuforums.org/showthread.php?t=2185305"). It details out a method to help remap the keyboard keys using xbindkeys and xbindkeys-config. Start with Step 2 (we've already determined the commands that will adjust brightness) to create the key bindings. See if that helps.

---

### Post by charles.figura on 2014-04-21
Toz - thanks for your continued help!  Sadly, no joy - still no control of the backlight.  

$ cat /proc/cmdline
```
BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=c22cd571-aa0e-4ce3-ad2f-8a14f53fc0c7 ro quiet splash vt.handoff=7 video.use_native_backlight=1

```
$ lspci -k | grep -iA2 VGA
```
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [Quadro NVS 4200M] (rev a1)
        Subsystem: Lenovo Device 21ce
        Kernel driver in use: nvidia

```
$ for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done

```
 /sys/class/backlight/acpi_video0
0
15
0

```
$ lsmod```

Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
cuse                   13445  3 
hidp                   23870  0 
hid                   106148  1 hidp
joydev                 17381  0 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   451511  0 
bnep                   19624  2 
rfcomm                 69160  12 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
uvcvideo               80885  0 
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel                                                                    
videobuf2_vmalloc      13216  1 uvcvideo                                                                       
ablk_helper            13597  1 aesni_intel                                                                    
videobuf2_memops       13362  1 videobuf2_vmalloc                                                              
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper                                    
btusb                  32412  0                                                                                
videobuf2_core         40664  1 uvcvideo                                                                       
bluetooth             395423  23 bnep,hidp,btusb,rfcomm                                                        
videodev              134688  2 uvcvideo,videobuf2_core                                                        
arc4                   12608  2                                                                                
psmouse               102222  0                                                                                
iwldvm                232285  0                                                                                
serio_raw              13462  0 
snd_hda_codec_hdmi     46207  1 
mac80211              626489  1 iwldvm
iwlwifi               169932  1 iwldvm
nvidia              10675249  42 
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
binfmt_misc            17468  1 
thinkpad_acpi          80817  1 
nvram                  14411  1 thinkpad_acpi
snd_hda_codec_conexant    57441  1 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_intel          52355  10 
snd_rawmidi            30144  1 snd_seq_midi
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
drm                   302817  2 nvidia
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
mac_hid                13205  0 
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  32 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
mei_me                 18627  0 
mei                    82274  1 mei_me
lpc_ich                21080  0 
soundcore              12680  1 snd
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
mmc_block              35929  0 
firewire_ohci          40409  0 
e1000e                254433  0 
firewire_core          68769  1 firewire_ohci
ahci                   25819  2 
crc_itu_t              12707  1 firewire_core
ptp                    18933  1 e1000e
sdhci_pci              23172  0 
libahci                32168  1 ahci
pps_core               19382  1 ptp
sdhci                  43015  1 sdhci_pci
wmi                    19177  0 
video                  19476  0 
```
cfigura@nightfall:~$ pastebinit /var/log/Xorg.0.log
[HTML]http://paste.ubuntu.com/7304179/[/HTML]

---

### Post by Toz on 2014-04-22
@charles.figura,
The first thing to try would be to add:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the "Device" section of your /etc/X11/xorg.conf file. Log out and in again to test.

----------

If that doesn't work, you noted earler that you are using a newer version of the nvidia drivers (ones not provided by ubuntu). Is there a reason why?

I would suggest first trying the nouveau drivers and the officially supported nvidia drivers to see if backlight works with them. If so, it may be a bug with the newer nvidia drivers.

---

### Post by charles.figura on 2014-04-22
Hmm... I don't *have* an xorg.conf, and haven't had one in a couple years now.  I don't know how kubuntu has been storing the video configuration, but it hasn't been using xorg.conf!

Hmmm.... I switched to the nvidia drivers instead of nouveau because there was another problem - either GL wasn't working, or... there was a conflict with some graphics-intensive software that I use - a problem with a library or module that causing the software to crash.

---

### Post by Toz on 2014-04-22
> **charles.figura said:**
> Hmm... I don't *have* an xorg.conf, and haven't had one in a couple years now.  I don't know how kubuntu has been storing the video configuration, but it hasn't been using xorg.conf!
Its using X determined defaults. You should be able to override them or add to them by, with root privileges, creating the file **/usr/share/X11/xorg.conf.d/20nvidia.conf** and add in the following content:
```
Section "Device"
        Identifier "Nvidia Card"
        Driver "nvidia"
        VendorName "NVIDIA Corporation"
        Option "NoLogo" "true"
        Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```
...and log out and in again to test. If something goes wrong, simply delete that file and reboot to get back to where you are now.

---

### Post by charles.figura on 2014-04-23
Toz -
Thank you!  The 20nvidia.conf file that you suggested has done the trick: I now have backlight brightness control!  For my sake, I'd mark this as 'solved', but since Josh45 still looks as if his issue is open, I'll leave it be.

Thanks very much for your help!

---

### Post by Toz on 2014-04-23
> **charles.figura said:**
> Toz -
Thank you!  The 20nvidia.conf file that you suggested has done the trick: I now have backlight brightness control!  For my sake, I'd mark this as 'solved', but since Josh45 still looks as if his issue is open, I'll leave it be.

Thanks very much for your help!

Cool. It still works. This is good to know. Thanks for posting back that it worked.

---

