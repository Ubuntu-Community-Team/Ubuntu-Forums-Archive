---
title: "Bluetooth audio debugging"
date: 2014-07-28
forum: Hardware
---

### Post by dargaud2 on 2014-07-28
Hello all,
I have a new set of bluetooth speakers. They work fine on my Android phones and my HP SPectreXT Ubuntu laptop. But my Dell Precision M6700 has problems with them. It starts by playing normally but then after a few minutes the sound gets all hacked up, then silent, then it disconnects, reconnects and starts playing again. Very annoying.

There used ot be a 2s lag that is now solved thanks to the VLC backend (aptitude install phonon-backend-vlc), but the periodical disconnect remains.
I've been trying to diagnose whether it's a config problem (normally this should be the same config as my HP) or a hardware problem, but I need some help with that.

I've been running hcidump -X and when the sound goes away, there's no more 'completed packets' messages and all the data packets are identical after the 1st few bytes:
> < ACL data: handle 11 flags 0x02 dlen 864
    L2CAP(d): cid 0x0204 len 860 [psm 0]
      0000: 80 01 b9 41 02 da bb 1a  00 00 00 01 0b 9c bd 20  ...A........... 
      0010: 38 00 00 00 00 00 00 00  00 00 55 55 15 55 55 55  8.........UU.UUU
      0020: 15 55 55 55 55 55 55 55  55 55 55 55 55 55 55 55  .UUUUUUUUUUUUUUU
      0030: 55 55 55 55 55 55 55 55  55 55 55 55 55 55 55 55  UUUUUUUUUUUUUUUU
      0040: 55 55 55 55 55 55 55 55  55 55 55 55 55 55 55 55  UUUUUUUUUUUUUUUU
      0050: 55 55 55 55 55 55 55 55  55 55 9c bd 20 38 00 00  UUUUUUUUUU.. 8..
      0060: 00 00 00 00 00 00 00 55  55 55 55 55 55 55 55 55  .......UUUUUUUUU
      0070: 55 55 55 55 55 55 55 55  55 55 55 55 55 55 55 55  UUUUUUUUUUUUUUUU
      0080: 55 55 55 55 55 55 55 55  55 55 55 55 55 55 55 55  UUUUUUUUUUUUUUUU
      0090: 55 55 55 55 55 55 55 55  55 55 55 55 55 55 55 55  UUUUUUUUUUUUUUUU
      00a0: 55 55 55 55 55 55 55 9c  bd 20 38 00 00 00 00 00  UUUUUUU.. 8.....
 

I also tried wireshark and I sawa a few messages like:
71099    780.376517000    localhost ()    remote ()    L2CAP    30    Sent Configure Response - Failure - unacceptable parameters (SCID: 0x09c2)

What can I try ?

---

### Post by tgalati4 on 2014-07-28
Turn off wireless and see how long the bluetooth connection lasts.  Typically wifi will interfere with bluetooth.  Sometimes there is an interference mode that you can activate in your wireless.  What module are you running for your wireless?

```
lsmod
lscpi | grep Network
```

---

### Post by dargaud2 on 2014-07-30
Thanks for your reply.
You are most likely right. I disabled the wifi in the BIOS and I just ran the BT sound for one hour without a hitch. I wonder if this is related to a slow wifi issue I'm having [here]("http://ubuntuforums.org/showthread.php?t=2237075&p=13086805").

```
$ lspci | grep Network  
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)

$ lsmod
Module                  Size  Used by
nfsv3                  39326  1 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
cuse                   13445  3 
rpcsec_gss_krb5        35573  1 
nfsv4                 461547  1 
rfcomm                 69160  10 
bnep                   19624  2 
uvcvideo               80885  0 
snd_hda_codec_hdmi     46254  1 
videobuf2_vmalloc      13216  1 uvcvideo
btusb                  32412  0 
dell_wmi               12761  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
sparse_keymap          13948  1 dell_wmi
bluetooth             391196  22 bnep,btusb,rfcomm
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
dell_laptop            18168  0 
snd_hda_codec_idt      54645  1 
arc4                   12608  2 
nfsd                  280330  2                                                                                                                  
intel_rapl             18773  0                                                                                                                  
x86_pkg_temp_thermal    14205  0                                                                                                                 
intel_powerclamp       14705  0                                                                                                                  
coretemp               13435  0                                                                                                                  
kvm_intel             143060  0                                                                                                                  
iwldvm                232285  0                                                                                                                  
kvm                   451511  1 kvm_intel                                                                                                        
mac80211              630653  1 iwldvm                                                                                                           
dcdbas                 14928  1 dell_laptop                                                                                                      
crct10dif_pclmul       14289  0                                                                                                                  
crc32_pclmul           13113  0                                                                                                                  
auth_rpcgss            59338  3 nfsd,rpcsec_gss_krb5                                                                                             
ghash_clmulni_intel    13216  0                                                                                                                  
aesni_intel            55624  0                                                                                                                  
snd_hda_intel          52355  5                                                                                                                  
nfs_acl                12837  2 nfsd,nfsv3                                                                                                       
aes_x86_64             17131  1 aesni_intel                                                                                                      
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel                                                               
snd_hwdep              13602  1 snd_hda_codec
lrw                    13286  1 aesni_intel
nfs                   236636  7 nfsv3,nfsv4
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
gf128mul               14951  1 lrw
lockd                  93977  3 nfs,nfsd,nfsv3
glue_helper            13990  1 aesni_intel
sunrpc                284590  40 nfs,nfsd,rpcsec_gss_krb5,auth_rpcgss,lockd,nfsv3,nfsv4,nfs_acl
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
binfmt_misc            17468  1 
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17381  0 
fscache                63988  2 nfs,nfsv4
snd_seq_midi           13324  0 
serio_raw              13462  0 
iwlwifi               169932  1 iwldvm
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
lpc_ich                21080  0 
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                 18627  0 
mei                    82276  1 mei_me
soundcore              12680  1 snd
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
radeon               1522422  3 
i2c_algo_bit           13413  1 radeon
ttm                    85115  1 radeon
firewire_ohci          40409  0 
drm_kms_helper         53081  1 radeon
ahci                   25819  2 
e1000e                254433  0 
libahci                32560  1 ahci
drm                   303102  5 ttm,drm_kms_helper,radeon
psmouse               106678  0 
firewire_core          68769  1 firewire_ohci
sdhci_pci              23172  0 
ptp                    18933  1 e1000e
sdhci                  43015  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
pps_core               19382  1 ptp
wmi                    19177  1 dell_wmi
video                  19476  0 

```

---

### Post by dargaud2 on 2014-08-03
I guess this ties in whith my slow wifi problems. If I disable the [bluetooth in the BIOS]("http://ubuntuforums.org/showthread.php?t=2237075&p=13087668"), the wifi speeds up (even if I don't use it).

---

