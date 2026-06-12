---
title: "HP 620 Wifi/bluetooth and fan problem"
date: 2011-05-18
forum: Hardware
---

### Post by chaemil on 2011-05-18
HI there. i've just bought the new laptop for my friend. It's HP 620 with SLED 11 preinstalled. but she wants Ubuntu. SO i've tried the live USB 11.04 and the laptop is working but i've issues with, wifi/bluetooth combo device (Ralink RT3090), and the fan after wake went to 100% and wont slow down. So if you have any suggestions how to transforms drivers from SLED 11 to Ubuntu 11.04 let my now... Thanks

---

### Post by meijer.o on 2011-05-18
Dear Linux user:

I don't know how to solve the wireless problem. Make a separate post and mention the type of your wireless card. If it works with Suse, it should work with Ubuntu as well.

I found a solution for the fan at full speed after sustpend (I own a HP ProBook). It might work on your computer as well

Copy the following script to /etc/pm/sleep.d and make it executable.

#!/bin/sh
#
# avoid max fan speed after resume
# position /etc/pm/sleep.d/11_fan_2.6.38



case "$1" in
        hibernate|suspend)
# do nothing

                ;;



        thaw|resume)
sleep 1
echo -n 1 > /sys/class/thermal/cooling_device0/cur_state
sleep 2
echo -n 0 > /sys/class/thermal/cooling_device0/cur_state



                ;;

# end script

Best regards,

otto


esac

---

### Post by PowerBarry43 on 2011-05-18
You can get a wireless driver if you go to system/administration/additional drivers and then enable the broadcom STA proprietary wireless driver thats what i had to do on my HP G62 laptop other than that i dont know :/

---

### Post by chaemil on 2011-05-18
i've got there the rt3090sta driver which i've downloaded here [https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090). but the driver is activated but not in use... how can i use it? o know it have something to do with unloading modules and loading the new one... but how?

---

### Post by chaemil on 2011-05-18
it looks like this:

[ATTACH]192537[/ATTACH]

i don't know how to enable it.

i've tryied the 

```

dkms status

```

ant it printed out

```

rt3090, 2.4.0.4, 2.6.38-8-generic, i686: installed 

```

but it's not in the list of modules

```

julinka@julinka-laptop:~$ lsmod
Module                  Size  Used by
rfcomm                 38125  8 
binfmt_misc            13213  1 
sco                    17779  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
usbhid                 41704  0 
arc4                   12473  2 
hid                    77084  1 usbhid
snd_timer              28659  2 snd_pcm,snd_seq
rt2800pci              18159  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2800lib              43824  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              13986  1 rt2800pci
uvcvideo               66851  0 
btusb                  18160  2 
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
videodev               75143  1 uvcvideo
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
eeprom_93cx6           12653  1 rt2800pci
serio_raw              12990  0 
cfg80211              156212  2 rt2x00lib,mac80211
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  450944  5 
drm_kms_helper         40745  1 i915
drm                   180037  6 i915,drm_kms_helper
ahci                   21591  3 
libahci                25548  1 ahci
i2c_algo_bit           13184  1 i915
r8169                  42534  0 
video                  18951  1 i915

```

---

### Post by jwvdhoek on 2011-05-27
@chaemil: my problems with Wifi not working properly were gone after adding the following line to the end of the file /etc/modprobe.d/blacklist.conf:  blacklist rt2800pci

---

### Post by carimbonon on 2011-06-20
My problem with a fresh install of Ubuntu 11.04 was solved with the blacklist line ! !  
In my case the blue led of the WiFi button was blinking  blue and orange all the time. Now works fine and the led is blue all the time. The only problem is that the **WiFi button works BUT it doesn't change color to orange**... I mean "the button works but the color doesn't change when the WiFi is off".

Thank you very much for the trick !

---

### Post by kemamikro on 2011-07-09
> **jwvdhoek said:**
> @chaemil: my problems with Wifi not working properly were gone after adding the following line to the end of the file /etc/modprobe.d/blacklist.conf:  blacklist rt2800pci

Works grate!

My HP620 was very slow to connect througt wifi and wont turn off, hibernate, restart, etc...

Adding the line, everything solved!

Thank you very much.

---

### Post by Deafboy on 2011-07-21
Thanks guys. I was trying to solve this issue since Christmas. I have wanted to buy HP 620 with Suse but it was sold out.

---

### Post by watmeto on 2011-08-26
Yeaah it works. THanks a lof. But i don t understand what does this line do: > blacklist rt2800pci Can you explain us what does it do ?

---

