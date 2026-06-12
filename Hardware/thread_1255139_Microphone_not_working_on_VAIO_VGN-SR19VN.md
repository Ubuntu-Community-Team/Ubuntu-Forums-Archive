---
title: "Microphone not working on VAIO VGN-SR19VN"
date: 2009-09-01
forum: Hardware
---

### Post by Picapillo on 2009-09-01
Hello everybody.

THE PROBLEM: 
I have been using Ubuntu in my VAIO VGN-SR19VN laptop almost for a year. The first version I installed was 8.10, then I upgraded to 9.04. Both of them behaved rather well. Particularly the audio was working ok, that is, I could hear sounds, but there was trouble with the microphone, which did not capture any input sound. Ubuntu recognized the internal microphone of my laptop, but when I tried to record something with the recorder, it wouldn't work: it did not record anything but the static garbage sound.

ATTEMPTS TO SOLVE THE PROBLEM:
I tried all possible stuff I found on several websites.
-I tried different configurations of parameters with Volume controller, particularly enabling the Capture and Microphone items and setting the volume to maximum.
-I used alsamixer to ensure volumes of all audio items were not muted.
-I followed the steps listed here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
to solve problems with hda-intel sound cards (my Audio Codec is Realtek ALC262): I modified the alsa-base.conf file attaching these lines at the end of the file:
options snd-hda-intel model=vaio
options snd-hda-intel model=3stack
and I upgraded to the last version of ALSA
-Since none of these attempts worked, I gave up. But after a couple of days, the battle continued.
I found somewhere that this was an ALSA bug (because there were a lot of people that had the same issue with different Sony, Toshiba and other laptops) and that it would get fixed in future version of ALSA.
I upgraded to the last version of ALSA, 1.0.20 but the problem is still there.

DETAILS OF MY SYSTEM:

