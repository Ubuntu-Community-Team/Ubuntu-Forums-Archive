---
title: "Sony Vaio E-Series Brightness Issue"
date: 2012-07-25
forum: Hardware
---

### Post by KarlMax on 2012-07-25
Hi everyone!

I hope to find help here!

I have similar problems like the others here on my Sony Vaio E-Series.
It looks like my laptop has nearly the same behavior like dsuresh's.
So I tried the solution of matt_symes. ([http://ubuntuforums.org/showpost.php?p=11378965&postcount=10]("http://ubuntuforums.org/showpost.php?p=11378965&postcount=10"))

After that I have also 2 entries in /sys/class/backlight 
acpi_video0 has changed to sony.

I know that my Fn-keys control the "brightness" file within acpi_video0 or sony folder.

Via terminal I'm able to control the brightness within the intel_backlight folder and it works!

How can I teach my Ubuntu 12.04 to control via Fn-Keys the brightness with the intel_backlight - driver?

Thanks for any suggestions!

---

### Post by Toz on 2012-07-25
Hello and welcome to the forums. I created a new thread for your issue as the other thread was old and dated.

Can you try matt_symes' suggestion again, and after reboot, post back the results of:
```
cat /proc/cmdline
```

Also, does this laptop have an intel video card? Can you run the following command and post back the results:
```
sudo lspci -vnn | grep -A12 VGA
```

---

### Post by KarlMax on 2012-07-26
Hi Toz!

Thanks for your reply and sorry that i didn't open a new thread!

So, my results:

**max@Sony-Vaio:~$ cat /proc/cmdline**
BOOT_IMAGE=/boot/vmlinuz-3.2.0-27-generic root=UUID=f8ff59d6-fae1-47ed-99f6-9bc5fe1e1773 ro acpi_backlight=vendor quiet splash acpi_backlight=vendor vt.handoff=7

The video card is an  Intel HD Graphics 3000 which is integrated into the CPU. That's the only one built-in in my laptop.

**max@Sony-Vaio:~$ sudo lspci -vnn | grep -A12 VGA**
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device [104d:90ac]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at c4000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915

---

### Post by Toz on 2012-07-26
No worries. Can you also post back the contents of **/etc/default/grub** and the results of the following commands:
```
ls /sys/class/backlight
```
```
lsmod
```
```
sudo dmidecode -s system-manufacturer
```
```
sudo dmidecode -s system-product-name
```

---

### Post by KarlMax on 2012-07-26
**/etc/default/grub**
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```[B]
ls /sys/class/backlight[/B] 
```
intel_backlight  sony
```[B]


lsmod[/B]
```
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  0 
vboxdrv               287130  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223962  1 
joydev                 17693  0 
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
btusb                  18288  0 
bluetooth             180104  11 rfcomm,bnep,btusb
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
arc4                   12529  2 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                87692  0 
serio_raw              13211  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
sony_laptop            45393  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 132390  0 
mac80211              506816  1 ath9k
wmi                    19256  1 acer_wmi
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              205544  3 ath9k,mac80211,ath
rts_pstor             445196  0 
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  472897  3 
drm_kms_helper         46978  1 i915
mei                    41616  0 
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62099  0
```[B]

sudo dmidecode -s system-manufacturer
[/B]```
Sony Corporation
```

[B]sudo dmidecode -s system-product-name
[/B]```
SVE1711C5E
```

---

### Post by Toz on 2012-07-26
Okay. A few things to try.

1. Try changing acpi_backlight=vendor to **acpi_backlight=video**. In your /etc/default/grub file, you only need one entry:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=video"
GRUB_CMDLINE_LINUX=""
```
...save file, run ***sudo update-grub*** and reboot.

If that doesn't work...

2. Try unloading the sony_laptop module:
```
sudo modprobe -r sony_laptop
```
Does this remove the sony backlight interface? Do the brightness keys work?

If that doesn't work...

3. Here is a workaround that you could use that should at least control the brightness ([http://ubuntuforums.org/showpost.php?p=9474805&postcount=50]("http://ubuntuforums.org/showpost.php?p=9474805&postcount=50"))

---

### Post by KarlMax on 2012-07-27
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=video"
GRUB_CMDLINE_LINUX=""didn't work!

```
sudo modprobe -r sony_laptop
```has no effect on **/sys/class/backlight**. And no, the Fn-Brightness-keys don't work anymore.

So I tried that workaround: [http://ubuntuforums.org/showpost.php?p=9474805&postcount=50](http://ubuntuforums.org/showpost.php?p=9474805&postcount=50)

I'm very sorry to say that it had absolutely no effect!
I also tried to manipulate the script brightdown.sh in etc/acpi to see if there's any effect:
```
#!/bin/bash

curr=`cat /sys/class/backlight/**intel_backlight**/actual_brightness`
if [ $curr -gt 0 ]; then
curr=$((curr-1));
echo $curr  > /sys/class/backlight/**intel_backlight**/brightness;
fi
```I changed acpi_video0 into **intel_backlight **because if I try to set brightness-levels via terminal (which works), I have to manipulate files in that directory.

So, nothing has changed since my first post.
Is it possible, that there is a problem with the brightness-levels inside /sys/class/backlight/**acpi_video0** and /sys/class/backlight/**intel_backlight**?
File max__brightness inside **intel_backlight**-directory contains 4882.
File max__brightness inside **acpi_video0**-directory contains 15.

I tried the original scripts from fugu72's post and my edited script. There's no different effect within **acpi_video0 **and** intel_backlight**-directories, as the scripts won't exist.
:(
Ah, and I checked if my keycodes are the same as in  fugu72's post. (acpi_listen) They are!

---

### Post by Toz on 2012-07-27
> File max__brightness inside intel_backlight-directory contains 4882.What is the value of actual_brightness?

What happens if you set /sys/class/backlight/intel_backlight/brightness to 2441 (half of max_brightness)? Does the brightness dim in half?

If it does, perhaps try this version of the scripts would work:

**/etc/acpi/brightdown.sh**
```

#!/bin/bash

curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -gt 0 ]; then
curr=$((curr-610));
echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```

**etc/acpi/brightup.sh**
```
#!/bin/bash

curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -lt 4882 ]; then
curr=$((curr+610));
echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```

---

### Post by KarlMax on 2012-07-27
I'm able to set any brightness-level from 0 - 4882 via terminal as I mentioned above. Maybe not elaborately enough. Sorry!

I use the following code to set brightness: ```
echo XXXX | sudo tee - /sys/class/backlight/intel_backlight/brightness
```XXXX stands for any value from 0 - 4882
And that works!!!

The problem is, that I need root-privileges to set my screen-brightness. That's a bit too heavy secure for me. ;-)

Your scripts don't work! 
I think I need a technique to set a value in /sys/class/backlight/**intel_backlight**/brightness without needing root-privileges. 

The Fn-brightness-keys are able to do that in /sys/class/backlight/**acpi_video0**/brightness.
I checked that!

---

### Post by Toz on 2012-07-27
From that previously-linked post, can you post back the contents of these files:
- /etc/acpi/events/sony-brightness-up
- /etc/acpi/events/sony-brightness-down
- /etc/acpi/brightdown.sh
- /etc/acpi/brightup.sh

and the results of this command:
```
ls -l /etc/acpi/bright*
```

---

### Post by KarlMax on 2012-07-27
**- /etc/acpi/events/sony-brightness-up**:
```
event=sony/hotkey SNC 00000001 00000011
action=/etc/acpi/brightup.sh
```[B]- /etc/acpi/events/sony-brightness-down
[/B]```
event=sony/hotkey SNC 00000001 00000010
action=/etc/acpi/brightdown.sh
```[B]
- /etc/acpi/brightdown.sh
[/B]```
#!/bin/bash

curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -gt 0 ]; then
curr=$((curr-610));
echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi\
```[B] - /etc/acpi/brightup.sh
[/B]```
#!/bin/bash


curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -lt 4882 ]; then
curr=$((curr+610));
echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```[B]ls -l /etc/acpi/bright*
[/B]-rw-r--r-- 1 root root 191 Jul 27 14:46 /etc/acpi/brightdown.sh
-rw-r--r-- 1 root root 180 Jul 27 14:44 /etc/acpi/brightdown.sh~
-rw-r--r-- 1 root root 193 Jul 27 14:47 /etc/acpi/brightup.sh
-rw-r--r-- 1 root root 180 Jul 27 14:45 /etc/acpi/brightup.sh~

---

### Post by Toz on 2012-07-27
Make /etc/acpi/brightdown.sh and /etc/acpi/brightup.sh executable:
```
sudo chmod +x /etc/acpi/brightdown.sh
sudo chmod +x /etc/acpi/brightup.sh
```

Remove the last \ after fi in /etc/acpi/brightdown.sh. Should be:
```
#!/bin/bash

curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -gt 0 ]; then
curr=$((curr-610));
echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```
...sorry, that was typo on my part.

Restart acpid
```
sudo service acpid restart
```

Do the brightness keys work now?

---

### Post by KarlMax on 2012-07-27
Thanks bro! You are my hero!!! =D>

It works! I didn't check if the files are  executable. ](*,)

For anybody else with a Sony Vaio E-series with a similar behaviour:
I edited the scripts as followed, that they work as I want:

**/etc/acpi/brightdown.sh**
```
#!/bin/bash

curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -gt 610 ]; then
curr=$((curr-305));
echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```**/etc/acpi/brightup.sh**
```
#!/bin/bash

curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -lt 4882 ]; then
curr=$((curr+305));
echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```@Toz: Thank you very much for your patience and help!

---

### Post by giovanoiannotti on 2012-08-02
> **KarlMax said:**
> Thanks bro! You are my hero!!! =D>

It works! I didn't check if the files are  executable. ](*,)

For anybody else with a Sony Vaio E-series with a similar behaviour:
I edited the scripts as followed, that they work as I want:

**/etc/acpi/brightdown.sh**
```
#!/bin/bash

curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -gt 610 ]; then
curr=$((curr-305));
echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```**/etc/acpi/brightup.sh**
```
#!/bin/bash

curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -lt 4882 ]; then
curr=$((curr+305));
echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```@Toz: Thank you very much for your patience and help!

KarlMax, I am using a Sony VCP F234FX and my hotkeys do not work neither, but volume control. I cannot control brightness nor inactivate touchpad. Can you, please, write your solution step by step? Thank you in advance.

---

### Post by abhicr on 2012-08-05
Hi guys!

I'm using 12.04, and my brightness control does not work. I tried whatever was mentioned in this post, but this is what is different. I've modified the grub to reflect

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"

When I run the next command 
ls /sys/class/backlight/
i see that there are no files in this folder and I don't know how to proceed to fix this one now. Any help will be appreciated.

Thanks in advance.

-Abhi.

---

### Post by Toz on 2012-08-05
> **abhicr said:**
> Hi guys!

I'm using 12.04, and my brightness control does not work. I tried whatever was mentioned in this post, but this is what is different. I've modified the grub to reflect

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"

When I run the next command 
ls /sys/class/backlight/
i see that there are no files in this folder and I don't know how to proceed to fix this one now. Any help will be appreciated.

Thanks in advance.

-Abhi.

This solution won't necessarily work for everyone. What is the make and model of your computer and what video card do you have:
```
sudo lspci -vnn | grep -A12 VGA
```

---

### Post by egidijus on 2012-08-06
I have installed xubuntu 12.04 on my sony vaio tx3xp_b laptop. Problem is when computer boots up, brightness is always on a half (dimmed) and i should increase brightness by Fn+F6 keys no matter computer operates on battery or when on AC.
In /etc/acpi here is no brightdown.sh or brightup.sh files (only asus-brn-down.sh and asus-brn-up.sh). Where can be a problem?

Thanks

Sorry for my poor english...:(

---

### Post by Toz on 2012-08-06
> **egidijus said:**
> I have installed xubuntu 12.04 on my sony vaio tx3xp_b laptop. Problem is when computer boots up, brightness is always on a half (dimmed) and i should increase brightness by Fn+F6 keys no matter computer operates on battery or when on AC.
In /etc/acpi here is no brightdown.sh or brightup.sh files (only asus-brn-down.sh and asus-brn-up.sh). Where can be a problem?

Thanks

Sorry for my poor english...:(

A couple of questions:

1. Do your FN+F6 (increase brightness) and Fn+F7 (decrease brightness) function keys work?

2. Have you tried adding the **acpi_backlight=vendor** kernel parameter as noted in posted #6, point #1?

---

### Post by egidijus on 2012-08-07
*1. Do your FN+F6 (increase brightness) and Fn+F7 (decrease brightness) function keys work?*
Fn+F5/F6 keys are working properly, as intended -- Fn+F5 decrease brightness and Fn+F6 increase brightness.

*2. Have you tried adding the **acpi_backlight=vendor** kernel parameter as noted in posted #6, point #1?*
Yes I tried adding ***acpi_backlight=vendor** *and  ***acpi_backlight=video ***but without success[I]:
- [/I]***acpi_backlight=vendor ***---- nothing changes (I should increase brightness from half to the max after every reboot)
- ***acpi_backlight=video ***---- after reboot, brightness stay on a half position and Fn+F6 key doesn't increase it any more, though Fn+F5 decrease it to the lower initial position.

---

### Post by Toz on 2012-08-07
Right after reboot, before adjusting with your brightness keys, run the following command (it will report back on your backlight interfaces and their values) and post back the results:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
```

---

### Post by egidijus on 2012-08-07
Results for command are:

owner@tx3xp:~$ for interface in /sys/class/backlight/*; do echo  $interface; cat $interface/max_brightness; cat  $interface/actual_brightness; cat $interface/brightness; done
/sys/class/backlight/intel_backlight
15625
15625
15625
/sys/class/backlight/sony
7
3
3
owner@tx3xp:~$

---

### Post by Toz on 2012-08-07
Ok, try this. It should set the brightness to maximum on boot.

Edit your /etc/rc.local file:
```
gksudo gedit /etc/rc.local
```

...and add, before the *exit 0* command, the following command:
```
echo 7 > /sys/class/backlight/sony/brightness
```

...save the file and reboot to test.

If it doesn't work, post back the contents of /etc/rc.local and /var/log/dmesg.

---

### Post by abhicr on 2012-08-08
> **Toz said:**
> This solution won't necessarily work for everyone. What is the make and model of your computer and what video card do you have:
```
sudo lspci -vnn | grep -A12 VGA
```

this is what i get on executing the above command:

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1055] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device [104d:908b]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 4000 [size=128]
    [virtual] Expansion ROM at d3080000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel

My laptop is a Sony Vaio E-series EH16EN with Ubuntu 12.04.
How do I proceed...?

Additionally, I installed the NVIDIA proprietary drivers through the System Settings. Since then, even the illumination level that was being displayed (though brightness was not controlled) has vanished. There is no brightness control bar in the "Brightness and Lock" in the system settings.

-Abhi.

---

### Post by egidijus on 2012-08-08
> **Toz said:**
> Ok, try this. It should set the brightness to maximum on boot.

Edit your /etc/rc.local file:
```
gksudo gedit /etc/rc.local
```...and add, before the *exit 0* command, the following command:
```
echo 7 > /sys/class/backlight/sony/brightness
```...save the file and reboot to test.

If it doesn't work, post back the contents of /etc/rc.local and /var/log/dmesg.

[COLOR=Blue]**Thank you very much... it finally worked** [/COLOR]:D 
I'm curious why this problem arise in ubuntu like systems (at least 11.10 and 12.04, on 11.04 I've not tested) because on 10.04 & 10.10 everything worked fine.
Another issue left to do is volume up/down buttons make working and i 'll be happy with xubuntu on my sony tx3xp.

---

### Post by Toz on 2012-08-08
> **egidijus said:**
> 
Another issue left to do is volume up/down buttons make working and i 'll be happy with xubuntu on my sony tx3xp.

From what I've read about this laptop on the net, it sends the same code for both the volume+ and volume- keys, so it would be difficult to get them to work (don't know how they work in windows). One option is to map volume up and volume down commands to different key strokes. I personally use Ctrl + and and Ctrl - to manage my volume. Look for the keyboard configuration utility and map the following commands:

Ctrl + -> amixer set Master 5%+
Ctrl - -> amixer set Master 5%-

Feel free to change the 5% to whatever value best suits you.

---

### Post by Toz on 2012-08-08
> **abhicr said:**
> this is what i get on executing the above command:

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1055] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device [104d:908b]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 4000 [size=128]
    [virtual] Expansion ROM at d3080000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel

My laptop is a Sony Vaio E-series EH16EN with Ubuntu 12.04.
How do I proceed...?

Additionally, I installed the NVIDIA proprietary drivers through the System Settings. Since then, even the illumination level that was being displayed (though brightness was not controlled) has vanished. There is no brightness control bar in the "Brightness and Lock" in the system settings.

-Abhi.

Since you have the nvidia proprietary driver installed, try adding:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...in the Device section of your xorg.conf file.

---

### Post by abhicr on 2012-08-09
> **Toz said:**
> Since you have the nvidia proprietary driver installed, try adding:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```...in the Device section of your xorg.conf file.

Thanks for the suggestion Toz., but unfortunately, it's doesn't work :(

Here's the content of my xorg.conf file, just in case something here is causing the problem...

Section "Device"
    Identifier    "Device0"
    Driver        "nvidia"
    VendorName    "NVIDIA Corporation"
    Option "RegistryDwords" "EnableBrightnessControl=1"
    Option    "NoLogo"    "True"
EndSection

---

### Post by Toz on 2012-08-09
Did you restart X? Log out and back in again or reboot. If still not working, post back the contents of your /var/log/Xorg.0.log file.

---

### Post by abhicr on 2012-08-10
> **Toz said:**
> Did you restart X? Log out and back in again or reboot. If still not working, post back the contents of your /var/log/Xorg.0.log file.

Yes, I've restarted and checked after those changes. I'd already changed the "RegistryDwords" option before from one of the earlier posts in this thread too... It hasn't worked yet. Here's the dump of the Xorg.0.log file.

```

[    15.971] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    15.971] X Protocol Version 11, Revision 0
[    15.971] Build Operating System: Linux 2.6.42-26-generic x86_64 Ubuntu
[    15.971] Current Operating System: Linux abhi-VPCEH16EN 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64
[    15.971] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-27-generic root=UUID=cea083ad-8f76-45de-ba08-294722978d0c ro acpi_backlight=vendor quiet splash acpi_backlight=vendor vt.handoff=7
[    15.971] Build Date: 16 July 2012  08:06:31PM
[    15.971] xorg-server 2:1.11.4-0ubuntu10.6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    15.971] Current version of pixman: 0.24.4
[    15.971]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    15.971] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.971] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 10 09:43:09 2012
[    15.971] (==) Using config file: "/etc/X11/xorg.conf"
[    15.971] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.972] (==) No Layout section.  Using the first Screen section.
[    15.972] (==) No screen section available. Using defaults.
[    15.972] (**) |-->Screen "Default Screen Section" (0)
[    15.972] (**) |   |-->Monitor "<default monitor>"
[    15.972] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    15.972] (**) |   |-->Device "Device0"
[    15.972] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    15.972] (==) Automatically adding devices
[    15.972] (==) Automatically enabling devices
[    15.972] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.972]     Entry deleted from font path.
[    15.972] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.972]     Entry deleted from font path.
[    15.972] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.972]     Entry deleted from font path.
[    15.972] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.972]     Entry deleted from font path.
[    15.972] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.972]     Entry deleted from font path.
[    15.972] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    15.972]     Entry deleted from font path.
[    15.972] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    15.972] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.972] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.972] (II) Loader magic: 0x7ffdca3a8b00
[    15.972] (II) Module ABI versions:
[    15.972]     X.Org ANSI C Emulation: 0.4
[    15.972]     X.Org Video Driver: 11.0
[    15.972]     X.Org XInput driver : 16.0
[    15.972]     X.Org Server Extension : 6.0
[    15.973] (--) PCI:*(0:1:0:0) 10de:1055:104d:908b rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[    15.973] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.973] (II) LoadModule: "extmod"
[    15.979] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.979] (II) Module extmod: vendor="X.Org Foundation"
[    15.979]     compiled for 1.11.3, module version = 1.0.0
[    15.979]     Module class: X.Org Server Extension
[    15.979]     ABI class: X.Org Server Extension, version 6.0
[    15.979] (II) Loading extension MIT-SCREEN-SAVER
[    15.979] (II) Loading extension XFree86-VidModeExtension
[    15.979] (II) Loading extension XFree86-DGA
[    15.979] (II) Loading extension DPMS
[    15.979] (II) Loading extension XVideo
[    15.979] (II) Loading extension XVideo-MotionCompensation
[    15.979] (II) Loading extension X-Resource
[    15.979] (II) LoadModule: "dbe"
[    15.980] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.980] (II) Module dbe: vendor="X.Org Foundation"
[    15.980]     compiled for 1.11.3, module version = 1.0.0
[    15.980]     Module class: X.Org Server Extension
[    15.980]     ABI class: X.Org Server Extension, version 6.0
[    15.980] (II) Loading extension DOUBLE-BUFFER
[    15.980] (II) LoadModule: "glx"
[    15.980] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    15.990] (II) Module glx: vendor="NVIDIA Corporation"
[    15.990]     compiled for 4.0.2, module version = 1.0.0
[    15.991]     Module class: X.Org Server Extension
[    15.991] (II) NVIDIA GLX Module  295.49  Tue May  1 00:09:10 PDT 2012
[    15.991] (II) Loading extension GLX
[    15.991] (II) LoadModule: "record"
[    15.991] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.991] (II) Module record: vendor="X.Org Foundation"
[    15.991]     compiled for 1.11.3, module version = 1.13.0
[    15.991]     Module class: X.Org Server Extension
[    15.991]     ABI class: X.Org Server Extension, version 6.0
[    15.991] (II) Loading extension RECORD
[    15.991] (II) LoadModule: "dri"
[    15.991] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.991] (II) Module dri: vendor="X.Org Foundation"
[    15.991]     compiled for 1.11.3, module version = 1.0.0
[    15.991]     ABI class: X.Org Server Extension, version 6.0
[    15.991] (II) Loading extension XFree86-DRI
[    15.992] (II) LoadModule: "dri2"
[    15.992] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.992] (II) Module dri2: vendor="X.Org Foundation"
[    15.992]     compiled for 1.11.3, module version = 1.2.0
[    15.992]     ABI class: X.Org Server Extension, version 6.0
[    15.992] (II) Loading extension DRI2
[    15.992] (II) LoadModule: "nvidia"
[    15.992] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    15.992] (II) Module nvidia: vendor="NVIDIA Corporation"
[    15.992]     compiled for 4.0.2, module version = 1.0.0
[    15.992]     Module class: X.Org Video Driver
[    15.993] (II) NVIDIA dlloader X Driver  295.49  Mon Apr 30 23:48:24 PDT 2012
[    15.993] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    15.993] (++) using VT number 7

[    15.993] (II) Loading sub module "fb"
[    15.993] (II) LoadModule: "fb"
[    15.993] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.993] (II) Module fb: vendor="X.Org Foundation"
[    15.993]     compiled for 1.11.3, module version = 1.0.0
[    15.993]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.993] (II) Loading sub module "wfb"
[    15.993] (II) LoadModule: "wfb"
[    15.993] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    15.993] (II) Module wfb: vendor="X.Org Foundation"
[    15.993]     compiled for 1.11.3, module version = 1.0.0
[    15.993]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.993] (II) Loading sub module "ramdac"
[    15.993] (II) LoadModule: "ramdac"
[    15.994] (II) Module "ramdac" already built-in
[    15.994] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    15.994] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    15.994] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.994] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    15.994] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    15.994] (==) NVIDIA(0): RGB weight 888
[    15.994] (==) NVIDIA(0): Default visual is TrueColor
[    15.994] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    15.994] (**) NVIDIA(0): Option "NoLogo" "True"
[    15.994] (**) NVIDIA(0): Option "RegistryDwords" "EnableBrightnessControl=1"
[    15.994] (**) NVIDIA(0): Enabling 2D acceleration
[    17.284] (II) NVIDIA(GPU-0): Display (Chi Mei Optoelectronics corp. (DFP-0)) does not
[    17.284] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    17.286] (II) NVIDIA(0): NVIDIA GPU GeForce 410M (GF119) at PCI:1:0:0 (GPU-0)
[    17.286] (--) NVIDIA(0): Memory: 524288 kBytes
[    17.286] (--) NVIDIA(0): VideoBIOS: 75.19.0c.00.03
[    17.286] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    17.286] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    17.290] (--) NVIDIA(0): Connected display device(s) on GeForce 410M at PCI:1:0:0
[    17.290] (--) NVIDIA(0):     Chi Mei Optoelectronics corp. (DFP-0)
[    17.290] (--) NVIDIA(0): Chi Mei Optoelectronics corp. (DFP-0): 330.0 MHz maximum pixel
[    17.290] (--) NVIDIA(0):     clock
[    17.290] (--) NVIDIA(0): Chi Mei Optoelectronics corp. (DFP-0): Internal Dual Link
[    17.290] (--) NVIDIA(0):     LVDS
[    17.290] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    17.290] (**) NVIDIA(0):     device Chi Mei Optoelectronics corp. (DFP-0) (Using EDID
[    17.290] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    17.307] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    17.307] (==) NVIDIA(0): 
[    17.307] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    17.307] (==) NVIDIA(0):     will be used as the requested mode.
[    17.307] (==) NVIDIA(0): 
[    17.307] (II) NVIDIA(0): Validated modes:
[    17.308] (II) NVIDIA(0):     "nvidia-auto-select"
[    17.308] (II) NVIDIA(0): Virtual screen size determined to be 1366 x 768
[    18.073] (--) NVIDIA(0): DPI set to (99, 102); computed from "UseEdidDpi" X config
[    18.073] (--) NVIDIA(0):     option
[    18.073] (--) Depth 24 pixmap format is 32 bpp
[    18.073] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    18.073] (II) NVIDIA:     access.
[    18.080] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    18.353] (II) Loading extension NV-GLX
[    18.386] (==) NVIDIA(0): Disabling shared memory pixmaps
[    18.386] (==) NVIDIA(0): Backing store disabled
[    18.386] (==) NVIDIA(0): Silken mouse enabled
[    18.386] (==) NVIDIA(0): DPMS enabled
[    18.386] (II) Loading extension NV-CONTROL
[    18.387] (II) Loading extension XINERAMA
[    18.387] (II) Loading sub module "dri2"
[    18.387] (II) LoadModule: "dri2"
[    18.387] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.387] (II) Module dri2: vendor="X.Org Foundation"
[    18.387]     compiled for 1.11.3, module version = 1.2.0
[    18.387]     ABI class: X.Org Server Extension, version 6.0
[    18.387] (II) NVIDIA(0): [DRI2] Setup complete
[    18.387] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    18.387] (==) RandR enabled
[    18.387] (II) Initializing built-in extension Generic Event Extension
[    18.387] (II) Initializing built-in extension SHAPE
[    18.387] (II) Initializing built-in extension MIT-SHM
[    18.387] (II) Initializing built-in extension XInputExtension
[    18.387] (II) Initializing built-in extension XTEST
[    18.387] (II) Initializing built-in extension BIG-REQUESTS
[    18.387] (II) Initializing built-in extension SYNC
[    18.387] (II) Initializing built-in extension XKEYBOARD
[    18.387] (II) Initializing built-in extension XC-MISC
[    18.387] (II) Initializing built-in extension SECURITY
[    18.387] (II) Initializing built-in extension XINERAMA
[    18.387] (II) Initializing built-in extension XFIXES
[    18.387] (II) Initializing built-in extension RENDER
[    18.387] (II) Initializing built-in extension RANDR
[    18.387] (II) Initializing built-in extension COMPOSITE
[    18.387] (II) Initializing built-in extension DAMAGE
[    18.389] (II) Initializing extension GLX
[    18.411] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.414] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    18.414] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.414] (II) LoadModule: "evdev"
[    18.415] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.415] (II) Module evdev: vendor="X.Org Foundation"
[    18.415]     compiled for 1.11.3, module version = 2.7.0
[    18.415]     Module class: X.Org XInput Driver
[    18.415]     ABI class: X.Org XInput driver, version 16.0
[    18.415] (II) Using input driver 'evdev' for 'Power Button'
[    18.415] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.415] (**) Power Button: always reports core events
[    18.415] (**) evdev: Power Button: Device: "/dev/input/event2"
[    18.415] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.415] (--) evdev: Power Button: Found keys
[    18.415] (II) evdev: Power Button: Configuring as keyboard
[    18.415] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    18.415] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    18.415] (**) Option "xkb_rules" "evdev"
[    18.415] (**) Option "xkb_model" "pc105"
[    18.415] (**) Option "xkb_layout" "us"
[    18.416] (II) config/udev: Adding input device Sony Vaio Keys (/dev/input/event8)
[    18.416] (**) Sony Vaio Keys: Applying InputClass "evdev keyboard catchall"
[    18.416] (II) Using input driver 'evdev' for 'Sony Vaio Keys'
[    18.416] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.416] (**) Sony Vaio Keys: always reports core events
[    18.416] (**) evdev: Sony Vaio Keys: Device: "/dev/input/event8"
[    18.416] (--) evdev: Sony Vaio Keys: Vendor 0x104d Product 0
[    18.416] (--) evdev: Sony Vaio Keys: Found keys
[    18.416] (II) evdev: Sony Vaio Keys: Configuring as keyboard
[    18.416] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/SNY5001:00/input/input8/event8"
[    18.416] (II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD, id 7)
[    18.416] (**) Option "xkb_rules" "evdev"
[    18.416] (**) Option "xkb_model" "pc105"
[    18.416] (**) Option "xkb_layout" "us"
[    18.417] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    18.417] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.417] (II) Using input driver 'evdev' for 'Video Bus'
[    18.417] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.417] (**) Video Bus: always reports core events
[    18.417] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    18.417] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    18.417] (--) evdev: Video Bus: Found keys
[    18.417] (II) evdev: Video Bus: Configuring as keyboard
[    18.417] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:21/LNXVIDEO:00/input/input4/event4"
[    18.417] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    18.417] (**) Option "xkb_rules" "evdev"
[    18.417] (**) Option "xkb_model" "pc105"
[    18.417] (**) Option "xkb_layout" "us"
[    18.418] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.418] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.418] (II) Using input driver 'evdev' for 'Power Button'
[    18.418] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.418] (**) Power Button: always reports core events
[    18.418] (**) evdev: Power Button: Device: "/dev/input/event0"
[    18.418] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.418] (--) evdev: Power Button: Found keys
[    18.418] (II) evdev: Power Button: Configuring as keyboard
[    18.418] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    18.418] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    18.418] (**) Option "xkb_rules" "evdev"
[    18.418] (**) Option "xkb_model" "pc105"
[    18.418] (**) Option "xkb_layout" "us"
[    18.418] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    18.418] (II) No input driver specified, ignoring this device.
[    18.418] (II) This device may have been added with another device file.
[    18.419] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event10)
[    18.419] (II) No input driver specified, ignoring this device.
[    18.419] (II) This device may have been added with another device file.
[    18.419] (II) config/udev: Adding input device Sony Visual Communication Camer (/dev/input/event5)
[    18.419] (**) Sony Visual Communication Camer: Applying InputClass "evdev keyboard catchall"
[    18.419] (II) Using input driver 'evdev' for 'Sony Visual Communication Camer'
[    18.419] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.419] (**) Sony Visual Communication Camer: always reports core events
[    18.419] (**) evdev: Sony Visual Communication Camer: Device: "/dev/input/event5"
[    18.419] (--) evdev: Sony Visual Communication Camer: Vendor 0xc45 Product 0x6436
[    18.419] (--) evdev: Sony Visual Communication Camer: Found keys
[    18.419] (II) evdev: Sony Visual Communication Camer: Configuring as keyboard
[    18.419] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input5/event5"
[    18.419] (II) XINPUT: Adding extended input device "Sony Visual Communication Camer" (type: KEYBOARD, id 10)
[    18.419] (**) Option "xkb_rules" "evdev"
[    18.419] (**) Option "xkb_model" "pc105"
[    18.419] (**) Option "xkb_layout" "us"
[    18.420] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event6)
[    18.420] (II) No input driver specified, ignoring this device.
[    18.420] (II) This device may have been added with another device file.
[    18.420] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event7)
[    18.420] (II) No input driver specified, ignoring this device.
[    18.420] (II) This device may have been added with another device file.
[    18.421] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    18.421] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.421] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    18.421] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.421] (**) AT Translated Set 2 keyboard: always reports core events
[    18.421] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    18.421] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    18.421] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    18.421] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    18.421] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    18.421] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    18.421] (**) Option "xkb_rules" "evdev"
[    18.421] (**) Option "xkb_model" "pc105"
[    18.421] (**) Option "xkb_layout" "us"
[    18.421] (II) config/udev: Adding input device DualPoint Stick (/dev/input/event11)
[    18.421] (**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
[    18.422] (**) DualPoint Stick: Applying InputClass "trackpoint catchall"
[    18.422] (II) Using input driver 'evdev' for 'DualPoint Stick'
[    18.422] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.422] (**) DualPoint Stick: always reports core events
[    18.422] (**) evdev: DualPoint Stick: Device: "/dev/input/event11"
[    18.422] (--) evdev: DualPoint Stick: Vendor 0x2 Product 0x8
[    18.422] (--) evdev: DualPoint Stick: Found 3 mouse buttons
[    18.422] (--) evdev: DualPoint Stick: Found relative axes
[    18.422] (--) evdev: DualPoint Stick: Found x and y relative axes
[    18.422] (II) evdev: DualPoint Stick: Configuring as mouse
[    18.422] (**) Option "Emulate3Buttons" "true"
[    18.422] (**) Option "EmulateWheel" "true"
[    18.422] (**) Option "EmulateWheelButton" "2"
[    18.422] (**) Option "YAxisMapping" "4 5"
[    18.422] (**) evdev: DualPoint Stick: YAxisMapping: buttons 4 and 5
[    18.422] (**) Option "XAxisMapping" "6 7"
[    18.422] (**) evdev: DualPoint Stick: XAxisMapping: buttons 6 and 7
[    18.422] (**) evdev: DualPoint Stick: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.422] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input11/event11"
[    18.422] (II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE, id 12)
[    18.422] (II) evdev: DualPoint Stick: initialized for relative axes.
[    18.422] (**) DualPoint Stick: (accel) keeping acceleration scheme 1
[    18.422] (**) DualPoint Stick: (accel) acceleration profile 0
[    18.422] (**) DualPoint Stick: (accel) acceleration factor: 2.000
[    18.422] (**) DualPoint Stick: (accel) acceleration threshold: 4
[    18.422] (II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse1)
[    18.422] (II) No input driver specified, ignoring this device.
[    18.422] (II) This device may have been added with another device file.
[    18.423] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event12)
[    18.423] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
[    18.423] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
[    18.423] (II) LoadModule: "synaptics"
[    18.423] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.423] (II) Module synaptics: vendor="X.Org Foundation"
[    18.423]     compiled for 1.11.3, module version = 1.6.2
[    18.423]     Module class: X.Org XInput Driver
[    18.423]     ABI class: X.Org XInput driver, version 16.0
[    18.423] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[    18.423] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.423] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    18.423] (**) Option "Device" "/dev/input/event12"
[    18.428] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: ignoring touch events for semi-multitouch device
[    18.428] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 2000
[    18.428] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 1400
[    18.428] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[    18.428] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: device does not report finger width.
[    18.428] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle double triple
[    18.428] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: Vendor 0x2 Product 0x8
[    18.428] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: invalid finger width range.  defaulting to 0 - 15
[    18.428] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    18.428] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    18.440] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input12/event12"
[    18.440] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD, id 13)
[    18.440] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    18.440] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: MaxSpeed is now 1.75
[    18.440] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: AccelFactor is now 0.082
[    18.440] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[    18.440] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 1
[    18.440] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[    18.440] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[    18.440] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    18.440] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse2)
[    18.440] (**) AlpsPS/2 ALPS DualPoint TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    18.443] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/event9)
[    18.443] (II) No input driver specified, ignoring this device.
[    18.443] (II) This device may have been added with another device file.
[    18.443] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse0)
[    18.443] (II) No input driver specified, ignoring this device.
[    18.443] (II) This device may have been added with another device file.
[    49.379] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[  1025.305] (II) config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/event13)
[  1025.305] (**)  USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
[  1025.305] (II) Using input driver 'evdev' for ' USB OPTICAL MOUSE'
[  1025.305] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1025.305] (**)  USB OPTICAL MOUSE: always reports core events
[  1025.305] (**) evdev:  USB OPTICAL MOUSE: Device: "/dev/input/event13"
[  1025.305] (--) evdev:  USB OPTICAL MOUSE: Vendor 0x15d9 Product 0xa4c
[  1025.305] (--) evdev:  USB OPTICAL MOUSE: Found 3 mouse buttons
[  1025.305] (--) evdev:  USB OPTICAL MOUSE: Found scroll wheel(s)
[  1025.305] (--) evdev:  USB OPTICAL MOUSE: Found relative axes
[  1025.305] (--) evdev:  USB OPTICAL MOUSE: Found x and y relative axes
[  1025.305] (II) evdev:  USB OPTICAL MOUSE: Configuring as mouse
[  1025.305] (II) evdev:  USB OPTICAL MOUSE: Adding scrollwheel support
[  1025.305] (**) evdev:  USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
[  1025.305] (**) evdev:  USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1025.305] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input13/event13"
[  1025.305] (II) XINPUT: Adding extended input device " USB OPTICAL MOUSE" (type: MOUSE, id 14)
[  1025.305] (II) evdev:  USB OPTICAL MOUSE: initialized for relative axes.
[  1025.306] (**)  USB OPTICAL MOUSE: (accel) keeping acceleration scheme 1
[  1025.306] (**)  USB OPTICAL MOUSE: (accel) acceleration profile 0
[  1025.306] (**)  USB OPTICAL MOUSE: (accel) acceleration factor: 2.000
[  1025.306] (**)  USB OPTICAL MOUSE: (accel) acceleration threshold: 4
[  1025.308] (II) config/udev: Adding input device  USB OPTICAL MOUSE (/dev/input/mouse3)
[  1025.308] (II) No input driver specified, ignoring this device.
[  1025.308] (II) This device may have been added with another device file.
```

---

### Post by Toz on 2012-08-10
Try removing **acpi_backlight=vendor** from your kernel command line (you've entered it in two places in /etc/default/grub - remove both entries) and leaving **Option "RegistryDwords" "EnableBrightnessControl=1"** in your xorg.conf file.

Reboot and try again. If no luck, post back /var/log/Xorg.0.log again as well as /var/log/dmesg. This method might be easier:
```
pastebinit /var/log/Xorg.0.log
pastebinit /var/log/syslod
```
...and post back the links that are generated.

EDIT: After removing acpi_backlight= vendor, do you have any entries in /sys/class/backlight?

---

### Post by abhicr on 2012-08-10
Thanks a million Toz, it's working after changing the grub with the [B]acpi_backlight=vendor
[/B]entries removed and one of them replaced with [B]
acpi_backlight=video[/B]
I'm able to control the screen brightness now. :D

here's the file in the **/sys/class/backlight** folder after the grub update...
acpi_video0

EDIT: sorry Toz, should've seen through the thread more in detail... :( found that you've already helped us out with the exact same solution... Thanks for all the support though :)

---

### Post by Toz on 2012-08-10
No worries. 

I have a quick question though: Do you still have the EnableBrightnessControl setting in your xorg.conf file?

---

### Post by abhicr on 2012-08-11
yes, the EnableBrightnessControl flag is still set to 1.

---

### Post by manojdh on 2012-12-18
[B]Sony E series with quantal installed
It worked by adding:
Option "RegistryDwords" "EnableBrightnessControl=1"[/B] in xorg.conf file.

Actually there are two different solutions to this problem depending upon whether you have nvidia drivers installed or not . :p

---

