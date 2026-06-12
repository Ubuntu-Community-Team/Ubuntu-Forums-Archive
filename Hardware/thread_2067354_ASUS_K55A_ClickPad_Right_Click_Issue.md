---
title: "ASUS K55A ClickPad Right Click Issue"
date: 2012-10-06
forum: Hardware
---

### Post by nowashburn on 2012-10-06
Hello, I just bought an ASUS K55A and immediately put Ubuntu 12.04 on it. So far so good, but for whatever reason the clickpad seems a little off to me. The clickpad has two areas on the bottom left and bottom right that are physically clickable. In my initial windows 7 startup, these areas were left and right click respectively and I would like it to behave the same way in Ubuntu as it does seem more natural and easier to use. Right now both buttons result in a left click. 

Also, I accidentally realized that the clickpad handles mouse clicks in the following manner:

- A single tap on the pad anywhere = left click
- Two quick taps on the pad anywhere = right click
- Three quick taps on the pad anywhere = a strange circle with arrows appears in the middle of the screen. Not sure what to do here.

Dragging and everything else I tested / needed seem to work fine, it's just that darn right click area that I would like to change. Any Suggestions? Thanks!

---

### Post by nowashburn on 2012-10-08
nothing eh :/

---

### Post by varunendra on 2012-10-11
I am posting this from my Asus X54C, and based on the specs I could find for your model, I think yours is more or less the same touchpad as mine (ETPS/2 Elantech Touchpad). However, the touchpad behaviour in my case is as follows:
- a single tap anywhere on the touchpad = left-click
- a two-finger tap anywhere on the touchpad = right-click
- two or three quick taps behave same as they do with normal moue two/three left-clicks (select word/paragraph)

IIRC, I had to manually enable the 'two-finger scrolling' function in "System Settings > Mouse > Touchpad" tab.

