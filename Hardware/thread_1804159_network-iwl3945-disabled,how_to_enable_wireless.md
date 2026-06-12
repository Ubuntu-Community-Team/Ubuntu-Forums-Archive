---
title: "network-iwl3945-disabled,how to enable wireless"
date: 2011-07-14
forum: Hardware
---

### Post by zh3236387 on 2011-07-14
root@andononi-PC:/home/andononi# lshw -c network
 *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:c4:e4:9e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.38-8-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:48 memory:f0900000-f0900fff
  *-network
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 14
       serial: 00:1e:68:03:18:50
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.2.41 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f0800000-f0803fff ioport:2000(size=256)



root@andononi-PC:/home/andononi# ifconfig
eth0      Link encap:&#20197;&#22826;&#32593;  &#30828;&#20214;&#22320;&#22336; 00:1e:68:03:18:50  
          inet &#22320;&#22336;:192.168.2.41  &#24191;&#25773;:192.168.2.255  &#25513;&#30721;:255.255.255.0
          inet6 &#22320;&#22336;: fe80::21e:68ff:fe03:1850/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  &#36291;&#28857;&#25968;:1
          &#25509;&#25910;&#25968;&#25454;&#21253;:120674 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#24103;&#25968;:0
          &#21457;&#36865;&#25968;&#25454;&#21253;:63456 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#36733;&#27874;:0
          &#30896;&#25758;:0 &#21457;&#36865;&#38431;&#21015;&#38271;&#24230;:1000 
          &#25509;&#25910;&#23383;&#33410;:166877960 (166.8 MB)  &#21457;&#36865;&#23383;&#33410;:4957622 (4.9 MB)
          &#20013;&#26029;:17 

lo        Link encap:&#26412;&#22320;&#29615;&#22238;  
          inet &#22320;&#22336;:127.0.0.1  &#25513;&#30721;:255.0.0.0
          inet6 &#22320;&#22336;: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  &#36291;&#28857;&#25968;:1
          &#25509;&#25910;&#25968;&#25454;&#21253;:16 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#24103;&#25968;:0
          &#21457;&#36865;&#25968;&#25454;&#21253;:16 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#36733;&#27874;:0
          &#30896;&#25758;:0 &#21457;&#36865;&#38431;&#21015;&#38271;&#24230;:0 
          &#25509;&#25910;&#23383;&#33410;:960 (960.0 B)  &#21457;&#36865;&#23383;&#33410;:960 (960.0 B)



root@andononi-PC:/home/andononi# ifconfig -a
eth0      Link encap:&#20197;&#22826;&#32593;  &#30828;&#20214;&#22320;&#22336; 00:1e:68:03:18:50  
          inet &#22320;&#22336;:192.168.2.41  &#24191;&#25773;:192.168.2.255  &#25513;&#30721;:255.255.255.0
          inet6 &#22320;&#22336;: fe80::21e:68ff:fe03:1850/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  &#36291;&#28857;&#25968;:1
          &#25509;&#25910;&#25968;&#25454;&#21253;:121333 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#24103;&#25968;:0
          &#21457;&#36865;&#25968;&#25454;&#21253;:63491 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#36733;&#27874;:0
          &#30896;&#25758;:0 &#21457;&#36865;&#38431;&#21015;&#38271;&#24230;:1000 
          &#25509;&#25910;&#23383;&#33410;:166930135 (166.9 MB)  &#21457;&#36865;&#23383;&#33410;:4967271 (4.9 MB)
          &#20013;&#26029;:17 

lo        Link encap:&#26412;&#22320;&#29615;&#22238;  
          inet &#22320;&#22336;:127.0.0.1  &#25513;&#30721;:255.0.0.0
          inet6 &#22320;&#22336;: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  &#36291;&#28857;&#25968;:1
          &#25509;&#25910;&#25968;&#25454;&#21253;:16 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#24103;&#25968;:0
          &#21457;&#36865;&#25968;&#25454;&#21253;:16 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#36733;&#27874;:0
          &#30896;&#25758;:0 &#21457;&#36865;&#38431;&#21015;&#38271;&#24230;:0 
          &#25509;&#25910;&#23383;&#33410;:960 (960.0 B)  &#21457;&#36865;&#23383;&#33410;:960 (960.0 B)

wlan0     Link encap:&#20197;&#22826;&#32593;  &#30828;&#20214;&#22320;&#22336; 00:1c:bf:c4:e4:9e  
          BROADCAST MULTICAST  MTU:1500  &#36291;&#28857;&#25968;:1
          &#25509;&#25910;&#25968;&#25454;&#21253;:0 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#24103;&#25968;:0
          &#21457;&#36865;&#25968;&#25454;&#21253;:0 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#36733;&#27874;:0
          &#30896;&#25758;:0 &#21457;&#36865;&#38431;&#21015;&#38271;&#24230;:1000 
          &#25509;&#25910;&#23383;&#33410;:0 (0.0 B)  &#21457;&#36865;&#23383;&#33410;:0 (0.0 B)






root@andononi-PC:/home/andononi# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off




root@andononi-PC:/home/andononi# lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
binfmt_misc            13213  1 
joydev                 17322  0 
snd_hda_codec_realtek   255820  1 
pcmcia                 39671  0 
arc4                   12473  2 
snd_hda_intel          24140  2 
iwl3945               130113  0 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
iwlcore               148965  1 iwl3945
snd_seq_midi           13132  0 
mac80211              257001  2 iwl3945,iwlcore
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               66851  0 
cfg80211              156212  3 iwl3945,iwlcore,mac80211
videodev               75143  1 uvcvideo
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
snd_timer              28659  2 snd_pcm,snd_seq
psmouse                73312  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_7xx1              12898  0 
tifm_core              15040  1 tifm_7xx1
serio_raw              12990  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  450944  3 
usbhid                 41704  0 
sdhci_pci              13623  0 
firewire_ohci          31504  0 
hid                    77084  1 usbhid
firewire_core          56138  1 firewire_ohci
drm_kms_helper         40745  1 i915
sky2                   49172  0 
drm                   180037  4 i915,drm_kms_helper
crc_itu_t              12627  1 firewire_core
ahci                   21591  3 
sdhci                  22720  1 sdhci_pci
libahci                25548  1 ahci
i2c_algo_bit           13184  1 i915
video                  18951  1 i915



how to enable wireless?

---

### Post by zh3236387 on 2011-07-14
root@andononi-PC:/home/andononi# ifconfig wlan0 up
SIOCSIFFLAGS: &#27809;&#26377;&#37027;&#20010;&#35774;&#22791;

---

