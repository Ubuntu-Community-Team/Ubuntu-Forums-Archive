---
title: "Non-functioning FN key on Sony Vaio"
date: 2013-12-08
forum: Hardware
---

### Post by Chris_Rutland on 2013-12-08
Hi, 
Have downloaded and installed Ubuntu 12.04 on my Vaio VGN-FJ3S/W. Everything is great except the FN key controlling the sound keys (F2, F3 and F4) and brightness keys (F5, F6) doesn't work.
Have tried changing <GRUB_CMDLINE_LINUX=""> to <GRUB_CMDLINE_LINUX="acpi_backlight=vendor"> and then GRUB_CMDLINE_LINUX="acpi_osi=Linux > and after that <GRUB_CMDLINE_LINUX="acpi_osi=linux> but nothing works!
Suggestions welcome
Thanks

---

### Post by Toz on 2013-12-08
Hello and welcome to the forums.

Can we see some more detailed information about your system? Open a terminal window, run the following commands, and post back the results:

1. Your dmesg log file:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated. If you get a message that pastebinit isn't installed, run:
```
sudo apt-get install pastebinit
```
...to install it.

2. Info about your video and audio devices:
```
lspci -k | grep -iA2 -e VGA -e Audio
```

3. Your active backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
```

4. What actual functions are the F2, F3, F4, F5 and F6 keys supposed to perform? (i.e. which one is for brightness up, brightness sound, volume up, etc).

---

### Post by Chris_Rutland on 2013-12-08
Thanks for your help.
Hope this works: [http://paste.ubuntu.com/6543016/plain/](http://paste.ubuntu.com/6543016/plain/)

Audio:
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Sony Corporation Device 81f1
    Kernel driver in use: i915
--
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
    Subsystem: Sony Corporation Device 81f1
    Kernel driver in use: snd_hda_intel

Backlight:
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Sony Corporation Device 81f1
    Kernel driver in use: i915
--
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
    Subsystem: Sony Corporation Device 81f1
    Kernel driver in use: snd_hda_intel
chrisrutland@chrisrutland-VGN-FJ3S-W:~$ ^C
chrisrutland@chrisrutland-VGN-FJ3S-W:~$ 
chrisrutland@chrisrutland-VGN-FJ3S-W:~$ 
chrisrutland@chrisrutland-VGN-FJ3S-W:~$ for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
/sys/class/backlight/sony
7
7

F2 is mute, F3 is audio down, F4 is audio up, F5 is brightness down, F6 is brightness up. 

Thanks.

---

### Post by Toz on 2013-12-08
Are you able to change the brightness using the brightness slider?

Can you run the following command in a terminal window:
```
xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
```
...then press the following keys/combination in this order:

Fn+F2
Enter
Fn+F3
Enter
Fn+F4
Enter
Fn+F5
Enter
Fn+F6
Enter

Then close the "Event Tester" window that opened and paste back the results that displayed in the terminal window. Lets see if the keys are being recognized and how.

---

### Post by Chris_Rutland on 2013-12-08
Brightness slider works perfectly.

The 2nd bit returned the following results:

36 Return
36 Return
36 Return
36 Return
36 Return
36 Return

---

### Post by Toz on 2013-12-08
Either the keys are not being recognized or they are being handled by the bios. Can you post back your list of modules:
```
lsmod
```
...you must have a sony-specific one there. Lets have a closer look at it.

Also, can you go to the first tty (Ctr+Alt+F1), log in to the text console there and run:
```
showkey
```
...and press the Fn+F keys again and see if they are being registered (text will appear on-screen when you press them if they are being registered).

I tried to have a second look at your dmesg file, but it doesn't appear to be available anymore. Can you post it again?

One more thing, are there any settings in your bios about the function keys? Perhaps some way to handle them, etc.

---

### Post by Chris_Rutland on 2013-12-09
lsmod:

Module                  Size  Used by
hid_generic            12484  0 
usbhid                 46125  0 
hid                    87362  2 hid_generic,usbhid
arc4                   12509  2 
lib80211_crypt_wep     12746  1 
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211552  10 bnep,rfcomm
parport_pc             27612  0 
ppdev                  12849  0 
snd_hda_codec_realtek    65042  1 
gspca_vc032x           31446  0 
gspca_main             27978  1 gspca_vc032x
videodev               96131  2 gspca_vc032x,gspca_main
snd_hda_intel          38819  3 
snd_hda_codec         118650  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
i915                  550464  3 
snd_rawmidi            25157  1 snd_seq_midi
ipw2200               142022  0 
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17329  0 
libipw                 33469  1 ipw2200
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
tifm_sd                17526  0 
drm_kms_helper         47749  1 i915
snd_timer              28931  2 snd_pcm,snd_seq
drm                   233935  4 i915,drm_kms_helper
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1              12944  0 
pcmcia                 39854  0 
microcode              18433  0 
tifm_core              15068  2 tifm_sd,tifm_7xx1
cfg80211              453919  2 ipw2200,libipw
snd                    57014  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27427  0 
soundcore              12600  1 snd
psmouse                82769  0 
i2c_algo_bit           13316  1 i915
pcmcia_rsrc            18367  1 yenta_socket
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
serio_raw              13031  0 
lpc_ich                17048  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
lib80211               14040  3 lib80211_crypt_wep,ipw2200,libipw
sony_laptop            44993  0 
video                  19116  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35914  0 
firewire_core          62086  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
8139too                27407  0 
8139cp                 26687  0 

Unfortunately Showkey doesn't register anything.

My dmesg log again:
[http://paste.ubuntu.com/6545614/](http://paste.ubuntu.com/6545614/)

Thanks for your help

---

### Post by Chris_Rutland on 2013-12-09
Just had a look on PhoenixBios Setup Utility but apart from the hotkey event code under the Advanced tab (afraid I don't know what it does though) I don't think it looks encouraging unfortunately.

There are tabs for Main (Bios Version, System Details etc) 
Advanced (Drives, Network Boot, Hotkey Event Code:   [type1])
Security: Various Passwords
Boot (Optical Drive, Hard disk Drive, Floppy Disk Drive, Network)
Exit

---

### Post by Toz on 2013-12-09
> **Chris_Rutland said:**
> Just had a look on PhoenixBios Setup Utility but apart from the hotkey event code under the Advanced tab (afraid I don't know what it does though) I don't think it looks encouraging unfortunately.

There are tabs for Main (Bios Version, System Details etc) 
Advanced (Drives, Network Boot, Hotkey Event Code:   [type1])
Security: Various Passwords
Boot (Optical Drive, Hard disk Drive, Floppy Disk Drive, Network)
Exit

What are the available options for "Hotkey Event Code"?

---

### Post by Chris_Rutland on 2013-12-09
Hi again,

Type1
Type2
Type3

Thanks

---

### Post by Toz on 2013-12-09
I can't seem to find any documentation on this setting. Can you try each setting one at a time and see if makes a difference? Perhaps the bios changes the way it presents these keys to the O/S based on some criteria. When you boot after each change, check to see if the xev event from post #4 picks up the function keys.

---

