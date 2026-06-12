---
title: "No sound with HDA Intel"
date: 2010-03-30
forum: Hardware
---

### Post by VirusCollector on 2010-03-30
Hello, this is driving me insane. I get no sound at all, after a long and epic battle over sound in Skype. The only problem I used to have with sound is the loss of it on system resume, but this was fixable by sudo alsa-utils force-reload. Then I installed Skype...

I don't know what version I had before, but it wasn't far behind what's available now. Both versions suddenly stopped making any sound at all. This time, they messed up my general sound configuration, however. Now I get no sound at all from any program. Doing the alsa-utils method as described before would ordinarily reset my sound controls and mute the volume, but now it doesn't touch the volume at all and does nothing.

In my quest for a solution, I've purged pulseaudio and alsa and reinstalled them for esound(this did not work). However, in the process I did manage to recover the actual name of my sound hardware, which previously was replaced with "Dummy Output". I also upgraded my ALSA to 1.22 or whatever is most recent using the AlsaUpgrade.sh script.

Help pleeease. I'm considering just reinstalling.

Output from dmesg, lspci, and lsmod.

```

Output from dmesg concerning my card:

[    9.392514] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0                
[    9.392528]   alloc irq_desc for 22 on node 0                                        
[    9.392531]   alloc kstat_irqs on node 0                                             
[    9.392539] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22       
[    9.392607]   alloc irq_desc for 31 on node 0                                        
[    9.392609]   alloc kstat_irqs on node 0                                             
[    9.392623] HDA Intel 0000:00:1b.0: irq 31 for MSI/MSI-X                             
[    9.392664] HDA Intel 0000:00:1b.0: setting latency timer to 64                      
[    9.604897] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9                                                                                       
[    9.640449] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10                                                                    
[    9.640536] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11 




Output from lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)                                                                                  
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)                                                                 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)                                                                        
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)                                                                                  
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)                                                                                  
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)                                                                                 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)                                                                                       
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)  
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)  
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)  
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)




Output from lsmod:


Module                  Size  Used by                                                   
nfnetlink_queue        10596  1                                                         
nfnetlink               5808  2 nfnetlink_queue                                         
binfmt_misc            10220  1                                                         
nf_conntrack_ipv4      16376  3                                                         
nf_defrag_ipv4          2400  1 nf_conntrack_ipv4                                       
ipt_REJECT              3584  1                                                         
xt_tcpudp               3616  2                                                         
xt_iprange              2720  0                                                         
xt_state                2432  3                                                         
nf_conntrack           80800  2 nf_conntrack_ipv4,xt_state                              
xt_mark                 2464  6                                                         
xt_NFQUEUE              3232  3                                                         
ppdev                   8232  0                                                         
vboxnetflt            100300  0                                                         
vboxnetadp             93292  0                                                         
vboxdrv              1708524  1 vboxnetflt                                              
deflate                 3552  0                                                         
zlib_deflate           22584  1 deflate                                                 
ctr                     5216  0                                                         
twofish                 6560  0                                                         
twofish_common         15200  1 twofish                                                 
camellia               19840  0                                                         
serpent                19104  0                                                         
blowfish                8512  0                                                         
cast5                  15904  0                                                         
des_generic            17408  0                                                         
cbc                     4224  0                                                         
cryptd                  8008  0                                                         
aes_x86_64              8992  0                                                         
aes_generic            28480  1 aes_x86_64                                              
xcbc                    5640  0                                                         
rmd160                  8768  0                                                         
sha256_generic         10816  0                                                         
sha1_generic            2656  0                                                         
crypto_null             3872  0                                                         
af_key                 32272  0                                                         
snd_hda_codec_idt      66224  1                                                         
snd_hda_intel          30208  3                                                         
snd_hda_codec          96416  2 snd_hda_codec_idt,snd_hda_intel                         
snd_hwdep               9480  1 snd_hda_codec                                           
snd_pcm_oss            44352  0                                                         
snd_mixer_oss          19040  1 snd_pcm_oss                                             
snd_pcm                93672  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss                 
snd_seq_dummy           3588  0                                                         
snd_seq_oss            33760  0                                                         
joydev                 13088  0                                                         
arc4                    2144  2                                                         
snd_seq_midi            8352  0                                                         
snd_rawmidi            27200  1 snd_seq_midi                                            
snd_seq_midi_event      8544  2 snd_seq_oss,snd_seq_midi                                
ecb                     3296  2                                                         
snd_seq                61312  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event                                                                                       
iwl3945                83360  0                                                         
snd_timer              25872  3 snd_pcm,snd_seq                                         
iwlcore               134884  1 iwl3945                                                 
snd_seq_device          8532  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq                                                                                      
mac80211              243368  2 iwl3945,iwlcore                                         
uinput                 10368  0                                                         
uvcvideo               65260  0                                                         
videodev               43360  1 uvcvideo                                                
v4l1_compat            16644  2 uvcvideo,videodev                                       
v4l2_compat_ioctl32    13344  1 videodev                                                
led_class               5256  2 iwl3945,iwlcore                                         
psmouse                57124  0                                                         
snd                    78152  18 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device                                                          
soundcore               9088  1 snd                                                     
lp                     11908  0                                                         
serio_raw               6596  0                                                         
parport                40528  2 ppdev,lp                                                
iptable_filter          3872  1                                                         
snd_page_alloc         11088  2 snd_hda_intel,snd_pcm                                   
ip_tables              21200  1 iptable_filter                                          
cfg80211              152616  3 iwl3945,iwlcore,mac80211
x_tables               25832  7 ipt_REJECT,xt_tcpudp,xt_iprange,xt_state,xt_mark,xt_NFQUEUE,ip_tables
dm_raid45              78504  0
xor                     5456  1 dm_raid45
fbcon                  41344  72
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
i915                  252424  3
drm                   194400  3 i915
i2c_algo_bit            7076  1 i915
usb_storage            66304  0
r8169                  38884  0
mii                     6368  1 r8169
video                  23612  1 i915
output                  3680  1 video
intel_agp              33040  2 i915



Output from cat /proc/asound/version:

Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Mar 30 2010 for kernel 2.6.31-20-generic (SMP).

```

---

### Post by jmate24 on 2010-03-30
i have run into the same problem several times with other software disabling my sound and so I just don't install it. (especially Skype on ubuntu 9.10)

jmate24

---

### Post by VirusCollector on 2010-03-30
Don't install other software? You use a strictly stock install?

---

### Post by VirusCollector on 2010-03-31
Argh I feel stupid. Instead of "sudo killall pulseaudio" I was typing "killall pulseaudio". Now ALSA took over just fine, except...

I really liked having that neat volume control widget. I wonder if there's a replacement.

---

