---
title: "Not able to control Brightness in my VAIO CW15FG laptop"
date: 2012-11-14
forum: Hardware
---

### Post by wizardvenkat on 2012-11-14
I've installed Ubuntu 12.10 recently. 
When ever I press Fn keys along with F5/F6 it shows that the brightness decreases / increases accordingly. But no difference on the screen.

I tried modifying the grub , xorg.conf files as mentioned in many other posts. But none helped me. I'm new to the Ubuntu environment and I'm completely clueless about what to do. 

In my /sys/class/backlight directory, I find two folders (shortcuts) 
nv_backlight &
sony
And when I change my brightness I find the value changes accordingly in brightness file present inside 'sony' folder.

Earlier I tried to install nvidia driver for my G210M graphics card and failed.  I get a blank screen after the boot screen after installation. So reverted the settings to work on my default driver

I even tried kubuntu 12.10 live cd (KDE environment) and found the same problem there. 
Plz someone help me with this brightness issue. it is even Ok for me to work without my nvidia drivers as I'm not a big fan of games.

---

### Post by Toz on 2012-11-14
> **wizardvenkat said:**
> I tried modifying the grub

What modifications did you make to grub? Did you try the **acpi_backlight=vendor** parameter?

---

### Post by wizardvenkat on 2012-11-14
> **Toz said:**
> What modifications did you make to grub? Did you try the **acpi_backlight=vendor** parameter?

This info is available in my /etc/default/grub
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=sony"
GRUB_CMDLINE_LINUX="acpi_backlight=sony"

---

### Post by Toz on 2012-11-14
The parameter should say exactly **acpi_backlight=vendor**, the ***vendor*** keyword indicating to use the vendor-specific driver instead of the acpi driver.

*acpi_backlight=sony* is not a valid parameter.

Make sure to also run:
```
sudo update-grub
```
...afterwards to commit the edits.

If it still doesn't work on reboot, can you post back the results of:
```
cat /proc/cmdline
```
...and the contents of your dmesg log file? Use this command:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

### Post by wizardvenkat on 2012-11-14
**acpi_backlight=vendor **statement is also not working.

These are my results for cat proc/cmdline :

BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic root=UUID=446e1f28-d397-4eef-a7fb-fa0eda88129a ro acpi_backlight=vendor quiet splash acpi_backlight=vendor vt.handoff=7

And my PasteBin URL is [here]("http://paste.ubuntu.com/1359382/")

---

### Post by Toz on 2012-11-14
Can you remove both of the acpi_backlight=vendor parameters from grub and reboot the computer? This time post back the results of:

```
cat /proc/cmdline
lsmod
```

...and the links to the following two log files:
```
pastebinit /var/log/dmesg
pastebinit /var/log/Xorg.0.log
```

You also mentioned that you tried to install the nvidia driver and that it didn't work. How did you try to install it? Was it through the additional drivers tab via:
```
software-properties-gtk
```
...(or Ubuntu Software Centre, select Edit->Software Sources and on the Additional Drivers tab)?

---

### Post by wizardvenkat on 2012-11-14
The results for cat /proc/cmdline :

BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic root=UUID=446e1f28-d397-4eef-a7fb-fa0eda88129a ro quiet splash vt.handoff=7

The results for lsmod : 

Module                  Size  Used by
snd_hda_codec_hdmi     32007  4 
joydev                 17457  0 
bnep                   18140  2 
parport_pc             32688  0 
ppdev                  17073  0 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
binfmt_misc            17500  1 
arc4                   12529  2 
coretemp               13400  0 
microcode              22803  0 
snd_hda_codec_realtek    77876  1 
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
snd_timer              29425  2 snd_seq,snd_pcm
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
mac_hid                13205  0 
videobuf2_memops       13368  1 videobuf2_vmalloc
sony_laptop            54039  0 
snd                    78734  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
nouveau               895609  3 
psmouse                95552  0 
iwlwifi               386826  0 
serio_raw              13215  0 
ttm                    83595  1 nouveau
mac80211              539908  1 iwlwifi
drm_kms_helper         46784  1 nouveau
drm                   275528  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13413  1 nouveau
mxm_wmi                12979  1 nouveau
cfg80211              206566  2 iwlwifi,mac80211
video                  19335  1 nouveau
soundcore              15047  1 snd
lpc_ich                17061  0 
wmi                    19070  2 nouveau,mxm_wmi
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
uas                    17844  0 
usb_storage            48838  0 
firewire_ohci          40401  0 
sdhci_pci              18616  0 
firewire_core          64368  1 firewire_ohci
sdhci                  32645  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
sky2                   58111  0

---

### Post by wizardvenkat on 2012-11-14
[Pastebin for /var/log/dmesg]("http://paste.ubuntu.com/1359495/")

