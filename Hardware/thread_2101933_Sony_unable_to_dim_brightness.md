---
title: "Sony unable to dim brightness"
date: 2013-01-05
forum: Hardware
---

### Post by souliers on 2013-01-05
Hi Guys,

My first thread here tonight after trying numerous options to restore the screen brightness control.  I find the slider to reduce brightness but it would not work.

I tried to add 
acpi_backlight=vendor into the grub 
no success.

When checking
sudo gedit /etc/X11/xorg.conf
I get a blank file so other options could not be tried.


Would greatly appreciate to find anyone who can help me on this one!


Setup:
Sony Vaio VPCS11C5E, Ubunti 12.10
NVIDIA binary Xorg driver, kernel module and VDPAU library
 - for GT218(GeForce310M)

---

### Post by NikTh on 2013-01-05
Hi souliers, 

various options for kernel (via grub) exist. 
Try also **acpi_osi=** and see if works. Do not forget to update grub when you add the parameter. 

If not works , then give the results of ```
ls /sys/class/backlight/*/
``` _Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [**See here how**]("http://i.stack.imgur.com/zADbK.png")


Thanks

---

### Post by souliers on 2013-01-05
Hi NikTh,

Thanks for your quick reply!

1)  I tried **acpi_osi=**  updated the grub, restarted - no change

2)  Reversed changes to grub, updated, restarted


My results are:

```
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type
```

---

### Post by NikTh on 2013-01-06
Hi , 
please post the full output (do not cut) . A path is missing here, what is it ? 
```
/sys/class/backlight/**acpi_video0 **
```or something else ? 

Also give full results of ```
lsmod
``` so we can see if **sony-laptop** module is loaded.
Thanks

---

### Post by souliers on 2013-01-06
Good morning,

I tried both codes:

```
ls /sys/class/backlight/*/
```

```
ls /sys/class/backlight/acpi_video0
```

The results I get are the same:

```
@ubuntu:~$ ls /sys/class/backlight/acpi_video0
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type
@ubuntu:~$ 
```


What do you mean with something is missing here?  Am completely new to Ubunto so need a leading hand...


Results of lsmod as follows:

```
Module                  Size  Used by
snd_hda_codec_hdmi     32007  4 
snd_hda_codec_realtek    78045  1 
snd_hda_intel          33491  5 
coretemp               13400  0 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
arc4                   12529  2 
kvm_intel             132759  0 
snd_hwdep              13602  1 snd_hda_codec
kvm                   414070  1 kvm_intel
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
iwlwifi               386826  0 
parport_pc             32688  0 
snd_seq_midi           13324  0 
uvcvideo               76749  0 
ppdev                  17073  0 
snd_rawmidi            30512  1 snd_seq_midi
lp                     17759  0 
snd_seq_midi_event     14899  1 snd_seq_midi
videobuf2_core         32851  1 uvcvideo
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
ghash_clmulni_intel    13180  0 
videodev              120309  2 uvcvideo,videobuf2_core
joydev                 17457  0 
parport                46345  3 parport_pc,ppdev,lp
bnep                   18140  2 
rfcomm                 46619  0 
aesni_intel            51037  2 
snd_timer              29425  2 snd_pcm,snd_seq
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
mac80211              539908  1 iwlwifi
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
videobuf2_vmalloc      12860  1 uvcvideo
bluetooth             209199  10 bnep,rfcomm
psmouse                95552  0 
snd                    78734  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    40690  0 
videobuf2_memops       13368  1 videobuf2_vmalloc
aes_x86_64             17208  1 aesni_intel
mxm_wmi                12979  0 
soundcore              15047  1 snd
mac_hid                13205  0 
sony_laptop            76908  1 
intel_ips              18243  0 
wmi                    19070  1 mxm_wmi
video                  19335  0 
serio_raw              13215  0 
microcode              22803  0 
nvidia              11257759  43 
lpc_ich                17061  0 
cfg80211              206566  2 iwlwifi,mac80211
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
firewire_ohci          40401  0 
firewire_core          64368  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
atl1c                  41101  0 
sdhci_pci              18616  0 
sdhci                  32645  1 sdhci_pci
```

---

### Post by NikTh on 2013-01-06
> **souliers said:**
> What do you mean with something is missing here?  Am completely new to Ubunto so need a leading hand...
Compare the following results and you will see what is missing. 
> **souliers said:**
> My results are:
```
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type
```
> **souliers said:**
> 
The results I get are the same:
```
@ubuntu:~$ ls /sys/class/backlight/acpi_video0
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type
@ubuntu:~$ 
```

Lets try something with the modules.. 

Execute the commands below with order and post back the results 
```
sudo modprobe -rvf mxm_wmi
sudo modprobe -rvf wmi
sudo modprobe -rvf sony-laptop
``` 

Thanks

---

### Post by souliers on 2013-01-06
Ok, got it :)

so, results following in the same order as the commands:


```
@ubuntu:~$ sudo modprobe -rvf mxm_wmi
[sudo] password for sebastian: 
rmmod /lib/modules/3.5.0-21-generic/kernel/drivers/platform/x86/mxm-wmi.ko
rmmod /lib/modules/3.5.0-21-generic/kernel/drivers/platform/x86/wmi.ko
```


```
sebastian@ubuntu:~$ sudo modprobe -rvf wmi
[sudo] password for sebastian: 
sebastian@ubuntu:~$ 
```


```

sebastian@ubuntu:~$ sudo modprobe -rvf sony-laptop
[sudo] password for sebastian: 
```
  


Strange thing is that with "modprobe -rvf wmi"  I typed the pasword but then nothing really happened.

Same story with "modprobe -rvf sony-laptop", after typing the password I do not even get the usual command line back.  Seems it triggers a process but does not show results as while closing the terminal it prompts me:  a process is still running, are you sure to close terminal?


