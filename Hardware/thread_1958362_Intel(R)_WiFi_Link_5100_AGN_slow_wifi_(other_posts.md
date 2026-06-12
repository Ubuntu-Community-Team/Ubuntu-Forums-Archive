---
title: "Intel(R) WiFi Link 5100 AGN slow wifi (other posts did not help)"
date: 2012-04-14
forum: Hardware
---

### Post by ilcontegis on 2012-04-14
Hello!

I did a large reasearch but I could not find a solution to my problem.

I have a vaio tt.
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
Linux gio 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```
lspci -nnk | grep -iA2 net
```
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
	Subsystem: Sony Corporation Device [104d:9047]
	Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
	Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1301]
	Kernel driver in use: iwlwifi

```
lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:18b1 Ricoh Co., Ltd Sony Vaio Integrated Webcam
Bus 001 Device 004: ID 054c:0279 Sony Corp. 
Bus 003 Device 002: ID 147e:1000 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 004 Device 002: ID 054c:02e1 Sony Corp. FeliCa S330 [PaSoRi]

```
iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1F:33:D0:C5:44   
          Bit Rate=135 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:407  Invalid misc:217   Missed beacon:0

eth0      no wireless extensions.

```
rfkill list all
```
1: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: sony-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
4: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
lsmod
```
Module                  Size  Used by
iwlwifi               328352  0 
mac80211              506816  1 iwlwifi
cfg80211              205544  2 iwlwifi,mac80211
parport_pc             32866  0 
rfcomm                 47604  0 
ppdev                  17113  0 
bnep                   18281  2 
tpm_infineon           17536  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
joydev                 17693  0 
arc4                   12529  2 
pcmcia                 49310  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
sony_laptop            45393  0 
snd_timer              29990  2 snd_pcm,snd_seq
tpm_tis                18804  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
r592                   18144  0 
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
memstick               16569  1 r592
i915                  468651  3 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         46978  1 i915
btusb                  18288  0 
drm                   242038  4 i915,drm_kms_helper
psmouse                87603  0 
soundcore              15091  1 snd
mac_hid                13253  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13211  0 
bluetooth             180104  11 rfcomm,bnep,btusb
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
e1000e                156693  0
```

I checked all the old posts about this such as [here]("http://ubuntuforums.org/showthread.php?t=1946898")and [here]("http://askubuntu.com/questions/66810/very-slow-connection-on-an-intelr-wifi-link-5100-agn"), but I cannot solve the problem. With ubuntu 11.10 I had the same issue but as I was using ethernet I did not care that much, now I need to use again my laptop with wifi and I really need to make it work
The common solution is not put this line somewhere in modprobe.d
```
options iwlagn 11n_disable=0
```
Is not working, I never had the intel-5300-iwlagn-disable11n.conf file even in Ubuntu 11.10.

Please I would really appreciate if you could give me a hand.

Thank you very much!):P

---

### Post by bkratz on 2012-04-14
Certainly not an expert, but the reason iwlagn 11n_disable=0 does nothing is because you are not using iwlagn.  You are using the new driver iwlwifi.
[COLOR=Red]Kernel driver in use: iwlwifi[/COLOR]
 Perhaps there is an option for that one. More info about the difference

[http://ubuntuforums.org/showthread.php?t=1886179](http://ubuntuforums.org/showthread.php?t=1886179)

---

### Post by ilcontegis on 2012-04-14
Thank you very much for your support! Now I know why that method is not working..
Still I need some help to find how to make the wifi working properly as on the net I cannot find an answer.
Can someone give me a little help? :p Thanks

---

### Post by ahallubuntu on 2012-04-14
I'm using this same Intel card in my Dell laptop - but I'm using Ubuntu 10.04 LTS (32 bit) which is supported for another year yet, until April 2013.  The card works quite well for me - certainly not slow at all.

10.04 works pretty well; it has a few issues, but it's quite usable.  So 10.04 is an option for you.  I like Gnome desktop so will probably want to stick with this install somewhat longer vs. moving to 12.04 LTS right away.  I might try it out first with Gnome 3 and see how it works out.

I had another laptop with this same 5100 card and 11.10 installed, and it did not seem slow there, though I did not use that laptop extensively or for very long the way I use the 10.04 laptop every day.

You could try 10.04 at least and see if you have the same issues.  If you do, maybe there is something wrong with your card.  Fortunately, it should be easy to replace the card with something else in a Sony; HP and Lenovo laptops are very strict in not allowing you to upgrade the wireless cards, but Sony, Dell, Acer, and Toshiba seem to allow it without issue if you plug in a compatible wireless card.

There's always an outside chance one of the antenna wires has come loose from the card.  Might be worth checking.

---

### Post by ilcontegis on 2012-04-14
The bug is the [following]("http://www.fedora-it.org/forum/segnala-un-bug/bug-785239-modulo-iwlwifi-non-funzionante-schede-wireless-intel-wifi")  the solution is similar but it needs to use iwlwifi.conf and the value must be set to 1.
From terminal
```
 sudo gedit /etc/modprobe.d/iwlwifi.conf
```

Then add this line 
```
options iwlwifi 11n_disable=1
```

Finally from terminal restart iwlwifi
```

sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```

Thank you for your support!

---

### Post by ahallubuntu on 2012-04-14
FYI, I use my 5100 card at full N speeds.  I do not need to slow it down with the "iwlagn 11n_disable=0" setting to get reliable, high speed connections (I still use iwlagn as I'm using Ubuntu 10.04).  I would not use a wireless card that only ran at G speeds; I would replace it first.

---

### Post by ilcontegis on 2012-04-16
> **ahallubuntu said:**
> FYI, I use my 5100 card at full N speeds.  I do not need to slow it down with the "iwlagn 11n_disable=0" setting to get reliable, high speed connections (I still use iwlagn as I'm using Ubuntu 10.04).  I would not use a wireless card that only ran at G speeds; I would replace it first.
The bug comes out from Ubuntu 11.10 (and therefore also ubuntu 12.04).
Of course if you are using ubuntu 10.04 you do not have this issue.
Nevertheless I don't like to use old versions of ubuntu, I prefer to enjoy new software releases although if sometimes some issues arises. With the modification I did I can succeed to d everything I need with that small laptop, which is: browse internet, stream HD videos (e.g. youtube), check e-mails, use gtalk for video chat.
Maybe you need a faster connection, but I prefer to have new software because I like to try out new things and have a wifi card which goes slightly slower. To tell the truth I do not feel any issue, I can stream HD content without any interruption.):P

---