[PasteBin for /var/log/Xorg.0.log]("http://paste.ubuntu.com/1359500/")

---

### Post by wizardvenkat on 2012-11-14
I've downloaded the nvidia drivers from Nvidia site.
I don't know the version but I hope the filename "NVIDIA-Linux-x86_64-304.64.run" gives you the information you needed..

---

### Post by Toz on 2012-11-15
> **wizardvenkat said:**
> I've downloaded the nvidia drivers from Nvidia site.
I don't know the version but I hope the filename "NVIDIA-Linux-x86_64-304.64.run" gives you the information you needed..

Try enabling the official additional drivers instead. Fire up Ubuntu Software Centre, select Edit->Software Sources, and look on the "Additional Drivers" tab (or, run "software-properties-gtk" in a terminal window instead).

EDIT: Hopefully, you can get nvidia drivers installed. If, with the nvidia drivers installed, you still don't get backlight control, you can try adding:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the "Device" section of /etc/X11/xorg.conf (log out and back in for it to take effect).

If still no luck, have a look at the nvidiabl driver [here]("https://github.com/guillaumezin/nvidiabl"). According to nvidiabl-laptops.h, your system is supported. The downloadable deb file is located [here]("https://github.com/guillaumezin/nvidiabl/downloads")

---

### Post by wizardvenkat on 2012-11-15
I installed the Nvidia drivers from software-properties-gtk, 
changed the xorg.conf file like this :

```
 
Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection

```And added the acpi_backlight parameter in grub like this :

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"

```Updated the Grub and restarted. But no changes...
So as you suggested I installed nvidiabl driver from github. Even after that I can't change my brightness.... :( What to do ?

---

### Post by Toz on 2012-11-15
1. Uninstall nvidiabl. 

2. Change grub and add **acpi_osi=Linux** to the existing kernel line. Reboot. Does it work now? Post back:
```
cat /proc/cmdline
```

3. Remove both acpi_osi and acpi_backlight=vendor. Reboot.

Post back:
```
pastebinit /var/log/dmesg
pastebinit /var/log/Xorg.0.log
```
...and the results of the following command:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```
...and
```
lsmod
```

4. Are you using the function keys to change brightness? If so, do they emit an acpi response? Open a terminal window, run:
```
sudo acpi_listen
```
...and press the function keys. Do any codes show up in the terminal window?

---

### Post by wizardvenkat on 2012-11-15
I uninstalled nvidiabl.
Modified the grub like this :

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"

```

Updated & rebooted. But no luck.

Also removed acpi_osi & acpi_backlight parameters and restarted. Still no luck.

[pastebinit /var/log/dmesg]("http://paste.ubuntu.com/1361632/") 
[pastebinit /var/log/Xorg.0.log]("http://paste.ubuntu.com/1361633/") 

Results for 'for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done'
```

/sys/class/backlight/sony
7
7
7


```

And lsmod code is 
```

Module                  Size  Used by
btrfs                 761721  0 
zlib_deflate           26914  1 btrfs
libcrc32c              12644  1 btrfs
ufs                    74821  0 
qnx4                   13317  0 
hfsplus                84442  0 
hfs                    54553  0 
minix                  36058  0 
ntfs                   97304  0 
msdos                  17332  0 
jfs                   181093  0 
xfs                   837979  0 
reiserfs              246392  0 
ext2                   72880  0 
joydev                 17457  0 
nvidia              11257759  42 
snd_hda_codec_hdmi     32007  4 
arc4                   12529  2 
coretemp               13400  0 
mxm_wmi                12979  0 
snd_hda_codec_realtek    77876  1 
psmouse                95552  0 
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
microcode              22803  0 
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13215  0 
iwlwifi               386826  0 
lpc_ich                17061  0 
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
snd                    78734  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              539908  1 iwlwifi
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
cfg80211              206566  2 iwlwifi,mac80211
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
video                  19335  0 
mac_hid                13205  0 
bnep                   18140  2 
sony_laptop            54039  0 
rfcomm                 46619  0 
parport_pc             32688  0 
wmi                    19070  1 mxm_wmi
bluetooth             209199  10 bnep,rfcomm
ppdev                  17073  0 
binfmt_misc            17500  1 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
usb_storage            48838  0 
firewire_ohci          40401  0 
firewire_core          64368  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18616  0 
sdhci                  32645  1 sdhci_pci
sky2                   58111  0 

```

Yes I tried both the Fn keys and changing from the settings itself...
I'm getting the acpi_listen response as follows :
```

sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000010
sony/hotkey SNC 00000001 0000003b

