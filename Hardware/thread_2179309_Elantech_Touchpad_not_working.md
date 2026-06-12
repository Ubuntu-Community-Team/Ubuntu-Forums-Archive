---
title: "Elantech Touchpad not working"
date: 2013-10-07
forum: Hardware
---

### Post by Keith_Valin on 2013-10-07
I can't get my elantech touchpad working at all.  HELP!!

---

### Post by varunendra on 2013-10-10
> **Keith_Valin said:**
> I can't get my elantech touchpad working at all.  HELP!!

Welcome to the forums Keith !

If you are still on it, please post back the outputs of -
```
lsb_release -d
uname -mr
xinput
lsmod
```

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by Keith_Valin on 2013-10-12
Can't find the link.

---

### Post by varunendra on 2013-10-12
> **Keith_Valin said:**
> Can't find the link.

Which link? The one about the code tags? Here it is : [http://ubuntuforums.org/showpost.php?p=12776168](http://ubuntuforums.org/showpost.php?p=12776168)

The commands you have to enter (or copy-paste) in a terminal which can be opened with Ctrl+Alt+T shortcut.

---

### Post by Keith_Valin on 2013-10-15
```

lsb_release -d
Description:	Ubuntu 12.04.3 LTS

uname -mr
3.2.0-54-generic x86_64



xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:1025	id=9	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Toshiba input device                    	id=12	[slave  keyboard (3)]

lsmod
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23237  0 
vboxnetadp             13382  0 
vboxnetflt             23478  0 
vboxdrv               287130  3 vboxpci,vboxnetadp,vboxnetflt
vesafb                 13844  1 
bnep                   18281  2 
rfcomm                 47604  4 
bluetooth             180113  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_conexant    62317  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_intel          33719  7 
snd_hda_codec         127706  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
fglrx                6725632  87 
rtl8188ee             138276  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
rtlwifi               123347  1 rtl8188ee
mac80211              506862  2 rtl8188ee,rtlwifi
snd_timer              29990  2 snd_pcm,snd_seq
cfg80211              205774  2 rtlwifi,mac80211
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17693  0 
mac_hid                13253  0 
snd                    79041  24 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17540  1 
toshiba_acpi           18582  0 
video                  19651  0 
i2c_piix4              13301  0 
sparse_keymap          13890  1 toshiba_acpi
wmi                    19256  1 toshiba_acpi
psmouse                97519  0 
serio_raw              13211  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
fam15h_power           13159  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_logitech_dj        18730  0 
usbhid                 47238  1 hid_logitech_dj
hid                    99636  2 hid_logitech_dj,usbhid



```

---

### Post by varunendra on 2013-10-15
So it's detected and the correct driver (psmouse) is also loaded for it. Maybe a bug in xorg causing it to get lost during startup. Have you tried updating the system? Apparently, such problems are often solved by newer kernel updates.

For now, see if this makes it active -
```
xinput float "ETPS/2 Elantech Touchpad"
[s]xinput reattach "ETPS/2 Elantech Touchpad" "Virtual **[COLOR="#FF0000"]C[/COLOR]**ore **[COLOR="#FF0000"]P[/COLOR]**ointer"[/s]
xinput reattach "ETPS/2 Elantech Touchpad" "Virtual core pointer"
```
[COLOR="#FF0000"](**EDIT:** Corrected the second command)[/COLOR]

If not, also try (with or without above) -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse
```

If an update fixes it, very good. If not, we can make the above workaround easier, probably automatic.

---

### Post by Keith_Valin on 2013-10-15
Ok I ran the commands that you gave me through the terminal this is the output.
```

xinput float "ETPS/2 Elantech Touchpad"

xinput reattach "ETPS/2 Elantech Touchpad" "Virtual Core Pointer"
unable to find device Virtual Core Pointer

sudo modprobe -rv psmouse
rmmod /lib/modules/3.2.0-54-generic/kernel/drivers/input/mouse/psmouse.ko

sudo modprobe -v psmouse
insmod /lib/modules/3.2.0-54-generic/kernel/drivers/input/mouse/psmouse.ko 

```

Rebooted, still didn't work, any other ideas?

---

### Post by varunendra on 2013-10-15
My bad ! The "Core Pointer" was in small letters -
> **Keith_Valin said:**
> ```
xinput
&#9121; **Virtual [COLOR="#FF0000"]core pointer[/COLOR]**                    	id=2	[master pointer  (3)]

```

So the second command should have been -
```
xinput reattach "ETPS/2 Elantech Touchpad" "Virtual **c**ore **p**ointer"
```

Please try that again and report back.

**PS:**
You can also use the IDs instead of names, but the ID of the touchpad may change on each reboot (most probably being 10, 11 or 12), although the ID of the Master Pointer would stay the same (2). So the command (assuming the touchpad's ID is 11) could also be of the form -
```
xinput float 11
xinput reattach 11 2
```
But this will change depending upon touchpad's ID on each reboot, so using the name string is a better approach.

**PPS:** Please also note that these xinput changes don't carry across reboot. So don't reboot after running the commands. If it makes it work, we can make it permanent by other means.

---

### Post by Keith_Valin on 2013-10-20
Still nothing.  What next?

---

### Post by varunendra on 2013-10-22
> **Keith_Valin said:**
> Still nothing.  What next?

I would suspect a broken update. Please try this -
```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

If that does not help, I would suggest to try upgrading to the latest kernel available by default, by installing "linux-generic-lts-raring" package and simultaneously upgrade to the relevant xorg packages as well (as recommended in the [wiki page here]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")) -
```
sudo apt-get install --install-recommends linux-generic-lts-raring xserver-xorg-lts-raring libgl1-mesa-glx-lts-raring
```

---

