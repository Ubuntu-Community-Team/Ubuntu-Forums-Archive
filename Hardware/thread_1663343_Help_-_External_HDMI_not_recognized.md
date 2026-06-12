---
title: "Help - External HDMI not recognized"
date: 2011-01-09
forum: Hardware
---

### Post by jcllings on 2011-01-09
Hardware: 
Sony Vaio VPCF115FM
nVidia 
GT 330M
HDMI Monitor is an Acer model H233H 

Situation: Go to -

     System Settings | Display and Monitor 

What I notice is that I can see VGA1, DVI1 and LVDS (connected) under "Size and Orientation" however VGA1 and DVI1 are disabled when it comes to changing anything. See attached pictures. 

Problem: How do I get my Acer HDMI monitor to be recognized and functional?

---

### Post by jcllings on 2011-01-09
BTW some more info on the system in question: 

It is actually Kubuntu. 

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.10
Release:        10.10
Codename:       maverick

Linux XXXXXXXX 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux


jim@XXXXXXXX:~$ lsmod 
Module                  Size  Used by
nls_iso8859_1           4657  1 
nls_cp437               6375  1 
vfat                   10954  1 
fat                    56244  1 vfat
mmc_block               9971  0 
joydev                 11395  0 
usbhid                 42062  0 
hid                    84710  1 usbhid
usb_storage            50372  1 
rfcomm                 40787  6 
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
sco                     9986  2 
bnep                   11985  2 
l2cap                  42304  16 rfcomm,bnep
snd_hda_codec_nvhdmi    15451  4 
snd_hda_codec_realtek   299844  1 
arc4                    1497  2 
nvidia              10221046  0 
snd_hda_intel          26019  3 
snd_hda_codec         100919  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
ath9k                 101730  0 
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
ath9k_common            6874  1 ath9k
ath9k_hw              314699  2 ath9k,ath9k_common
snd_seq_midi            5932  0 
ath                    10413  2 ath9k,ath9k_hw
mac80211              266625  2 ath9k,ath9k_common
snd_rawmidi            22207  1 snd_seq_midi
cfg80211              170293  4 ath9k,ath9k_common,ath,mac80211
uvcvideo               62379  0 
videodev               49359  1 uvcvideo
snd_seq_midi_event      7291  1 snd_seq_midi
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev                                                                                                                                                                                                                                       
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event                                                                                                                                                                                                                
snd_timer              23850  2 snd_pcm,snd_seq                                                                                                                                                                                                                                
btusb                  12929  2                                                                                                                                                                                                                                                
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb                                                                                                                                                                                                                    
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq                                                                                                                                                                                                               
snd                    64181  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device                                                                                                                              
i7core_edac            18122  0                                                                                                                                                                                                                                                
psmouse                62080  0                                                                                                                                                                                                                                                
serio_raw               4910  0                                                                                                                                                                                                                                                
edac_core              46822  1 i7core_edac                                                                                                                                                                                                                                    
soundcore               1240  1 snd                                                                                                                                                                                                                                            
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm                                                                                                                                                                                                                          
sony_laptop            34416  0                                                                                                                                                                                                                                                
video                  22176  0                                                                                                                                                                                                                                                
output                  2527  1 video                                                                                                                                                                                                                                          
lp                     10201  0                                                                                                                                                                                                                                                
parport                37032  3 parport_pc,ppdev,lp                                                                                                                                                                                                                            
firewire_ohci          24615  0                                                                                                                                                                                                                                                
sky2                   53371  0                                                                                                                                                                                                                                                
firewire_core          54327  1 firewire_ohci                                                                                                                                                                                                                                  
ahci                   22210  3                                                                                                                                                                                                                                                
sdhci_pci               7765  0                                                                                                                                                                                                                                                
libahci                26052  1 ahci
sdhci                  18400  1 sdhci_pci
led_class               3393  2 ath9k,sdhci
crc_itu_t               1739  1 firewire_core

---

### Post by jcllings on 2011-01-16
Hello? Anybody?

---

### Post by jcllings on 2012-06-08
Conclusion: Support for this model was abysmal on all sides.  Bottom line: Don't buy department store laptops. Get em certified for Linux online.

---