```
Laptop: Sony VAIO VGN-SR19VN
OS: Ubuntu 9.04
Kernel Version: 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux
```Alsa Information Script: [http://www.alsa-project.org/db/?f=cf08606cf41b6779d2c2332b987bdc3432ccb36c](http://www.alsa-project.org/db/?f=cf08606cf41b6779d2c2332b987bdc3432ccb36c)

Audio Codecs:
```
Codec: Realtek ALC262
Codec: Conexant ID 2c06
```lspci output:

```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
05:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
07:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
```lsmod output:

```
Module                  Size  Used by
isofs                  39844  1 
udf                    87716  0 
crc_itu_t              10112  1 udf
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18496  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_codec_realtek   205060  1 
snd_hda_intel          34120  3 
snd_hda_codec          83584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              15364  1 snd_hda_codec
snd_pcm_oss            45984  0 
snd_mixer_oss          22912  1 snd_pcm_oss
arc4                    9856  2 
snd_pcm                82948  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ecb                    10752  2 
snd_seq_dummy          10884  0 
snd_seq_oss            36224  0 
snd_seq_midi           14240  0 
iwlagn                100228  0 
snd_rawmidi            29984  1 snd_seq_midi
iwlcore                93184  1 iwlagn
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57584  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               63368  0 
snd_timer              29320  2 snd_pcm,snd_seq
led_class              12036  1 iwlcore
snd_seq_device         15372  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
compat_ioctl32          9344  1 uvcvideo
mac80211              217592  2 iwlagn,iwlcore
snd                    66852  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               41600  1 uvcvideo
sdhci_pci              15232  0 
psmouse                61972  0 
soundcore              15200  1 snd
fglrx                2081668  31 
video                  25360  0 
v4l1_compat            21764  2 uvcvideo,videodev
sdhci                  23940  1 sdhci_pci
pcspkr                 10496  0 
btusb                  19608  2 
snd_page_alloc         17032  2 snd_hda_intel,snd_pcm
serio_raw              13444  0 
cfg80211               38288  3 iwlagn,iwlcore,mac80211
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
tpm_infineon           16936  0 
tpm                    22976  1 tpm_infineon
tpm_bios               14080  1 tpm
sony_laptop            41052  0 
output                 11008  1 video
intel_agp              34108  0 
agpgart                42696  2 fglrx,intel_agp
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```QUESTIONS:
Has anybody had similiar problems? Does anybody know how I should proceed in order to fix the issue?
Thanks a lot for your help.

Picapillo

---

### Post by fernandoch on 2009-09-09
We have almost the same laptop. I have an VGN SR 21M and I haven't tried the mic yet. Can you adjust the brightness correctly? Do your top buttons work with Ubuntu 9.04?

Have you checked this: 

[http://www.linlap.com/wiki/sony+vaio+sr](http://www.linlap.com/wiki/sony+vaio+sr)

I am not using that kernel. I have an older one. What about you?

---

### Post by net.ricky on 2009-09-20
I have the same laptop and the same problem :(
External microphone works fine. When I try to record audio from internal microphone what I listen is only some noise in background. So internal mic seems to work and seems to be a problem of volume.
Ani idea ??? 
Someone can help us?
Thanks

---

### Post by net.ricky on 2009-09-20
Finally I find a solution. It's not a completely satisfactory solution but it works! What seems to be is that neither alsa mixer 1.21 support well our sound card. What people do is to set in 
/etc/modprobe.d/alsa-base.conf
is
options snd-hda-intel model=toshiba-s06
and reboot.
After run alsamixer and in capture screen you can select internal or external microphone.
What it's annoying is that you can't set separatly headphone volume level. But internal microphone works! ;)

If someone find another solution, please write it here!

Bye

---

### Post by FreshP on 2009-12-03
Same thing here, i got the microphone to work, with some noise in the background though, but i cant use the hotkeys to change the volume now. I can change it only from the alsamixer master channel. Sucks....... booting to windows to use skype.

I have VGN-FW510F.

---

### Post by FreshP on 2009-12-04
Well, finally i got the mic to work and the volume control buttons. I did play with the settings in preferences>sound, i dont remember exactly what i did, i think the buttons were not working because i had chosen the graphics card in the Hardware tab, instead of the internal audio.

---

### Post by parthab on 2009-12-11
> **FreshP said:**
> Same thing here, i got the microphone to work, with some noise in the background though, but i cant use the hotkeys to change the volume now. I can change it only from the alsamixer master channel. Sucks....... booting to windows to use skype.

I have VGN-FW510F.
I have the VGN-FW129E. The internal mic does work if you set the computer to a Toshiba! However, you will notice that it stops working after sometime if you don't use it for awhile. To reactivate it, I have to insert an external mic momentarily and it will start again, ... till it stops again. So, still need the external mic. 

Again, it will work for sometime. If you have it working continuously then it should be OK. If you don't use for sometime, it will stop working till you insert an external mic.

Partha

---

### Post by Bdiah on 2010-06-13
I know its been a while, but I was wondering if we have a better solution for this.

I am running an SR490 with 9.10 and still encountering the same issues regarding the microphone.  The line edit of the alsa-base.conf file did not work for me.

---

### Post by industry on 2010-10-18
> **net.ricky said:**
> Finally I find a solution. It's not a completely satisfactory solution but it works! What seems to be is that neither alsa mixer 1.21 support well our sound card. What people do is to set in 
/etc/modprobe.d/alsa-base.conf
is
options snd-hda-intel model=toshiba-s06
and reboot.
After run alsamixer and in capture screen you can select internal or external microphone.
What it's annoying is that you can't set separatly headphone volume level. But internal microphone works! ;)


If someone find another solution, please write it here!

Bye

I have a Sony VAIO VGN-NW270T and...
This worked really good for me. Thanks a lot!

---

### Post by FreshP on 2010-12-16
After making a clean install of Ubuntu 10.10, the internal microphone works out of the box, and without some minor problems I was facing before. 

(Unfortunately, a bunch of other stuff dont work well in 10.10, like suspending computer, brightness function key, connecting an IPOD shuffle, adding external monitor (asks for logging out and back in))

I am considering going back to 9.10 for these reasons.

---

