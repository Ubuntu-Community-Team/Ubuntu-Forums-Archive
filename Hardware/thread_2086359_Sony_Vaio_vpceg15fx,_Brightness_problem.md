---
title: "Sony Vaio vpceg15fx, Brightness problem"
date: 2012-11-20
forum: Hardware
---

### Post by martzp on 2012-11-20
Hello there !
I opened a new question, but basically I have the same problem.
Sony Vaio vpceg15fx, Brightness problem. Ubuntu 12.04 64 bits.
Intel Integrated Graphics card, I can control Brightness via terminal with the command:        intel_backlight xx.

I tried all solutions you (Moderator posted here) but nothing works, I would really appreciate if you were able to tell me what I am doing wrong.

Thanks in advance for your time and patience.

---

### Post by Toz on 2012-11-20
hello and welcome to the forums.

I have moved your post to its own thread. Original thread: [http://ubuntuforums.org/showthread.php?t=2084054]("http://ubuntuforums.org/showthread.php?t=2084054").

Can you open a terminal window and post back the results of these commands:
```
cat /proc/cmdline
lsmod
sudo lspci -vnn  |grep -A10 VGA
```
...run this long command to report back on your backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```
...and run these commands and post back the links that are generated so that we can have a look at your log files:
```
pastebinit /var/log/dmesg
pastebinit /var/log/Xorg.0.log
```

---

### Post by Linuxisfast on 2012-11-20
Install xbacklight and set up a startup shortcut with xbacklight -set xx where xx represents the value of your brightness.

---

### Post by martzp on 2012-11-21
Hello TOZ !
Thanks a lot for your help, I know I am late but I had to go to work. I will post the answers to the commands you wrote :

```
cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-3.2.0-33-generic root=UUID=df5560fb-f4f4-48ce-a0ea-3630b700d6c7 ro quiet splash acpi_backlight=video vt.handoff=7
```

```
lsmod

Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_conexant    62358  1 
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
joydev                 17693  0 
usbhid                 47199  0 
hid                    99592  1 usbhid
arc4                   12529  2 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
sony_laptop            45393  0 
wmi                    19256  1 acer_wmi
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlwifi               397012  0 
mac_hid                13253  0 
mac80211              506816  1 iwlwifi
psmouse                97443  0 
mei                    41616  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
serio_raw              13211  0 
rts_pstor             445196  0 
cfg80211              205544  2 iwlwifi,mac80211
i915                  473298  3 
drm_kms_helper         46978  1 i915
drm                   241921  4 i915,drm_kms_helper
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
lp                     17799  0 
video                  19596  1 i915
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41718  0
```

```
sudo lspci -vnn  |grep -A10 VGA

00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device [104d:908a]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
```

```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done

/sys/class/backlight/acpi_video0
7
7
15
/sys/class/backlight/intel_backlight
700
700
4882
```

```
pastebinit /var/log/dmesg
```

[http://paste.ubuntu.com/1374194/](http://paste.ubuntu.com/1374194/)

```
pastebinit /var/log/Xorg.0.log
```

[http://paste.ubuntu.com/1374195/](http://paste.ubuntu.com/1374195/)

---

### Post by martzp on 2012-11-21
Thanks a lot for your help, but I am already able to do that using :
 
echo 1000 > /sys/class/backlight/intel_backlight/brightness


  Which I entered in the folowing file : /etc/rc.local


What I really need to do is make ubuntu to recognize the Hot keys [FN+F5 ;  FN+F6]
in order to do this automatically.

  
> **Linuxisfast said:**
> Install xbacklight and set up a startup shortcut with xbacklight -set xx where xx represents the value of your brightness.

---

### Post by Toz on 2012-11-21
> **martzp said:**
> Hello TOZ !
Thanks a lot for your help, I know I am late but I had to go to work. I will post the answers to the commands you wrote :

```
cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-3.2.0-33-generic root=UUID=df5560fb-f4f4-48ce-a0ea-3630b700d6c7 ro quiet splash acpi_backlight=video vt.handoff=7
```

```
lsmod

Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_conexant    62358  1 
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
joydev                 17693  0 
usbhid                 47199  0 
hid                    99592  1 usbhid
arc4                   12529  2 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
sony_laptop            45393  0 
wmi                    19256  1 acer_wmi
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlwifi               397012  0 
mac_hid                13253  0 
mac80211              506816  1 iwlwifi
psmouse                97443  0 
mei                    41616  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
serio_raw              13211  0 
rts_pstor             445196  0 
cfg80211              205544  2 iwlwifi,mac80211
i915                  473298  3 
drm_kms_helper         46978  1 i915
drm                   241921  4 i915,drm_kms_helper
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
lp                     17799  0 
video                  19596  1 i915
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41718  0
```

```
sudo lspci -vnn  |grep -A10 VGA

00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device [104d:908a]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
```

```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done

/sys/class/backlight/acpi_video0
7
7
15
/sys/class/backlight/intel_backlight
700
700
4882
```

```
pastebinit /var/log/dmesg
```

[http://paste.ubuntu.com/1374194/](http://paste.ubuntu.com/1374194/)

```
pastebinit /var/log/Xorg.0.log
```

[http://paste.ubuntu.com/1374195/](http://paste.ubuntu.com/1374195/)

Can you try the following kernel paramaters _instead_ of "acpi_backlight=video"? Try each line individually, reboot, test the function keys, and post back whether they work and the results of:
```
cat /proc/cmdline
```...for each attempt:

[LIST=1]
[*]**acpi_backlight=vendor**
[*]**acpi_osi=Linux**
[*]**acpi_osi=Linux acpi_backlight=vendor**
[/LIST]

---

### Post by martzp on 2012-11-21
Hello Toz ! Thanks a lot for your time and attention, I tried individually each parameter and this is what I got :

acpi_backlight=vendor ***** In this first case the bubble indicators on screen move, but back Light does not change.

cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-33-generic root=UUID=df5560fb-f4f4-48ce-a0ea-3630b700d6c7 ro quiet splash acpi_backlight=vendor vt.handoff=7


acpi_osi=Linux  ***** In this second case the bubble indicators on screen move just partially, but back light Does Not change

cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-33-generic root=UUID=df5560fb-f4f4-48ce-a0ea-3630b700d6c7 ro quiet splash acpi_osi=Linux vt.handoff=7

acpi_osi=Linux acpi_backlight=vendor    ***** Third case, the bubble indicators on screen move just partially, but back light Does Not change

cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-33-generic root=UUID=df5560fb-f4f4-48ce-a0ea-3630b700d6c7 ro quiet splash acpi_osi=Linux acpi_backlight=vendor vt.handoff=7

---

### Post by Toz on 2012-11-21
With only **acpi_backlight=vendor** as a kernel parameter, what does the following return?
```
cat /sys/module/video/parameters/brightness_switch_enabled
```

If it returns **Y**, then execute:
```
echo N | sudo tee /sys/module/video/parameters/brightness_switch_enabled
```

If it returns **N**, then execute:
```
echo Y | sudo tee /sys/module/video/parameters/brightness_switch_enabled
```

Does this allow the brightness to be changed?

If still no brightness control, can you type in a terminal:
```
sudo acpi_listen
```
...then press the up brightness and down brightness keys, then post back what gets displayed in the terminal window?

---

### Post by martzp on 2012-11-22
hello Toz ! 
Again thanks a lot for your help and patience.
In both cases there was no change in Brightness. 
The results of the terminal window tests are as follows:

sudo acpi_listen

brightness up
 
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b

brightness down 

sony/hotkey SNC 00000001 00000010
sony/hotkey SNC 00000001 0000003b

---

### Post by Toz on 2012-11-22
Ok, lets make the following changes and see what happens.

Create the following files with the following content (you will need root privileges to do this, so something like "gksu gedit <file>" where <file> is: )

1. /etc/acpi/events/sony-brightness-up
```

event=sony/hotkey SNC 00000001 00000011
action=/etc/acpi/brightup.sh
```

2. /etc/acpi/events/sony-brightness-down
```
event=sony/hotkey SNC 00000001 00000010
action=/etc/acpi/brightdown.sh
```

3. /etc/acpi/brightdown.sh
```
#!/bin/bash
curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -gt 406 ]; then
   curr=$((curr-406));
   echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```

4. /etc/acpi/brightup.sh
```
#!/bin/bash
curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -lt 4477 ]; then
   curr=$((curr+406));
   echo $curr  > /sys/class/backlight/intel_backlight/brightness;
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