Hope I did not miss anything this time..

---

### Post by NikTh on 2013-01-06
Now give the results of 
```
lsmod | egrep 'wmi|sony'
```Thanks

---

### Post by souliers on 2013-01-06
here you go:


```
sebastian@ubuntu:~$ lsmod | egrep 'wmi|sony'
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sony_laptop            76908  1 
sebastian@ubuntu:~$ 
```

---

### Post by NikTh on 2013-01-06
I cannot see and I cannot understand what module uses the sony-laptop module. 
sony-laptop as I can read (modinfo) depends from rfkill module , but rfkill is not listed in your modules list. 

Anyway , lets try something else , but you have to reboot your system. 
```
echo "options sony-laptop kbd_backlight=1" | sudo tee /etc/modprobe.d/sony-laptop.conf
```

Then reboot and see if brightness keys works.. 
If not , try below command
```
sudo modprobe -rvf mxm_wmi
``` 
and try again the keys. 
Thanks

---

### Post by souliers on 2013-01-06
Hi Nik,

tried both but no change.  Got following codes:


```
sebastian@ubuntu:~$ echo "options sony-laptop kbd_backlight=1" | sudo tee /etc/modprobe.d/sony-laptop.conf
[sudo] password for sebastian: 
options sony-laptop kbd_backlight=1
sebastian@ubuntu:~$ 
```


```
sebastian@ubuntu:~$ sudo modprobe -rvf mxm_wmi
[sudo] password for sebastian: 
rmmod /lib/modules/3.5.0-21-generic/kernel/drivers/platform/x86/mxm-wmi.ko
rmmod /lib/modules/3.5.0-21-generic/kernel/drivers/platform/x86/wmi.ko
sebastian@ubuntu:~$ 
```


Do you think it has something to do with the graphic card drivers?

---

### Post by NikTh on 2013-01-06
Well , the problem (as the title correct emphasize , **Yet**) is known , but I don't know a permanent fix. 

Usually for such problems responsible is the ACPI. 

Now to revert back to original state , remove the file we added in /modprobe.d/ 
```
sudo rm /etc/modprobe.d/sony-laptop.conf
```and lets examine the acpi_video0. 

Give the results ```
cat /sys/class/backlight/acpi_video0/brightness
cat /sys/class/backlight/acpi_video0/actual_brightness
cat /sys/class/backlight/acpi_video0/max_brightness
```

---

### Post by souliers on 2013-01-06
indeed, most solutions need to be tailor made, so am very happy you are taking on this challenge :)

Results as follows:

```
@ubuntu:~$ cat /sys/class/backlight/acpi_video0/brightness
0
@ubuntu:~$ cat /sys/class/backlight/acpi_video0/actual_brightness
0
@ubuntu:~$ cat /sys/class/backlight/acpi_video0/max_brightness
8
@ubuntu:~$ 
```

---

### Post by Toz on 2013-01-06
If I my interject...