The circle with arrows you mentioned is, I guess, the 'rotate' function of the touchpad which only works in windows 7 in my laptop (I'm still dual booting with it). I am using 'psmouse' driver with my touchpad, but can't say if that is the reason for the difference in behaviour.

Please post the outputs of :
```
xinput -list
lsmod
```
to let us have a peek at your input devices and loaded drivers. I think you must have already played with settings in "System Settings > Mouse > Touchpad". If not, try altering some settings there (although I can't see anything relevant to your problem there).

---

### Post by nowashburn on 2012-10-17
> **varunendra said:**
> 
Please post the outputs of :
```
xinput -list
lsmod
```


xinput -list:
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; ASUS USB2.0 Webcam                      	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

```
lsmod:
```

Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23199  15244400589488568 [permanent]
vboxnetadp             13382  14412373197595967675 [permanent]
vboxnetflt             23441  7130872889771857359 [permanent]
vboxdrv               287104  481650285748355819 vboxpci,vboxnetadp,vboxnetflt,[permanent]
bnep                   18190  2 
rfcomm                 47012  0 
bluetooth             206685  10 bnep,rfcomm
parport_pc             32734  0 
ppdev                  17180  0 
binfmt_misc            17498  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17535  1 
fat                    61245  1 vfat
iptable_filter         12810  0 
iptable_mangle         12695  0 
iptable_nat            13182  0 
nf_nat                 25339  1 iptable_nat
nf_conntrack_ipv4      19630  3 iptable_nat,nf_nat
nf_conntrack           82962  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
ip_tables              27227  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               29728  4 iptable_filter,iptable_mangle,iptable_nat,ip_tables
snd_hda_codec_hdmi     32111  1 
snd_hda_codec_realtek    77948  1 
uvcvideo               72690  0 
videobuf2_core         32801  1 uvcvideo
videodev              111615  1 uvcvideo
snd_hda_intel          33332  3 
snd_hda_codec         123847  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13652  1 snd_hda_codec
snd_pcm                97231  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
snd_seq_midi           13324  0 
usbhid                 46836  0 
hid                    99833  1 usbhid
arc4                   12529  2 
snd_rawmidi            30655  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k                 139686  0 
mac80211              519398  1 ath9k
ath9k_common           14057  1 ath9k
ath9k_hw              405977  2 ath9k,ath9k_common
snd_seq                61538  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29708  2 snd_pcm,snd_seq
snd_seq_device         14490  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17597  0 
coretemp               13602  0 
snd                    79086  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath                    23896  3 ath9k,ath9k_common,ath9k_hw
i915                  484383  4 
ghash_clmulni_intel    13180  0 
drm_kms_helper         46958  1 i915
drm                   265069  5 i915,drm_kms_helper
asus_wmi               24281  0 
sparse_keymap          13890  1 asus_wmi
aesni_intel            51530  2 
soundcore              14996  1 snd
cfg80211              202006  3 ath9k,mac80211,ath
cryptd                 20396  2 ghash_clmulni_intel,aesni_intel
psmouse                87589  0 
mac_hid                13205  0 
i2c_algo_bit           13509  1 i915
video                  19280  1 i915
snd_page_alloc         18572  2 snd_hda_intel,snd_pcm
aes_x86_64             17208  1 aesni_intel
serio_raw              13211  0 
microcode              22945  0 
mei                    40904  0 
wmi                    19141  1 asus_wmi
lp                     17789  0 
parport                46360  3 parport_pc,ppdev,lp
r8169                  61681  0

```

---

### Post by varunendra on 2012-10-18
> **nowashburn said:**
> xinput -list:

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; ASUS USB2.0 Webcam                      	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

lsmod:

Module                  Size  Used by
[COLOR="Red"]**usbhid**[/COLOR]                 46836  0 
hid                    99833  1 usbhid
..
<snip>
..
psmouse                87589  0 
So the touchpad is indeed detected to be same as mine, and also the driver psmouse is there. But I don't see any USB mouse or keyboard in your xinput list which use the usbhid driver. So just as a blind shot, please try removing it, and removing -> reloading psmouse driver also-
(please note that after executing the 2nd command, the touchpad should stop working. But it will get functional again after executing the 3rd command):
```
sudo modprobe -rfv usbhid
sudo modprobe -rfv psmouse
sudo modprobe -v psmouse
```

Just for reference, my xinput -list output is this:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; **[COLOR="red"]ETPS/2 Elantech Touchpad[/COLOR]**                	id=14	[slave  pointer  (2)]
&#9116;   &#8627; **Logitech USB Optical Mouse**              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Generic USB K/B                         	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; ASUS USB2.0 WebCam                      	id=9	[slave  keyboard (3)]
    &#8627; **Generic USB K/B**                         	id=12	[slave  keyboard (3)]

```

Note that I do have a USB mouse and keyboard attached (via a USB hub), and as far as I could notice, these are the only things that get disabled after removing *usbhid* driver. So yes, I also have *usbhid* loaded along with *psmouse* but it's not causing any troubles with psmouse.
That's why I'm calling it a 'blind' shot. :) The idea is to use only what you need, and see if it helps.

**PS:**
Please edit your above post to enclose the outputs in 'Code' tags. It makes the code more readable by preserving its formatting, and thus also makes the post look tidy.
To do so, just add [noparse]```
 in the beggining of the code, and 
```[/noparse] at its end. Or, in advanced edit mode, just highlight the code text, then click on **#** symbol to auto generate these tags around the highlighted area.

---

### Post by nowashburn on 2012-11-12
> **varunendra said:**
> So the touchpad is indeed detected to be same as mine, and also the driver psmouse is there. But I don't see any USB mouse or keyboard in your xinput list which use the usbhid driver. So just as a blind shot, please try removing it, and removing -> reloading psmouse driver also-
(please note that after executing the 2nd command, the touchpad should stop working. But it will get functional again after executing the 3rd command):
```
sudo modprobe -rfv usbhid
sudo modprobe -rfv psmouse
sudo modprobe -v psmouse
```

Just for reference, my xinput -list output is this:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; **[COLOR="red"]ETPS/2 Elantech Touchpad[/COLOR]**                	id=14	[slave  pointer  (2)]
&#9116;   &#8627; **Logitech USB Optical Mouse**              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Generic USB K/B                         	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; ASUS USB2.0 WebCam                      	id=9	[slave  keyboard (3)]
    &#8627; **Generic USB K/B**                         	id=12	[slave  keyboard (3)]

```

Note that I do have a USB mouse and keyboard attached (via a USB hub), and as far as I could notice, these are the only things that get disabled after removing *usbhid* driver. So yes, I also have *usbhid* loaded along with *psmouse* but it's not causing any troubles with psmouse.
That's why I'm calling it a 'blind' shot. :) The idea is to use only what you need, and see if it helps.

**PS:**
Please edit your above post to enclose the outputs in 'Code' tags. It makes the code more readable by preserving its formatting, and thus also makes the post look tidy.
To do so, just add [noparse]```
 in the beggining of the code, and 
```[/noparse] at its end. Or, in advanced edit mode, just highlight the code text, then click on **#** symbol to auto generate these tags around the highlighted area.

Thanks for the reply and sorry for the delayed response. I upgraded to 12.10 an now it works as expected.I dont know what actually changed but maybe this thread will help someone else with the same or a similar issue.

---

### Post by varunendra on 2012-11-12
You're welcome ! and...> **nowashburn said:**
> maybe this thread will help someone else with the same or a similar issue...please mark the thread as **[Solved]** using '**Thread Tools**' to help this cause :) (see 'how to' in my sig.)

---

