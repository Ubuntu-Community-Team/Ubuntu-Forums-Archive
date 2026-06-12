---
title: "Dell 1018 WIFI"
date: 2010-12-24
forum: Hardware
---

### Post by tomreid on 2010-12-24
Hi

I have the above netbook. 

On first install of Ubuntu 1004 LTS Netbook edition, it's wifi did not work at all. It has a **Realtek RTL8188CE** wifi card.

I applied the fix indicated in this thread: [http://guide.ubuntuforums.org/showthread.php?p=10267140#post10267140](http://guide.ubuntuforums.org/showthread.php?p=10267140#post10267140) which involved loading a PPA

When I have been using the wifi for around 10 mins, when I surf to  another URl, the browser gets stuck at "looking up....." and I have to  re-boot the system to start the internet working again.

I have an older Dell mini 10V (it's about 16 months old running off the  same wifi in the same house and it never does this). I also had exactly  this same issue on a HP Desktop, it seemed to be some kind of DNS look  up issue, but I never got to the bottom of it.

Any help gratefuly received.

cheers

---

### Post by tragantaba on 2012-01-12
I'm having the same issue, I had tried everything! Any help would be greatly appreciated. 

Here i have some infor that might help:

karlos@karlos-Inspiron-1018:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux karlos-Inspiron-1018 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
karlos@karlos-Inspiron-1018:~$ lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  05)
    Subsystem: Dell Device [1028:048e]
    Kernel driver in use: r8169
--
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Dell Device [1028:8194]
    Kernel driver in use: rtl8192ce
karlos@karlos-Inspiron-1018:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:eek:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:eek:ff
          Power Management:eek:n
          
karlos@karlos-Inspiron-1018:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
karlos@karlos-Inspiron-1018:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
arc4                   12473  2 
snd_hda_codec_realtek   254125  1 
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
rtl8192ce             127398  0 
uvcvideo               67271  0 
rtlwifi               102641  1 rtl8192ce
videodev               85626  1 uvcvideo
mac80211              393459  2 rtl8192ce,rtlwifi
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  505159  3 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
cfg80211              172392  2 rtlwifi,mac80211
serio_raw              12990  0 
snd                    55902  13  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,   snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,sn  d_seq_device
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
binfmt_misc            17292  1 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
r8169                  43104  0 
karlos@karlos-Inspiron-1018:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        5C:26:0A:4E:8B:grin:3

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.132.20.37
    Prefix:          24 (255.255.255.0)
    Gateway:         10.132.20.1

    DNS:             10.151.18.2
    DNS:             10.151.18.3
    DNS:             10.130.11.3
    DNS:             10.130.11.4
    DNS:             10.129.40.7


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             unavailable
  Default:           no
  HW Address:        88:25:2C:grin:4:BC:grin:4

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


karlos@karlos-Inspiron-1018:~$ sudo iwlist scan
[sudo] password for karlos: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

---