```
The first two line when I increase my brightness and the others while decreasing it....

---

### Post by Toz on 2012-11-15
Do the following commands adjust your brightness:
```
echo 4 | sudo tee /sys/class/backlight/sony/brightness
```
...to dim and:
```
echo 7 | sudo tee /sys/class/backlight/sony/brightness
```
...to brighten again.

EDIT: It looks like acpi events are being generated, they just don't seem to be tied to anything. If the above works, we may be able to workaround this issue.

(note to self: [http://ubuntuforums.org/showthread.php?t=2033273](http://ubuntuforums.org/showthread.php?t=2033273))

---

### Post by wizardvenkat on 2012-11-15
No the code 

"echo 4 | sudo tee /sys/class/backlight/sony/brightness" 

still does not make changes to my screen...

As I've already mentioned, the values in brightness in /sys/class/backlight/sony changes... But no effects on screen...

---

### Post by Toz on 2012-11-15
Hmmm, can you report back again the following:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```
...just to confirm.

EDIT: Also report back the results of that command with the **acpi_backlight=vendor** grub parameter.

---

### Post by wizardvenkat on 2012-11-15
After executing the code "echo 4 | sudo tee /sys/class/backlight/sony/brightness"

I get the response for "for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done"
as 
/sys/class/backlight/sony
4
4
7

---

### Post by Toz on 2012-11-15
Can you try the same command with the **acpi_backlight=vendor** grub parameter enabled?

---

### Post by wizardvenkat on 2012-11-15
Modified grub like this :

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"

```

updated it, rebooted and gave the command
```

echo 4 | sudo tee /sys/class/backlight/sony/brightness

```
after which I gave
```

for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done

```
and still got the same response..
```

/sys/class/backlight/sony
4
4
7


```

---

### Post by Toz on 2012-11-15
Did the screen brightness change?

---

### Post by wizardvenkat on 2012-11-15
Before installing nvidia drivers from software-properties-gtk, I had problem when ubuntu starts..
I get a plain purple screen after which I get the login screen.
While shut down I get the usual Ubuntu screen (the purple screen with Ubuntu written and an animation indicating that shutdown /restart process is going on)

After installing the nvidia drivers, I get a text "Ubuntu 12.10" with no loading animation. and sometimes I get it with a black background on it. And while shutting down, I just get my screen blanked. No acknowledgement about the Ubuntu getting shut down. I've to to look at the Power LED to make sure my PC is turned off...

Is that something to do with/related to the brightness issue ???

---

### Post by wizardvenkat on 2012-11-15
> **Toz said:**
> Did the screen brightness change?

No, no changes on the screen :(

---

### Post by Toz on 2012-11-15
> **wizardvenkat said:**
> Before installing nvidia drivers from software-properties-gtk, I had problem when ubuntu starts..
I get a plain purple screen after which I get the login screen.
While shut down I get the usual Ubuntu screen (the purple screen with Ubuntu written and an animation indicating that shutdown /restart process is going on)

After installing the nvidia drivers, I get a text "Ubuntu 12.10" with no loading animation. and sometimes I get it with a black background on it. And while shutting down, I just get my screen blanked. No acknowledgement about the Ubuntu getting shut down. I've to to look at the Power LED to make sure my PC is turned off...

Is that something to do with/related to the brightness issue ???

More likely its related to the install of the nvidia drivers. Unfortunately, I don't have an nvidia card and can't comment. You might want to create another thread afterwards to discuss that issue.

In the meantime, does that command change the screen brightness for you?
```
echo 4 | sudo tee /sys/class/backlight/sony/brightness
```

You can also try:
```
echo 1 | sudo tee /sys/class/backlight/sony/brightness
```
...to try to get more of an effect.

---

### Post by wizardvenkat on 2012-11-15
> **Toz said:**
> More likely its related to the install of the nvidia drivers. Unfortunately, I don't have an nvidia card and can't comment. You might want to create another thread afterwards to discuss that issue.

In the meantime, does that command change the screen brightness for you?
```
echo 4 | sudo tee /sys/class/backlight/sony/brightness
```You can also try:
```
echo 1 | sudo tee /sys/class/backlight/sony/brightness
```...to try to get more of an effect.

No changes on the screen...

---

### Post by Toz on 2012-11-15
That's interesting. Can you try re-installing nvidiabl ([https://github.com/guillaumezin/nvidiabl/downloads]("https://github.com/guillaumezin/nvidiabl/downloads")) and then again try running:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```

Lets see if we can get a backlight interface that we can manipulate.

---

### Post by wizardvenkat on 2012-11-16
After I re-installed nvidiabl drivers again, I get 
```

/sys/class/backlight/nvidia_backlight
34487
126
127
/sys/class/backlight/sony
1
1
7

```

after typing 
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done

---

### Post by Toz on 2012-11-16
Do either of these commands dim the screen brightness:
```
echo 64 | sudo tee /sys/class/backlight/nvidia_backlight/brightness
```
```
echo 4 | sudo tee /sys/class/backlight/sony/brightness
```