You might want want to give **nvidiabl** a try (info here: [https://github.com/guillaumezin/nvidiabl]("https://github.com/guillaumezin/nvidiabl"), downloadable deb here: [https://github.com/guillaumezin/nvidiabl/downloads]("https://github.com/guillaumezin/nvidiabl/downloads")). According to the nvidiabl-laptops.h file, your system is supported:
> NVIDIABL_DECLARE_LAPTOP_MODEL("Sony Corporation", "VGN-AW11", PCI_ANY_ID, NVIDIABL_AUTO, NVIDIABL_AUTO, NVIDIABL_AUTO),
NVIDIABL_DECLARE_LAPTOP_MODEL("Sony Corporation", "VGN-AW290J", PCI_ANY_ID, NVIDIABL_AUTO, NVIDIABL_AUTO, NVIDIABL_AUTO),
NVIDIABL_DECLARE_LAPTOP_MODEL("Sony Corporation", "VGN-FZ11", PCI_ANY_ID, NVIDIABL_AUTO, NVIDIABL_AUTO, NVIDIABL_AUTO),
NVIDIABL_DECLARE_LAPTOP_MODEL("Sony Corporation", "VGN-FZ31", PCI_ANY_ID, NVIDIABL_AUTO, NVIDIABL_AUTO, NVIDIABL_AUTO),
NVIDIABL_DECLARE_LAPTOP_MODEL("Sony Corporation", "VGN-FZ38", PCI_ANY_ID, NVIDIABL_AUTO, NVIDIABL_AUTO, NVIDIABL_AUTO),
NVIDIABL_DECLARE_LAPTOP_MODEL("Sony Corporation", "VPCCW1", PCI_ANY_ID, NVIDIABL_AUTO, NVIDIABL_AUTO, 0x1FFFF),
NVIDIABL_DECLARE_LAPTOP_MODEL("Sony Corporation", "VPCCW2", PCI_ANY_ID, NVIDIABL_AUTO, NVIDIABL_AUTO, 0x1FFFF),
[COLOR="Red"]NVIDIABL_DECLARE_LAPTOP_MODEL("Sony Corporation", "VPCS1", PCI_ANY_ID, NVIDIABL_AUTO, NVIDIABL_AUTO, 0x679a),[/COLOR]
NVIDIABL_DECLARE_LAPTOP_MODEL("Sony Corporation", "VGN-S560", PCI_ANY_ID, NVIDIABL_AUTO, NVIDIABL_AUTO, NVIDIABL_AUTO),
NVIDIABL_DECLARE_LAPTOP_MODEL("Sony Corporation", "VPCF1", PCI_ANY_ID, NVIDIABL_AUTO, NVIDIABL_AUTO, NVIDIABL_AUTO),

This package will expose an nvidia_backlight interface that can be manipulated. You can then use a script like obacklight ([http://dev.osource.se/software/obacklight/]("http://dev.osource.se/software/obacklight/")) to manipulate the interface or just tweak the acpi scripts (something like [http://ubuntuforums.org/showpost.php?p=12357584&postcount=29]("http://ubuntuforums.org/showpost.php?p=12357584&postcount=29")).

---

### Post by souliers on 2013-01-06
Hi Toz,

All interjections are very welcome, thanks!

I tried **nvidiabl** had a successful installation but that's about it.  Codes came out as follows:

```
sebastian@ubuntu:~$ sudo dkms ldtarball --archive=nvidiabl-0.80-source-only.dkms.tar.gz build install

Loading tarball for nvidiabl-0.80

DKMS: ldtarball completed.

Creating symlink /var/lib/dkms/nvidiabl/0.80/source ->
                 /usr/src/nvidiabl-0.80

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.5.0-21-generic -C /lib/modules/3.5.0-21-generic/build SUBDIRS=/var/lib/dkms/nvidiabl/0.80/build modules.....
cleaning build area....

DKMS: build completed.

nvidiabl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-21-generic/updates/dkms/

/etc/modprobe.d/dkms.conf: added '# Prevent conflicts with nvidiabl'
/etc/modprobe.d/dkms.conf: added 'blacklist nvidia_bl'
/etc/modprobe.d/dkms.conf: added 'blacklist nvbacklight'
/etc/modprobe.d/dkms.conf: added 'blacklist mbp_nvidia_bl'
/etc/modprobe.d/dkms.conf: added '# End of entries added for nvidiabl'
depmod.......

DKMS: install completed.
```



Then I tried your tweak  [http://ubuntuforums.org/showpost.php...4&postcount=29]("http://ubuntuforums.org/showpost.php?p=12357584&postcount=29") but still no change:

```
sebastian@ubuntu:~$ gksu gedit /etc/acpi/events/sony-brightness-up
sebastian@ubuntu:~$ gksu gedit /etc/acpi/events/sony-brightness-down
sebastian@ubuntu:~$ gksu gedit /etc/acpi/brightdown.sh
sebastian@ubuntu:~$ gksu gedit /etc/acpi/brightup.sh
sebastian@ubuntu:~$ sudo chmod +x /etc/acpi/events/sony-brightness-up
sebastian@ubuntu:~$ sudo chmod +x /etc/acpi/events/sony-brightness-down
sebastian@ubuntu:~$ sudo chmod +x /etc/acpi/brightdown.sh
sebastian@ubuntu:~$ sudo chmod +x /etc/acpi/brightup.sh
sebastian@ubuntu:~$ sudo service acpid restart
acpid stop/waiting
acpid start/running, process 5024
```


After that I tried the last option, [http://dev.osource.se/software/obacklight/](http://dev.osource.se/software/obacklight/), but somehow fear I did that one in a wrong way.  How can I check if obacklight had been activated properly?  how can I edit the settings?

---

### Post by Toz on 2013-01-06
Can you post back the results of the following command:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```

---

### Post by souliers on 2013-01-06
Here you go:

```
sebastian@ubuntu:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
3
3
8
/sys/class/backlight/nvidia_backlight
611
610
127
sebastian@ubuntu:~$ 
```

---

### Post by Toz on 2013-01-06
Do an of the following commands affect the brightness:
```

echo 10 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
echo 64 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
echo 127 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
echo 400 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```

---

### Post by souliers on 2013-01-07
Hi Toz,

sorry for replying late, had to wait until work was over...

Results are:

echo 10 = no reaction, terminal hangs

echo 64 = brightness reduced, felt like 50% of the full brightness

echo 127 = brightness increased a little more than felt 50% - Ubuntu asking for Password to confirm execution


 
echo 400 =

```
sebastian@ubuntu:~$ echo 400 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
400
tee: /sys/class/backlight/nvidia_backlight/brightness: Das Argument ist ungültig
sebastian@ubuntu:~$ 
```For better understanding:  "Das Argument ist ungültig" means "the argument is not valid"

I observed that the slider for brightness remains at maximum.

---

### Post by Calinou on 2013-01-07
Edit /etc/rc.local with a text editor with administrator privileges:
```
gksudo gedit /etc/rc.local
```

Before the "exit 0" line, add this:
```
echo N > /sys/class/backlight/acpi_video0/brightness
```

**N** is a value between 0 and 10. Higher is brighter. Default is 10.

Save and reboot.
???
PROFIT (this is actually valid here, saves electicity!)

---

### Post by souliers on 2013-01-07
Hi Calinou,

tried and amended my rc.local as follows:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo 3 > /sys/class/backlight/acpi_video0/brightness
exit 0
```


No results upon restart, brightness at 100%

---

### Post by Toz on 2013-01-07
> **souliers said:**
> Hi Calinou,

tried and amended my rc.local as follows:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo 3 > /sys/class/backlight/acpi_video0/brightness
exit 0
```


No results upon restart, brightness at 100%

This won't work for you since you're acpi_video0 interface is not a valid one. Can you please remove those commands from your /etc/rc.local file.

Whats interesting, is the results that your nvidiabl interface are generating - they are not "normal".

Can you provide some further information:
```
cat /proc/cmdline
```
```
lsmod
```
```
modinfo nvidiabl
```

---

### Post by souliers on 2013-01-07
Hi Toz,

good to see you back :)  have reversed changes to /etc/rc.local file.

Results as follows:


```
sebastian@ubuntu:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-21-generic root=UUID=3C602F74602F33D4 loop=/ubuntu/disks/root.disk ro quiet splash
```



```
sebastian@ubuntu:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32007  4 
snd_hda_codec_realtek    78045  1 
snd_hda_intel          33491  7 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
arc4                   12529  2 
coretemp               13400  0 
snd_hwdep              13602  1 snd_hda_codec
iwlwifi               386826  0 
snd_pcm                96580  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
kvm_intel             132759  0 
snd_seq_midi           13324  0 
uvcvideo               76749  0 
kvm                   414070  1 kvm_intel
snd_rawmidi            30512  1 snd_seq_midi
videobuf2_core         32851  1 uvcvideo
parport_pc             32688  0 
snd_seq_midi_event     14899  1 snd_seq_midi
videodev              120309  2 uvcvideo,videobuf2_core
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
ppdev                  17073  0 
snd_timer              29425  2 snd_pcm,snd_seq
lp                     17759  0 
ghash_clmulni_intel    13180  0 
mac80211              539908  1 iwlwifi
joydev                 17457  0 
aesni_intel            51037  2 
videobuf2_vmalloc      12860  1 uvcvideo
bnep                   18140  2 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
parport                46345  3 parport_pc,ppdev,lp
rfcomm                 46619  0 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
videobuf2_memops       13368  1 videobuf2_vmalloc
snd                    78734  23 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    40690  0 
bluetooth             209199  10 bnep,rfcomm
psmouse                95552  0 
aes_x86_64             17208  1 aesni_intel
nvidiabl               40764  0 
soundcore              15047  1 snd
mxm_wmi                12979  0 
nvidia              11257759  43 
lpc_ich                17061  0 
cfg80211              206566  2 iwlwifi,mac80211
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
intel_ips              18243  0 
wmi                    19070  1 mxm_wmi
sony_laptop            76908  1 
mac_hid                13205  0 
video                  19335  0 
serio_raw              13215  0 
microcode              22803  0 
firewire_ohci          40401  0 
firewire_core          64368  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18616  0 
sdhci                  32645  1 sdhci_pci
atl1c                  41101  0 
```



```

sebastian@ubuntu:~$ modinfo nvidiabl
filename:       /lib/modules/3.5.0-21-generic/updates/dkms/nvidiabl.ko
license:        GPL
description:    Nvidia-based graphics adapter backlight driver
author:         Mario Schwalbe <schwalbe@inf.tu-dresden.de>, Guillaume Zin <guillaume.zin@gmail.com>
srcversion:     2E4C7A42B8A279EE8310AFD
alias:          dmi*:svn*Hewlett-Packard*:pn*HPPaviliondv3500NotebookPC*:
alias:          dmi*:svn*Acer*:pn*TravelMate8481TG*:
alias:          dmi*:svn*FUJITSU*:pn*AMILOPi3560*:
alias:          dmi*:svn*Quanta*:pn*TW9*:
alias:          dmi*:svn*Compal*:pn*PBL01*:
alias:          dmi*:svn*ASUSTeKComputerInc.*:pn*G55VW*:
alias:          dmi*:svn*ASUSTeKComputerInc.*:pn*G74Sx*:
alias:          dmi*:svn*LGElectronics*:pn*R580-K.AHC4WA9*:
alias:          dmi*:svn*LGElectronics*:pn*R590-K.BE52P1*:
alias:          dmi*:svn*LGElectronics*:pn*R590-P.BN58P1*:
alias:          dmi*:svn*LENOVO*:pn*42844MG*:
alias:          dmi*:svn*LENOVO*:pn*4270CTO*:
alias:          dmi*:svn*LENOVO*:pn*4313CTO*:
alias:          dmi*:svn*AppleInc.*:pn*MacBookAir3,2*:
alias:          dmi*:svn*AppleInc.*:pn*MacBookAir3,1*:
alias:          dmi*:svn*AppleInc.*:pn*MacBookAir2,1*:
alias:          dmi*:svn*AppleInc.*:pn*MacBookPro7,1*:
alias:          dmi*:svn*AppleInc.*:pn*MacBookPro5,5*:
alias:          dmi*:svn*AppleInc.*:pn*MacBookPro5,4*:
alias:          dmi*:svn*AppleInc.*:pn*MacBookPro5,2*:
alias:          dmi*:svn*AppleInc.*:pn*MacBookPro4,1*:
alias:          dmi*:svn*AppleInc.*:pn*MacBookPro3,2*:
alias:          dmi*:svn*AppleInc.*:pn*MacBookPro3,1*:
alias:          dmi*:svn*AppleInc.*:pn*MacBook7,1*:
alias:          dmi*:svn*AppleInc.*:pn*MacBook6,1*:
alias:          dmi*:svn*AppleInc.*:pn*MacBook5,2*:
alias:          dmi*:svn*AppleInc.*:pn*MacBook5,1*:
alias:          dmi*:svn*TOSHIBA*:pn*SATELLITEL750*:
alias:          dmi*:svn*TOSHIBA*:pn*SATELLITEPROU500*:
alias:          dmi*:svn*SAMSUNGELECTRONICSCO.,LTD.*:pn*RV409/RV509/RV709*:
alias:          dmi*:svn*SAMSUNGELECTRONICSCO.,LTD.*:pn*R510/P510*:
alias:          dmi*:svn*SAMSUNGELECTRONICSCO.,LTD.*:pn*Q430/Q530*:
alias:          dmi*:svn*SAMSUNGELECTRONICSCO.,LTD.*:pn*SR70S/SR71S*:
alias:          dmi*:svn*SAMSUNGELECTRONICSCO.,LTD.*:pn*N510*:
alias:          dmi*:svn*DellInc.*:pn*Vostro3500*:
alias:          dmi*:svn*DellInc.*:pn*Vostro3400*:
alias:          dmi*:svn*DellInc.*:pn*Inspiron1370*:
alias:          dmi*:svn*SonyCorporation*:pn*VPCF1*:
alias:          dmi*:svn*SonyCorporation*:pn*VGN-S560*:
alias:          dmi*:svn*SonyCorporation*:pn*VPCS1*:
alias:          dmi*:svn*SonyCorporation*:pn*VPCCW2*:
alias:          dmi*:svn*SonyCorporation*:pn*VPCCW1*:
alias:          dmi*:svn*SonyCorporation*:pn*VGN-FZ38*:
alias:          dmi*:svn*SonyCorporation*:pn*VGN-FZ31*:
alias:          dmi*:svn*SonyCorporation*:pn*VGN-FZ11*:
alias:          dmi*:svn*SonyCorporation*:pn*VGN-AW290J*:
alias:          dmi*:svn*SonyCorporation*:pn*VGN-AW11*:
depends:        
vermagic:       3.5.0-21-generic SMP mod_unload modversions 
parm:           model:backlight model, must be empty for autodetection, nv4x or nv5x (charp)
parm:           type:Backlight type (raw|platform|firmware) default is raw (string)
parm:           off:value to put in the register to disable the backlight, negative value is interpreted as percentage of maximum, -101 for default, autodetect otherwise (long)
parm:           min:minimum register value for the backlight, negative value is interpreted as percentage of maximum, -101 for default, autodetect otherwise (long)
parm:           max:maximum register value for the backlight, -101 for default, autodetect otherwise (long)
parm:           pci_id:PCI ID of the Nvidia card - usefull only when not using autodetection and more than one Nvidia PCI device (ulong)
sebastian@ubuntu:~$ 
```

---

### Post by Toz on 2013-01-07
Let's try some module parameters to see if we can get it to work properly. After each attempt, post back the results of:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```
...and whether the following commands adjust the brightness:
```
echo 10 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
echo 64 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
echo 127 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
echo 400 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```

We are going to unload the nvidiabl module and reload it with a set of parameters to test. Here are the test parameters:
[LIST=1]
[*]```
sudo modprobe -r nvidiabl && sudo modprobe nvidiabl type=firmware
```
[*]```
sudo modprobe -r nvidiabl && sudo modprobe nvidiabl type=platform
```
[*]```
sudo modprobe -r nvidiabl && sudo modprobe nvidiabl max=100
```
[*]```
sudo modprobe -r nvidiabl && sudo modprobe nvidiabl min=1 max=100
```
[/LIST]

BTW, is this a wubi install?

---

### Post by souliers on 2013-01-09
sorry for the delay, had to follow my other work for some time. 

Yes, it has been a WUBI install as I could not figure out the partitioning while attempting to install from a USB, feared to wipe out my windows installation and details of existing partitions were somewhat different what I know from Partion Magic or other programs.  Is there any guideline on that part?


Here are the results:


```
sebastian@ubuntu:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
8
8
8
/sys/class/backlight/nvidia_backlight
127
127
127
sebastian@ubuntu:~$ 
```



```
sebastian@ubuntu:~$ echo 10 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
[sudo] password for sebastian: 
10
sebastian@ubuntu:~$ 
```
 
= decreasing brightness to a very low level




```
sebastian@ubuntu:~$ echo 64 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
64
sebastian@ubuntu:~$ 
```

= increasing the brightness a little from the previous level



```
sebastian@ubuntu:~$ echo 127 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
127
sebastian@ubuntu:~$ 
```

= increasing brightness even more



```
sebastian@ubuntu:~$ echo 400 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
400
tee: /sys/class/backlight/nvidia_backlight/brightness: Das Argument ist ungültig
sebastian@ubuntu:~$ 
```

= no reaction, Ubuntu saying the argument is invalid




```
sebastian@ubuntu:~$ sudo modprobe -r nvidiabl && sudo modprobe nvidiabl type=firmware
sebastian@ubuntu:~$ 
```

= full brightness restored



```
sebastian@ubuntu:~$ sudo modprobe -r nvidiabl && sudo modprobe nvidiabl type=platform
sebastian@ubuntu:~$ 
```

= no reaction


```

sebastian@ubuntu:~$ sudo modprobe -r nvidiabl && sudo modprobe nvidiabl max=100
sebastian@ubuntu:~$ 
```

= no reaction



```
sebastian@ubuntu:~$ sudo modprobe -r nvidiabl && sudo modprobe nvidiabl min=1 max=100
sebastian@ubuntu:~$ 
```

= no reaction

---

### Post by Toz on 2013-01-09
Interesting. Reboot the computer and try this again:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```

1. Is the brightness at full?

2. Run:
```
echo 10 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```
...is the brightness low?

3. Run:
```
echo 64 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```
...is brightness at about half?

4. Run:
```
echo 127 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```
...is brightness at full again?

We seem to be getting contradictory results. Lets see if this returns what I expect it will.

---

### Post by souliers on 2013-01-10
So, here we go:

```
sebastian@ubuntu:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
8
8
8
/sys/class/backlight/nvidia_backlight
611
610
127
sebastian@ubuntu:~$ 
```


1) Brigtness is at full power


2)
```
sebastian@ubuntu:~$ echo 10 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
[sudo] password for sebastian: 
10
sebastian@ubuntu:~$ 

```

= Brightness is very low, feels like lowest setting


3)
```
sebastian@ubuntu:~$ echo 64 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
64
sebastian@ubuntu:~$ 
```

=  Yes, brightness is about half


4)
```
sebastian@ubuntu:~$ echo 127 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
127
sebastian@ubuntu:~$ 
```

=  No, brightness is not as bright as before starting the tests, maybe around 75-85%

---

### Post by Toz on 2013-01-10
Now, can you try:
```
sudo modprobe -r nvidiabl && sudo modprobe nvidiabl type=firmware
```
...then:
```

for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```
1. Is the brightness at full?

2. Run:
```

echo 10 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```
...is the brightness low?

3. Run:
```

echo 64 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```
...is brightness at about half?

4. Run:
```

echo 127 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```
...is brightness at full again?

Edit:
Can you also post back the results of:
```
ps -ef | grep -i backlight
```

---

### Post by souliers on 2013-01-11
I restarted the system, opened the terminal and started.  As I do not have a proper reference indicating at which brightness level the display is set, the only reference I have is immediately after restarting as then the brightness is at full beam.


```
sebastian@ubuntu:~$ sudo modprobe -r nvidiabl && sudo modprobe nvidiabl type=firmware
[sudo] password for sebastian: 
sebastian@ubuntu:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
8
8
8
/sys/class/backlight/nvidia_backlight
611
610
127
```

=  Brightness full


```
sebastian@ubuntu:~$ echo 10 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
10
```

=  brightness very low


```
sebastian@ubuntu:~$ echo 64 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
64
```

=  yes, brightness about half


```
sebastian@ubuntu:~$ echo 127 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
127

```

= no, brightness about 70-80%


And the remaining results:

```
sebastian@ubuntu:~$ ps -ef | grep -i backlight
1000      2511  2426  0 21:56 pts/2    00:00:00 grep --color=auto -i backlight
sebastian@ubuntu:~$ 
```

---

### Post by Toz on 2013-01-11
Lets keep going. Try this one:
```
sudo modprobe -r nvidiabl && sudo modprobe nvidiabl type=firmware min=1 max=127
```
...then:
```

for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```

1. Is the brightness at full?

2. Run:
```

echo 10 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```

...is the brightness low?

3. Run:
```

echo 64 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```

...is brightness at about half?

4. Run:
```

echo 127 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```

...is brightness at full again?

---

### Post by souliers on 2013-01-12
Keeping it going and being rewarded by a surprise:

1)
sebastian@ubuntu:~$ sudo modprobe -r nvidiabl && sudo modprobe nvidiabl type=firmware min=1 max=127
[sudo] password for sebastian:
sebastian@ubuntu:~$

= so far so good, brightness full


2)
sebastian@ubuntu:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
8
8
8
/sys/class/backlight/nvidia_backlight
123700
123699
127
sebastian@ubuntu:~$

= still all good, brightness at full


3)
echo 10 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
= after entering this I could not see anything.  Taking cover under a quilt I could iamgine some schemes but not more than that.  I had to manually shut down the computer


4)
sebastian@ubuntu:~$ echo 64 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
64
sebastian@ubuntu:~$

= the screen turned low, only under the quilt I could continue entering the codes, estimate of 5%


5)
sebastian@ubuntu:~$ echo 127 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
127
sebastian@ubuntu:~$

= the screen turned brighter, maybe to 10%, still hard to read results without using a quilt

---

### Post by Toz on 2013-01-12
What about:
```
echo 123699 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```

Does it return to full brightness?


Make sure its run with the previous commands if you've rebooted or reloaded the module.

Edit: What nvidiabl module parameters got you the results from post #25 where all there values were 127?

---

### Post by souliers on 2013-01-12
Tried the following:

1)
```
sebastian@ubuntu:~$ sudo modprobe -r nvidiabl && sudo modprobe nvidiabl type=firmware min=1 max=127
[sudo] password for sebastian: 
```

= full brightness


2)
```
sebastian@ubuntu:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
8
8
8
/sys/class/backlight/nvidia_backlight
123700
123699
127
```

= full brightness


3)
```
sebastian@ubuntu:~$ echo 127 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
127
```

= brightness very low, quilt time again


4)
```
sebastian@ubuntu:~$ echo 123699 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
123699
tee: /sys/class/backlight/nvidia_backlight/brightness: Das Argument ist ungültig
sebastian@ubuntu:~$ 
```

= no reaction, terminal saying the argument is invalid


The nvidiabl module getting me all 127 in post #25 should be the module you described in post #14 - if I am not mistaken.  I actualy believe that was not uninstalled, or did I miss it and uninstalled already with commands you suggested during the consecutive posts?  Is there a connection to the proprietary I am using?

---

### Post by Toz on 2013-01-12
Try this one again:
```
sudo modprobe -r nvidiabl && sudo modprobe nvidiabl type=platform
```

then

```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
```

---

### Post by souliers on 2013-01-12
Alright, tried below but nothing changed with brightness...


```
sebastian@ubuntu:~$ sudo modprobe -r nvidiabl && sudo modprobe nvidiabl type=platform
[sudo] password for sebastian: 
sebastian@ubuntu:~$ 
```


```
sebastian@ubuntu:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
8
8
8
/sys/class/backlight/nvidia_backlight
611
610
127
sebastian@ubuntu:~$ 
```

---

### Post by Toz on 2013-01-12
One more:
```
sudo modprobe -r nvidiabl && sudo modprobe nvidiabl type=raw
```

then

```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```

---

### Post by souliers on 2013-01-12
And here it goes:

1)
```
sebastian@ubuntu:~$ sudo modprobe -r nvidiabl && sudo modprobe nvidiabl type=raw[sudo] password for sebastian: 
sebastian@ubuntu:~$ 
```

= no change

2)
```
sebastian@ubuntu:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
8
8
8
/sys/class/backlight/nvidia_backlight
611
610
127
sebastian@ubuntu:~$ 

```

---

### Post by Toz on 2013-01-12
Hmph. Being persistent.....

```
sudo modprobe -r nvidiabl && sudo modprobe nvidiabl type=raw min=0 max=611
```

then

```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```

then

```
echo 127 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```
```
echo 610 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```

EDIT: can you also post back the results of:
```
dmesg | grep nvidiabl
```

---

### Post by souliers on 2013-01-12
I trust that in the end all will be good?!?  ;)

here we go again:

1)
```
sebastian@ubuntu:~$ sudo modprobe -r nvidiabl && sudo modprobe nvidiabl type=raw min=0 max=611
[sudo] password for sebastian: 
sebastian@ubuntu:~$ 

```

= brightness full, no change

2)
```
sebastian@ubuntu:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
8
8
8
/sys/class/backlight/nvidia_backlight
25509
25508
127
sebastian@ubuntu:~$ 
```


3)
```
sebastian@ubuntu:~$ echo 127 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
127
sebastian@ubuntu:~$ 

```

= brightness reduced, now around 20%


4)
```
sebastian@ubuntu:~$ echo 610 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
610
tee: /sys/class/backlight/nvidia_backlight/brightness: Das Argument ist ungültig
sebastian@ubuntu:~$ 

```

= terminal says argument is invalid, no change

---

### Post by Toz on 2013-01-12
```
dmesg | grep nvidiabl
```

---

### Post by souliers on 2013-01-12
```
sebastian@ubuntu:~$ dmesg | grep nvidiabl
[   16.088138] nvidiabl: loading driver version 0.80
[   16.088145] nvidiabl: Sony Corporation - VPCS1 model detected in DMI tables
[   16.088153] nvidiabl: Supported Nvidia graphics adapter 10de:0a75:104d:9069 detected
[   16.088174] nvidiabl: smartdimmer register at address 0xd261c084 mapped at address 0xffffc9000067e084
[   16.088176] nvidiabl: backlight type is raw
[   16.088218] nvidiabl: backup register value 0x4001df67
[   16.088220] nvidiabl: using value 0x679a as maximum
[   16.088221] nvidiabl: autodetecting off
[   16.088222] nvidiabl: using value 0x0 as off
[   16.088223] nvidiabl: autodetecting minimum
[   16.088224] nvidiabl: minimum is 5% of maximum
[   16.088225] nvidiabl: using value 0x52e as minimum
[   16.300189] Modules linked in: video mac_hid mxm_wmi nvidiabl(O) sony_laptop(+) wmi nvidia(PO) aes_x86_64 mac80211 videobuf2_vmalloc microcode(+) snd videobuf2_memops cfg80211 psmouse serio_raw intel_ips lpc_ich soundcore snd_page_alloc mei firewire_ohci firewire_core atl1c crc_itu_t sdhci_pci sdhci
[ 4125.178278] nvidiabl: restore register value 0x4001df67
[ 4125.194539] nvidiabl: loading driver version 0.80
[ 4125.194549] nvidiabl: Sony Corporation - VPCS1 model detected in DMI tables
[ 4125.194562] nvidiabl: Supported Nvidia graphics adapter 10de:0a75:104d:9069 detected
[ 4125.194599] nvidiabl: smartdimmer register at address 0xd261c084 mapped at address 0xffffc9000067e084
[ 4125.194603] nvidiabl: backlight type is platform
[ 4125.194681] nvidiabl: backup register value 0x4001df67
[ 4125.194685] nvidiabl: using value 0x679a as maximum
[ 4125.194688] nvidiabl: autodetecting off
[ 4125.194691] nvidiabl: using value 0x0 as off
[ 4125.194693] nvidiabl: autodetecting minimum
[ 4125.194696] nvidiabl: minimum is 5% of maximum
[ 4125.194699] nvidiabl: using value 0x52e as minimum
[ 5464.813597] nvidiabl: restore register value 0x4001df67
[ 5464.828979] nvidiabl: loading driver version 0.80
[ 5464.828988] nvidiabl: Sony Corporation - VPCS1 model detected in DMI tables
[ 5464.829000] nvidiabl: Supported Nvidia graphics adapter 10de:0a75:104d:9069 detected
[ 5464.829034] nvidiabl: smartdimmer register at address 0xd261c084 mapped at address 0xffffc9000067e084
[ 5464.829038] nvidiabl: backlight type is raw
[ 5464.829119] nvidiabl: backup register value 0x4001df67
[ 5464.829123] nvidiabl: using value 0x679a as maximum
[ 5464.829125] nvidiabl: autodetecting off
[ 5464.829128] nvidiabl: using value 0x0 as off
[ 5464.829130] nvidiabl: autodetecting minimum
[ 5464.829133] nvidiabl: minimum is 5% of maximum
[ 5464.829136] nvidiabl: using value 0x52e as minimum
[ 7754.785405] nvidiabl: restore register value 0x4001df67
[ 7754.800239] nvidiabl: loading driver version 0.80
[ 7754.800248] nvidiabl: Sony Corporation - VPCS1 model detected in DMI tables
[ 7754.800256] nvidiabl: Supported Nvidia graphics adapter 10de:0a75:104d:9069 detected
[ 7754.800285] nvidiabl: smartdimmer register at address 0xd261c084 mapped at address 0xffffc9000067e084
[ 7754.800288] nvidiabl: backlight type is raw
[ 7754.800330] nvidiabl: backup register value 0x4001df67
[ 7754.800331] nvidiabl: using value 0x263 as maximum
[ 7754.800332] nvidiabl: autodetecting off
[ 7754.800333] nvidiabl: using value 0x0 as off
[ 7754.800333] nvidiabl: using value 0x0 as minimum
sebastian@ubuntu:~$ 

```

---

### Post by Toz on 2013-01-12
```

sudo modprobe -r nvidiabl && sudo modprobe nvidiabl max=50
```

then

```

for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```

Do the following adjust brightness?
```
nvidiablctl up
nvidiablctl down
```

---

### Post by souliers on 2013-01-12
1)
```
sebastian@ubuntu:~$ sudo modprobe -r nvidiabl && sudo modprobe nvidiabl max=50
[sudo] password for sebastian: 
sebastian@ubuntu:~$
```

=  Brightness full


2)
```
sebastian@ubuntu:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
8
8
8
/sys/class/backlight/nvidia_backlight
324709
324707
127
```

= no change


3)
```
sebastian@ubuntu:~$ nvidiablctl up
nvidiablctl: Befehl nicht gefunden.
```

= command not found


4)
```
sebastian@ubuntu:~$ nvidiablctl down
nvidiablctl: Befehl nicht gefunden.
```

= command not found

---

### Post by Toz on 2013-01-12
I'm sorry, but I just can't seem to figure this out. The numbers aren't making sense. Perhaps it would be best to post at the author's site for further assistance: [https://github.com/guillaumezin/nvidiabl/issues?state=open]("https://github.com/guillaumezin/nvidiabl/issues?state=open")

---

### Post by souliers on 2013-01-12
Alright, let me try and solve this with the developer and see how it goes.  Will keep this thread open and update once there are news.

Thanks a lot for investing a lot of time and expertise, very much appreciated!

---

### Post by Toz on 2013-01-12
Just reviewing the thread. I'm wondering whether we just need to find the correct max value. Here is what we have found out so far:

```
max setting                  max_brightness value
-----------                  ---------------------
unspecified                  611
50                           324709
127                          123700
611                          25509
```

Seems like as the max setting increases, the max_brightness value decreases. I believe we want to get the max_brightness value down to 127.

Out of curiosity, what happens with:
```
sudo modprobe -r nvidiabl && sudo modprobe nvidiabl max=1000
```
and
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```

Try changing the 1000 value to see if you can get max_brightness to be 127.

---

### Post by souliers on 2013-01-16
Hi Toz, happy to try whatever comes to your mind, sorry though I could not get back earlier.

I tried as follows:


```
sebastian@ubuntu:~$ sudo modprobe -r nvidiabl && sudo modprobe nvidiabl max=1000[sudo] password for sebastian: 
sebastian@ubuntu:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
8
8
8
/sys/class/backlight/nvidia_backlight
16399
16398
127
sebastian@ubuntu:~$ 
```


how should I try to get the 127?  looks like it we have it, right?

---

### Post by Toz on 2013-01-16
Not yet. Keep going.
```
sudo modprobe -r nvidiabl && sudo modprobe nvidiabl max=10000
```
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```

---

### Post by souliers on 2013-01-17
and here we go.....

```
sebastian@ubuntu:~$ sudo modprobe -r nvidiabl && sudo modprobe nvidiabl max=10000
[sudo] password for sebastian: 
sebastian@ubuntu:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
8
8
8
/sys/class/backlight/nvidia_backlight
1633
1632
127
sebastian@ubuntu:~$ 
```

---

### Post by Toz on 2013-01-17
We're getting closer. Do any of the following values get you closer to 127?

- 50000
- 75000
- 100000

---

### Post by souliers on 2013-01-18
not sure if I had typed the correct commands but this is what I got:


```
sebastian@ubuntu:~$ sudo modprobe -r nvidiabl && sudo modprobe nvidiabl max=50000
[sudo] password for sebastian: 
sebastian@ubuntu:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
8
8
8
/sys/class/backlight/nvidia_backlight
321
320
127
```


```
sebastian@ubuntu:~$ sudo modprobe -r nvidiabl && sudo modprobe nvidiabl max=75000
sebastian@ubuntu:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
8
8
8
/sys/class/backlight/nvidia_backlight
212
211
127
```


```
sebastian@ubuntu:~$ sudo modprobe -r nvidiabl && sudo modprobe nvidiabl max=100000
sebastian@ubuntu:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
8
8
8
/sys/class/backlight/nvidia_backlight
157
156
127
sebastian@ubuntu:~$ 
```

---

### Post by eenofonn on 2013-01-18
I have a similar problem on my iMac and I've been able to adjust the brightness using xrandr:
```

xrandr --output NAME --brightness 1 #range from 0.0 - 1.0 DO NOT SET TO 0.0

```
Where NAME is the name of your output displayed in:
```

xrandr --current

```

Hope that helps

---

### Post by souliers on 2013-01-18
I could not specify NAME, maybe you can help?


```
sebastian@ubuntu:~$ xrandr --current
Screen 0: minimum 8 x 8, current 1366 x 768, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 connected 1366x768+0+0 (normal left inverted right x axis y axis) 290mm x 170mm
   1366x768       60.0*+
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
sebastian@ubuntu:~$ 
```

---

### Post by eenofonn on 2013-01-18
> **souliers said:**
> I could not specify NAME, maybe you can help?


```
sebastian@ubuntu:~$ xrandr --current
Screen 0: minimum 8 x 8, current 1366 x 768, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 connected 1366x768+0+0 (normal left inverted right x axis y axis) 290mm x 170mm
   1366x768       60.0*+
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
sebastian@ubuntu:~$ 
```
it's right there :) sorry my instructions weren't very clear

for max
```

xrandr --output LVDS-0 --brightness 1

```

lowest I'd recommend
```

xrandr --output LVDS-0 --brightness 0.25

```

---

### Post by souliers on 2013-01-18
alright, got it and can confirm that brightness changes

so how can I relate these commands to the FN keys?

---

### Post by eenofonn on 2013-01-18
> **souliers said:**
> alright, got it and can confirm that brightness changes

so how can I relate these commands to the FN keys?
Not sure about that, I'm working on a app that gives you a slider to do it... but I haven't thought about mapping it to keys

---

### Post by souliers on 2013-01-18
relating them to the fn keys would be my optimal solution but an app with a slider would be of advantage as well.  Let me know once finalised ;)

is there any chance to connect the commands to a script that automatically dims the brightness at startup?


@ Toz:  might there be any further thoughts you have about it?

---

### Post by eenofonn on 2013-01-18
> **souliers said:**
> relating them to the fn keys would be my optimal solution but an app with a slider would be of advantage as well.  Let me know once finalised ;)

is there any chance to connect the commands to a script that automatically dims the brightness at startup?


@ Toz:  might there be any further thoughts you have about it?
you can follow the thread here [http://ubuntuforums.org/showthread.php?t=2106109]("http://ubuntuforums.org/showthread.php?t=2106109")

---

