---
title: "USB-to-Parallel Printer Completely Crashes System"
date: 2011-05-09
forum: Hardware
---

### Post by fcoster on 2011-05-09
A long time ago, (9.10) I had trouble getting my HP Laserjet 6P running, as described [here]("http://ubuntuforums.org/showthread.php?t=1289329").

I've just installed 11.04 and I'm having printing trouble again. The system has recognized the printer: HP-LaserJet-6P appears in the printing menu, listing hpcups 3.11.1 as the driver and [FONT="Courier New"]usb://HP/LaserJet%206P[/FONT] as the device URI. 

I cannot print, however. And when I try to Change the device URI (as when I previously had this problem) the computer crashes--it becomes completely unresponsive (screen freezes; no response to Ctrl-Alt-Del) l and requires a hard reboot. If I delete the printer and try to add a new one the same thing happens. Output of lsmod, and relevant bits of lsusb and dmesg below.

**lsmod**
```
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
usblp                  17827  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
nvidia               9766978  54 
arc4                   12473  2 
snd_usb_audio          91410  1 
snd_pcm                80244  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_hwdep              13274  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
b43                   296610  0 
mac80211              257001  1 b43
cfg80211              156212  2 b43,mac80211
snd                    55295  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uss720                 17981  3 
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
psmouse                73312  0 
asus_atk0110           17664  0 
k10temp                12951  0 
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
lp                     13349  0 
parport                36746  4 parport_pc,ppdev,uss720,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ssb                    45942  1 b43
sata_nv                23176  3 
pata_amd               13762  0 
forcedeth              58190  0 
```

**After the printer is plugged in via USB, dmesg:**

```

[ 4690.432055] usb 2-5: new full speed USB device using ohci_hcd and address 6
[ 4694.132981] parport2: Printer, Hewlett-Packard HP LaserJet 6P
[ 4694.132990] parport2: fix this legacy no-device port driver!
[ 4694.133163] lp2: using parport2 (polling).
[ 4714.811967] usb 2-5: USB disconnect, address 6
[ 4762.632055] usb 2-5: new full speed USB device using ohci_hcd and address 7
[ 4766.334990] parport3: Printer, Hewlett-Packard HP LaserJet 6P
[ 4766.335000] parport3: fix this legacy no-device port driver!
[ 4766.335172] lp3: using parport3 (polling).

```

**And lsusb see this:**
```
Bus 002 Device 007: ID 050d:0002 Belkin Components
```

Any help anyone?

---

