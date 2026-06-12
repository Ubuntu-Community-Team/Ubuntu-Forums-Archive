---
title: "Toshiba p100 sound problem"
date: 2008-05-09
forum: Hardware
---

### Post by kavatzoulas on 2008-05-09
hello from Greece.
i have a problem with the headphones output.
i am using Ubuntu 8.04 64bit ,i have a toshiba satellite P100-437 T7400 2gb ram Nvidia 7900gs 512mb.
i made a clean install everything works fine except the sound problem.
i have sound from the laptop speakes but when i want to insert the jack to hear the sound of a movie from my stereo system i get nothing -zero!!!
anybody with this problem?

i give the lspci output 
lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)

01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GS (rev a1)

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller

0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller

0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

0a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)


and the 
lsmod | grep snd

snd_hda_intel         440408  2 

snd_pcm_oss            47648  0 

snd_mixer_oss          20224  2 snd_pcm_oss

snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss

snd_page_alloc         13200  2 snd_hda_intel,snd_pcm

snd_hwdep              12552  1 snd_hda_intel

snd_seq_dummy           5764  0 

snd_seq_oss            38912  0 

snd_seq_midi           10688  0 

snd_rawmidi            29856  1 snd_seq_midi

snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi

snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              27912  2 snd_pcm,snd_seq

snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

snd                    70856  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

soundcore              10400  2 snd

---

### Post by thewarlock on 2008-05-09
Same effect here. (just checked)

I'll see what happens after I finish fixing the acpi thing.

---

### Post by kavatzoulas on 2008-05-17
the problem is solved.....
terminal:    gksu gedit /etc/modprobe.d/alsa-base
add 
options snd-hda-intel model=laptop-micsense

save

thats all

special thanks to 
[https://bugs.launchpad.net/ubuntu/+bug/218817](https://bugs.launchpad.net/ubuntu/+bug/218817)

---

