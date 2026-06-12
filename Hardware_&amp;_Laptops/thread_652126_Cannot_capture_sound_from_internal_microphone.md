---
title: "Cannot capture sound from internal microphone"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by blwegrzyn on 2007-12-28
I have a dell d630 and I am running ubuntu 7.10.  My sound card works fine besides the internal microphone. I cannot capture through it. I tried windows xp and everything is ok.
When I record something through record sound it is silence only.
How to troubleshoot that.
Below is some output that may be useful:
blwegrzyn@blwegrzyn-laptop:~$ 
blwegrzyn@blwegrzyn-laptop:~$ lsmod | grep snd
snd_hda_intel         375848  4 
snd_pcm_oss            47488  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                93832  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm
snd_hwdep              12168  1 snd_hda_intel
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62624  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27400  3 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69544  16 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
blwegrzyn@blwegrzyn-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 135M (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
blwegrzyn@blwegrzyn-laptop:~$ cat /proc/asound/
card0/   devices  Intel/   oss/     seq/     version  
cards    hwdep    modules  pcm      timers   
blwegrzyn@blwegrzyn-laptop:~$ cat /proc/asound/modules 
 0 snd_hda_intel
blwegrzyn@blwegrzyn-laptop:~$ cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 21
blwegrzyn@blwegrzyn-laptop:~$ cat /proc/asound/
card0/   devices  Intel/   oss/     seq/     version  
cards    hwdep    modules  pcm      timers   
blwegrzyn@blwegrzyn-laptop:~$ cat /proc/asound/pcm 
00-01: STAC92xx Digital : STAC92xx Digital : playback 1
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 2

thx

---

### Post by blwegrzyn on 2007-12-28
please look at the attachments to see what options are available in the mixersetup
also:
blwegrzyn@blwegrzyn-laptop:~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0- 1]: hardware dependent
  8: [ 0- 0]: hardware dependent
  9: [ 0]   : control
blwegrzyn@blwegrzyn-laptop:~$

---

### Post by blwegrzyn on 2007-12-28
also, i can record through input line, but not the build in mic

thx

---

### Post by nicolarsson on 2008-01-27
I have the same problem. Cannot use the internal microphone.
Which settings should be used in "Sound recorder"?

---

### Post by cthulhu666 on 2008-02-01
Have a look here: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

