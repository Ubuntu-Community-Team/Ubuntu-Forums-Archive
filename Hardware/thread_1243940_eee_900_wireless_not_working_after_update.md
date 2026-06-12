---
title: "eee 900 wireless not working after update"
date: 2009-08-18
forum: Hardware
---

### Post by mardukvmbc on 2009-08-18
I did a very foolish thing by activating the "Alternate Atheros madwifi driver" and updating to 2.6.28-15-generic kernel on my wife's eee 900.
Now the wireless isn't working... 

Deactivating the driver doesn't help. Also tried the backports fix and that didn't help.

When I use the network management applet to add a wireless connection, the wireless tab is greyed out.

The madwifi driver won't activate anymore, either. Update: got it to activate using jockey-gtk instead of jockey-kde.

I'm running kubuntu jaunty.

Any ideas anyone? My wife is going to kill me :(

---

### Post by mardukvmbc on 2009-08-19
interestingly,[INDENT]iwconfig                          
lo        no wireless extensions.                       

eth0      no wireless extensions.

pan0      no wireless extensions.

[/INDENT]and[INDENT]lsmod
Module                  Size  Used by
nfs                   266600  0      
i915                   67844  2      
drm                    96424  3 i915 
ppdev                  15620  0      
bridge                 56212  0      
stp                    10500  1 bridge
bnep                   20224  2       
nfsd                  228012  13      
lockd                  74284  2 nfs,nfsd
nfs_acl                11136  2 nfs,nfsd
auth_rpcgss            42144  1 nfsd    
sunrpc                195552  14 nfs,nfsd,lockd,nfs_acl,auth_rpcgss                                             
exportfs               12416  1 nfsd                    
input_polldev          11912  0                         
lp                     17156  0                         
parport                42220  2 ppdev,lp                
pcspkr                 10496  0                         
psmouse                61972  0                         
serio_raw              13444  0                         
iTCO_wdt               19108  0                         
iTCO_vendor_support    11652  1 iTCO_wdt                
uvcvideo               63368  0                         
compat_ioctl32          9344  1 uvcvideo                
videodev               41600  1 uvcvideo                
v4l1_compat            21764  2 uvcvideo,videodev       
joydev                 18496  0                         
snd_hda_intel         434100  3                         
snd_pcm_oss            46336  0                         
snd_mixer_oss          22656  1 snd_pcm_oss             
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss                                                       
snd_seq_dummy          10756  0                         
snd_seq_oss            37760  0                         
ath_pci                99224  0                         
snd_seq_midi           14336  0                         
wlan                  210544  1 ath_pci                 
ath_hal               198864  1 ath_pci                 
snd_rawmidi            29696  1 snd_seq_midi            
atl2                   34328  0                         
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event                       
snd_timer              29704  2 snd_pcm,snd_seq         
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
intel_agp              34108  1
agpgart                42696  3 drm,intel_agp
video                  25360  0
output                 11008  1 video
eeepc_laptop           18452  0
usbhid                 42336  0
usb_storage            99648  0
fbcon                  46112  0
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

[/INDENT]shouldn't the wireless card be listed here?

the following yeilds:
lspci                       
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)                                                       
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)      
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)                                                   
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)           
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)           
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)           
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)              
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)              
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)

---

### Post by mardukvmbc on 2009-08-19
Victory!
a sudo modprobe ath5k did the trick, although I don't know why.
I've put it in my init.d and all seems well.

---

### Post by ROY.G.BIV on 2009-08-19
> **mardukvmbc said:**
> Victory!
a sudo modprobe ath5k did the trick, although I don't know why.
I've put it in my init.d and all seems well.

Hey,

Its because ath5k is what Ubuntu identifies your card as... I found the file once, but I can't find it now...

Question for you: I'm running a wireless cared where I have to type in "sudo modprobe option" for it to pick it up. Does adding it to init.d make it pick it automatically? If so, what do I have to od to do that?

---

