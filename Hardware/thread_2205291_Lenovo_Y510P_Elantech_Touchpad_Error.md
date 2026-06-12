---
title: "Lenovo Y510P Elantech Touchpad Error"
date: 2014-02-13
forum: Hardware
---

### Post by jrtobac on 2014-02-13
xinput
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Optical USB Mouse                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=9    [slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                           id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Ideapad extra buttons                       id=14    [slave  keyboard (3)]


```

lsmod:
```
Module                  Size  Used by
nvidia               9430205  69 
snd_hda_codec_hdmi     37463  1 
coretemp               13596  0 
snd_hda_codec_realtek    79962  1 
snd_hda_intel          44339  5 
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
kvm                   456261  0 
snd_hwdep              13668  1 snd_hda_codec
bnep                   18399  2 
rfcomm                 47922  12 
parport_pc             28284  0 
ppdev                  17113  0 
ghash_clmulni_intel    13259  0 
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
aesni_intel            55495  2 
joydev                 17613  0 
hid_generic            12540  0 
ablk_helper            13597  1 aesni_intel
snd_seq_midi           13324  0 
cryptd                 20530  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lrw                    13323  1 aesni_intel
snd_rawmidi            30417  1 snd_seq_midi
aes_x86_64             17255  1 aesni_intel
uvcvideo               82214  0 
usbhid                 47346  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
arc4                   12573  2 
snd_timer              29989  2 snd_pcm,snd_seq
iwldvm                249122  0 
mac80211              631450  1 iwldvm
hid                   105826  2 hid_generic,usbhid
videobuf2_core         40815  1 uvcvideo
videodev              130172  2 uvcvideo,videobuf2_core
iwlwifi               183845  1 iwldvm
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
xts                    12951  1 aesni_intel
gf128mul               14951  2 lrw,xts
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
psmouse                97902  0 
cfg80211              526422  3 iwldvm,mac80211,iwlwifi
btusb                  22431  0 
mei                    45974  0 
snd                    69533  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
alx                    73500  0 
mac_hid                13253  0 
ideapad_laptop         18596  0 
serio_raw              13215  0 
sparse_keymap          13890  1 ideapad_laptop
mdio                   13807  1 alx
microcode              23075  0 
bluetooth             247324  24 bnep,rfcomm,btusb
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
video                  19652  0 
drm                   287796  3 nvidia
mxm_wmi                13021  0 
wmi                    19256  1 mxm_wmi
lpc_ich                17144  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
nls_iso8859_1          12713  1 
ahci                   25879  3 
libahci                31636  1 ahci


```

lsb_release -d 
```
Description:    Ubuntu 12.04.4 LTS
```

Touchpad can be clicked but that is it. I cannot move the pointer with the touchpad, can't right click, scroll, etc.

Do not have *[I] /etc/X11/*xorg.conf[/I] 
so the fix that has been posted for acer computers does not work [http://ubuntuforums.org/showthread.php?t=2071125](http://ubuntuforums.org/showthread.php?t=2071125)

Looking to enable the touchpad so it is fully customizable and I can turn on/off things like tap clicking

Thanks in advance for your help
[B]
**UDPATE**[/B]
```
sudo apt-get install xserver-xorg-input-synaptics
```

does work, I just didn't realize I needed to restart in order for it to take effect. sorry for the post

---

### Post by phidia on 2014-03-03
Actually I think this post is helpful for others looking for help with trackpad issues.
You could edit your post as solved and further that process. 

Off topic: I'm somewhat interested in the Y510P. How well would you say it works with Ubuntu?

---