Check if the function keys work now.

---

### Post by martzp on 2012-11-22
Hello TOZ !

I really appreciate your kind help ! This time I did and I checked every word inside the files. This  time the screen changes accordingly. Finally I am able to change the screen brightness using the HOT Keys.
There is only one drawback, the Bubble light indicators move just a little bit, not all the way down to the left; however, that's not really important. What really matters is functionality, I just wanted to let you know about it.
With this solution, my problem has been solved. Thanks again for your time and attention.

---

### Post by Toz on 2012-11-22
> **martzp said:**
> 
There is only one drawback, the Bubble light indicators move just a little bit, not all the way down to the left
The code that I created has 12 steps of brightness. Are you saying that there should be more steps? If so, can you try to guess how many steps of brightness there are in your bubble and I can change the code to accomodate.

---

### Post by martzp on 2012-11-22
Hello TOZ !
I am sorry if I didn't explain properly, the physical brightness on the screen changes the way I expected. What does change just a bit is the (Image) Bubble Light Indicator (the bar that appears on the screen), it just moves a little from right to left, but Not all the way to the left. 
I don't really care about that, I just wanted to let you know. What I really wanted was to be able to control the screen brightness with the Hot Keys and now I am able to do so.

---

### Post by Toz on 2012-11-22
Okay. 

I was thinking about changing the number of steps in the code to match the number of increments in the bubble. For example, if you estimate that there are 24 steps of brightness increments in the bubble, I can change the code to have 24 increments and try to match up the actual brightness increments with what the bubble is displaying. I don't mind making the change to make it look more professional or accurate.

If you're happy with the way it this, then can you please mark this thread as Solved using the **Thread Tools** link towards the top of this page? Thanks.

---

### Post by thiagomoreira on 2013-11-13
Ive been struggling with this problem on my VAIO VPCEG for quite a time.   After doing everything mentioned in every forum I found something  interesting.  After changing the boot parameter 'acpi_osi=Linux acpi_backlight=vendor'  and trying to manually change /sys/class/backlight/[vendor - in my case  intel_backlight]/brightness, I realized that changing permission to  this file from root to my user and restarting acpid service, this would  allow me to use brightness keys flawlessly. =)

---