Also, what does the following return:
```
lsmod
```

---

### Post by wizardvenkat on 2012-11-16
Finally !!! I'm able to control the brightness through the code 
```

echo 20 | sudo tee /sys/class/backlight/nvidia_backlight/brightness

```However, the code 
```

echo 1 | sudo tee /sys/class/backlight/sony/brightness

```still doesnt work....

The results for lsmod is :
```

Module                  Size  Used by
usb_storage            48838  0 
uas                    17844  0 
rfcomm                 46619  0 
bnep                   18140  2 
parport_pc             32688  0 
bluetooth             209199  10 rfcomm,bnep
ppdev                  17073  0 
binfmt_misc            17500  1 
joydev                 17457  0 
snd_hda_codec_hdmi     32007  4 
arc4                   12529  2 
nvidia              11257759  42 
coretemp               13400  0 
snd_hda_codec_realtek    77876  1 
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
mxm_wmi                12979  0 
nvidiabl               40764  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlwifi               386826  0 
mac80211              539908  1 iwlwifi
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
soundcore              15047  1 snd
videobuf2_vmalloc      12860  1 uvcvideo
video                  19335  0 
videobuf2_memops       13368  1 videobuf2_vmalloc
psmouse                95552  0 
cfg80211              206566  2 iwlwifi,mac80211
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
lpc_ich                17061  0 
sony_laptop            54039  0 
wmi                    19070  1 mxm_wmi
mac_hid                13205  0 
serio_raw              13215  0 
microcode              22803  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
firewire_ohci          40401  0 
sky2                   58111  0 
firewire_core          64368  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18616  0 
sdhci                  32645  1 sdhci_pci

```So how do I control the brightness from the GUI (slider in 'Brightness & Lock' utility and hotkeys) ?

---

### Post by Toz on 2012-11-16
Ok, lets make the following changes and see what happens.

Create the following files with the following content (you will need root privileges to do this, so something like "gksu gedit <file>" where <file> is: )

1. **/etc/acpi/events/sony-brightness-up**
```
event=sony/hotkey SNC 00000001 00000011
action=/etc/acpi/brightup.sh
```

2. **/etc/acpi/events/sony-brightness-down**
```
event=sony/hotkey SNC 00000001 00000010
action=/etc/acpi/brightdown.sh
```

3. **/etc/acpi/brightdown.sh**
```
#!/bin/bash
curr=`cat /sys/class/backlight/nvidia_backlight/actual_brightness`
if [ $curr -gt 11 ]; then
   curr=$((curr-11));
   echo $curr  > /sys/class/backlight/nvidia_backlight/brightness;
fi
```

4. **/etc/acpi/brightup.sh**
```
#!/bin/bash
curr=`cat /sys/class/backlight/nvidia_backlight/actual_brightness`
if [ $curr -lt 117 ]; then
   curr=$((curr+11));
   echo $curr  > /sys/class/backlight/nvidia_backlight/brightness;
fi
```

Make all 4 of those scripts executable via:
```
sudo chmod +x /etc/acpi/events/sony-brightness-up
sudo chmod +x /etc/acpi/events/sony-brightness-down
sudo chmod +x /etc/acpi/brightdown.sh
sudo chmod +x /etc/acpi/brightup.sh
```

Restart acpid:
```
sudo service acpid restart
```

The function keys should now work.

Let me know if the gui controls work as well (you should probably log out and back in again to check the gui controls).



_EDIT:_ To make the gui controls work, I believe you need to create (if it doesn't already exist) the file **/etc/modprobe.d/nvidiabl** with the following contents:
```
options nvidiabl type=firmware
```
...and reboot, or:
```

sudo modprobe -r nvidiabl
sudo modprobe nvidiabl type=firmware
```

---

### Post by wizardvenkat on 2012-11-16
Thanks a lot Toz !! :)
Everything works fine now...
The hot keys and the GUI control.
But still I don't know why my Brightness resets to maximum when I open Firefox or Thunderbird ?
It does not happen if I open other softwares..

---

### Post by Toz on 2012-11-16
> **wizardvenkat said:**
> Thanks a lot Toz !! :)
Everything works fine now...
The hot keys and the GUI control.
Good news. Glad to hear it worked.
> But still I don't know why my Brightness resets to maximum when I open Firefox or Thunderbird ?
It does not happen if I open other softwares..
I've never heard about this type of problem before. Pretty wierd. A quick search of google found [this]("https://developer.mozilla.org/en-US/docs/DOM/window.screen.mozBrightness"). Can you check and see if you have the property **dom.screenBrightnessProperty.enabled** and if so, is it set to true? You might also check what plugins/add-ons you have installed and whether one of them might be doing this.

---

