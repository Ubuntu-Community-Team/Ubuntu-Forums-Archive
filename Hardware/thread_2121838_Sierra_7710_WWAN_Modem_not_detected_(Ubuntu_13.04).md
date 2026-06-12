---
title: "Sierra 7710 WWAN Modem not detected (Ubuntu 13.04)"
date: 2013-03-03
forum: Hardware
---

### Post by Cobuntu on 2013-03-03
Yesterday I got my new Fujitsu T902 and it also has Sierra 7710. I  installed 13.04 alpha and have been searching all threads here related  to 7710. I have no idea of how to get this to work and would be grateful  for any advice or things to try. Here are outputs of commands in this  and related threads:


**uname -mr:**
```
   3.8.0-9-generic x86_64


```

**lsusb:**
```
   Bus 001 Device 006: ID 1199:68a2 Sierra Wireless, Inc.  


```

**usb-devices:**
```
T: Bus=01 Lev=02 Prnt=02 Port=04 Cnt=02 Dev#= 6 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs= 2
P: Vendor=1199 ProdID=68a2 Rev=00.06
S: Manufacturer=Sierra Wireless, Incorporated
S: Product=MC7710
C: #Ifs= 2 Cfg#= 2 Atr=e0 MxPwr=0mA
/usr/bin/usb-devices: line 79: printf: 0c: invalid number
I: If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=0e Prot=00 Driver=cdc_mbim
/usr/bin/usb-devices: line 79: printf: 0d: invalid number
I: If#= 0 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=02 Driver=cdc_mbim
```

**lsmod:**
```
Module Size Used by
sierra_net 13564 0
sierra 18149 0
cdc_mbim 12975 0
cdc_ncm 18448 1 cdc_mbim
cdc_wdm 17999 1 cdc_mbim
usbnet 31879 3 sierra_net,cdc_mbim,cdc_ncm
joydev 17377 0
usbserial 36875 1 sierra
hid_sensor_hub 18484 0
parport_pc 32688 0
ppdev 17073 0
rfcomm 42641 16
bnep 18036 2
tpm_infineon 17410 0
coretemp 13355 0
kvm_intel 132891 0
kvm 443165 1 kvm_intel
ghash_clmulni_intel 13259 0
snd_hda_codec_hdmi 36748 1
aesni_intel 55399 591
aes_x86_64 17255 1 aesni_intel
xts 12885 1 aesni_intel
lrw 13257 1 aesni_intel
gf128mul 14951 2 lrw,xts
ablk_helper 13597 1 aesni_intel
snd_hda_codec_realtek 78399 1
cryptd 20373 3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel 39619 3
nls_iso8859_1 12713 1
snd_hda_codec 136128 3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep 13602 1 snd_hda_codec
snd_pcm 97451 3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
arc4 12615 2
snd_page_alloc 18710 2 snd_pcm,snd_hda_intel
snd_seq_midi 13324 0
snd_seq_midi_event 14899 1 snd_seq_midi
iwldvm 241834 0
mac80211 606411 1 iwldvm
iwlwifi 173312 1 iwldvm
snd_rawmidi 30180 1 snd_seq_midi
cfg80211 510937 3 iwlwifi,mac80211,iwldvm
snd_seq 61554 2 snd_seq_midi_event,snd_seq_midi
snd_seq_device 14497 3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer 29425 2 snd_pcm,snd_seq
uvcvideo 80847 0
videobuf2_vmalloc 13056 1 uvcvideo
videobuf2_memops 13202 1 videobuf2_vmalloc
videobuf2_core 40513 1 uvcvideo
snd 68876 16  snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
fujitsu_tablet 13074 0
videodev 129260 2 uvcvideo,videobuf2_core
microcode 22881 0
btusb 18334 0
rtsx_pci_ms 13011 0
usbhid 47074 1 hid_sensor_hub
bluetooth 228619 22 bnep,btusb,rfcomm
hid 101002 2 hid_sensor_hub,usbhid
memstick 16554 1 rtsx_pci_ms
psmouse 91076 0
serio_raw 13215 0
lpc_ich 17061 0
tpm_tis 18675 0
soundcore 12680 1 snd
mac_hid 13205 0
fujitsu_laptop 18947 0
mei 41158 0
lp 17759 0
parport 46345 3 lp,ppdev,parport_pc
rtsx_pci_sdmmc 17475 0
i915 600342 3
rtsx_pci 28279 2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci 25731 2
e1000e 198787 0
libahci 31364 1 ahci
video 19390 1 i915
i2c_algo_bit 13413 1 i915
drm_kms_helper 49394 1 i915
drm 281283 4 i915,drm_kms_helper
```

**dmesg | tail -20**
```
[ 7.146402] cdc_mbim 1-1.5:2.12 wwan0: register 'cdc_mbim' at usb-0000:00:1a.0-1.5, CDC MBIM, 9e:1f:bb:d7:bd:2b
[ 7.146420] usbcore: registered new interface driver cdc_mbim
[ 10.631464] wlan0: authenticate with bc:05:43:91:70:19
[ 10.636340] wlan0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[ 10.641579] wlan0: send auth to bc:05:43:91:70:19 (try 1/3)
[ 10.643706] wlan0: authenticated
[ 10.644192] wlan0: associate with bc:05:43:91:70:19 (try 1/3)
[ 10.648051] wlan0: RX AssocResp from bc:05:43:91:70:19 (capab=0x431 status=0 aid=2)
[ 10.667021] wlan0: associated
[ 10.667055] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 10.667117] cfg80211: Calling CRDA for country: DE
[ 10.670306] cfg80211: Regulatory domain changed to country: DE
[ 10.670309] cfg80211: (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 10.670310] cfg80211: (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 10.670311] cfg80211: (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 10.670311] cfg80211: (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 10.670312] cfg80211: (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[ 1624.225240] usbcore: registered new interface driver sierra
[ 1624.225250] usbserial: USB Serial support registered for Sierra USB modem
[ 1641.353716] usbcore: registered new interface driver sierra_net
```

**cat /var/log/syslog | tail -20**
```
Mar 3 11:05:17 T902 sudo: pam_ecryptfs: pam_sm_authenticate: /home/captain is already mounted
Mar 3 11:05:17 T902 kernel: [ 1624.225240] usbcore: registered new interface driver sierra
Mar 3 11:05:17 T902 kernel: [ 1624.225250] usbserial: USB Serial support registered for Sierra USB modem
Mar 3 11:05:34 T902 kernel: [ 1641.353716] usbcore: registered new interface driver sierra_net
Mar 3 11:09:38 T902 wpa_supplicant[1500]: wlan0: WPA: Group rekeying completed with bc:05:43:91:70:19 [GTK=TKIP]
Mar 3 11:17:01 T902 CRON[3398]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)
Mar 3 11:19:38 T902 wpa_supplicant[1500]: wlan0: WPA: Group rekeying completed with bc:05:43:91:70:19 [GTK=TKIP]
Mar 3 11:22:31 T902 sudo: pam_ecryptfs: pam_sm_authenticate: /home/captain is already mounted
Mar 3 11:29:38 T902 wpa_supplicant[1500]: wlan0: WPA: Group rekeying completed with bc:05:43:91:70:19 [GTK=TKIP]
Mar 3 11:38:13 T902 sudo: pam_ecryptfs: pam_sm_authenticate: /home/captain is already mounted
Mar 3 11:39:38 T902 wpa_supplicant[1500]: wlan0: WPA: Group rekeying completed with bc:05:43:91:70:19 [GTK=TKIP]
Mar 3 11:43:25 T902 sudo: pam_ecryptfs: pam_sm_authenticate: /home/captain is already mounted
Mar 3 11:49:38 T902 wpa_supplicant[1500]: wlan0: WPA: Group rekeying completed with bc:05:43:91:70:19 [GTK=TKIP]
Mar 3 11:51:48 T902 sudo: pam_ecryptfs: pam_sm_authenticate: /home/captain is already mounted
Mar 3 11:59:38 T902 wpa_supplicant[1500]: wlan0: WPA: Group rekeying completed with bc:05:43:91:70:19 [GTK=TKIP]
Mar 3 12:09:38 T902 wpa_supplicant[1500]: wlan0: WPA: Group rekeying completed with bc:05:43:91:70:19 [GTK=TKIP]
Mar 3 12:15:34 T902 NetworkManager[967]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Mar 3 12:17:01 T902 CRON[4498]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)
Mar 3 12:19:38 T902 wpa_supplicant[1500]: wlan0: WPA: Group rekeying completed with bc:05:43:91:70:19 [GTK=TKIP]
Mar 3 12:29:38 T902 wpa_supplicant[1500]: wlan0: WPA: Group rekeying completed with bc:05:43:91:70:19 [GTK=TKIP]
```

**rfkill list**
```
0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
```

---

### Post by bmork on 2013-03-09
> **Cobuntu said:**
> Yesterday I got my new Fujitsu T902 and it also has Sierra 7710. I  installed 13.04 alpha and have been searching all threads here related  to 7710. I have no idea of how to get this to work and would be grateful  for any advice or things to try. Here are outputs of commands in this  and related threads:


**uname -mr:**
```
   3.8.0-9-generic x86_64


```

**lsusb:**
```
   Bus 001 Device 006: ID 1199:68a2 Sierra Wireless, Inc.  


```

**usb-devices:**
```
T: Bus=01 Lev=02 Prnt=02 Port=04 Cnt=02 Dev#= 6 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs= 2
P: Vendor=1199 ProdID=68a2 Rev=00.06
S: Manufacturer=Sierra Wireless, Incorporated
S: Product=MC7710
C: #Ifs= 2 Cfg#= 2 Atr=e0 MxPwr=0mA
/usr/bin/usb-devices: line 79: printf: 0c: invalid number
I: If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=0e Prot=00 Driver=cdc_mbim
/usr/bin/usb-devices: line 79: printf: 0d: invalid number
I: If#= 0 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=02 Driver=cdc_mbim
```


Yes, there's your problem.  You have pretty new firmware which support both CDC MBIM and the "legacy" QMI/wwan + serial mode.  It does this using 2 configurations (see the  Cfg#= 2).  Linux selects the CDC MBIM configuration by default because standard class functions are preferred over vendor specific functions.

Now, this should ideally have worked and there is a driver as you can see.  But there is no userspace support for the management protocol yet, and this is required to connect.  This is WIP, but still very early in the process.  See [http://sigquit.wordpress.com/2013/02/06/an-introduction-to-libmbim/](http://sigquit.wordpress.com/2013/02/06/an-introduction-to-libmbim/)

So, unless you want to start developing (that would be appreciated, but is of course voluntary), your option for now is to manually override the Linux default and select configuration #1 instead.  It should be supported by a recent ModemManager.  You can change configurations on the command line using
```

 sudo echo 1 >/sys/bus/usb/devices/1-1.5/bConfigurationValue

```

Unfortunately, the MC7710 firmware has a few bugs which may hit you at this point so the above is not always enough.  The absolutely best is to create an udev rule which does this immediately on boot.  That will prevent most problems.  Maybe something like this (completely untested) rule:

```

ACTION!="add|change", GOTO="mbim_to_qmi_rules_end"

SUBSYSTEM!="usb", GOTO="mbim_to_qmi_rules_end"

# ignore any device with only one configuration
ATTR{bNumConfigurations}=="1", GOTO="mbim_to_qmi_rules_end"

# force Sierra Wireless MC7710 to configuration #1
ATTR{idVendor}=="1199",ATTR{idProduct}=="68a2",ATTR{bConfigurationValue}="1"

LABEL="mbim_to_qmi_rules_end"

```

Put it in a file under /etc/udev/rules.d/ and see if it does the job.

Note that this is really just a temporary workaround until the Linux MBIM support is finished.  Using that will be superior, providing a standardized management protocol.  But it will take some time to finish.

---

### Post by Cobuntu on 2013-03-09
Ok, I created an udev rule under /etc/udev/rules.d/ as you suggested:

```

ACTION!="add|change", GOTO="mbim_to_qmi_rules_end"

SUBSYSTEM!="usb", GOTO="mbim_to_qmi_rules_end"

# ignore any device with only one configuration
ATTR{bNumConfigurations}=="1", GOTO="mbim_to_qmi_rules_end"

# force Sierra Wireless MC7710 to configuration #1
ATTR{idVendor}=="1199",ATTR{idProduct}=="68a2",ATTR{bConfigurationValue}="1"

LABEL="mbim_to_qmi_rules_end"

```


After restart Modem Manager offers to create a new broadband connection, after creating that it just works! So far I tested a bit and it is totally stable, after manually discinnecting it reconnects immediately without any problems, also after standby.

**So thank you so much for your quick and brilliant reply! So much appreciated! **

Will the workaround be a problem when the Linux MBIM support is finished and do I have to remove it then? At the moment I have no LTE coverage to test, but will it work when it is available with the workaround? Or is LTE mode not supported, not even with the Linux MBIM support?

---

### Post by bmork on 2013-03-10
> **Cobuntu said:**
> Will the workaround be a problem when the Linux MBIM support is finished and do I have to remove it then? At the moment I have no LTE coverage to test, but will it work when it is available with the workaround? Or is LTE mode not supported, not even with the Linux MBIM support?

Good to hear that it worked.  The workaround will prevent you from testing and using the MBIM support, but this should not be a problem.  This modem works just as well (or even better) in its legacy mode.

LTE works independently of MBIM.  It will work just as well in both modes, and will automatically be used as long as your operator implement handover between the LTE and 3G networks.  No changes required anywhere on your end.  You can look forward to it.  I often see download speed > 80 Mbits/s with the MC7710, on my way to work :)

---

### Post by Cobuntu on 2013-03-10
Thanx for clearing this up! Even better news, still can't believe that this turned out to be so easy with your great help. Thanx again!

---

### Post by Cobuntu on 2013-03-11
Today I went to LTE covered areas and to my astonishment LTE works also and shows correctly in the Network Manager! So everything really works perfectly with this modem!

---

### Post by lere on 2013-04-29
> **Cobuntu said:**
> Ok, I created an udev rule under /etc/udev/rules.d/ as you suggested:

```

ACTION!="add|change", GOTO="mbim_to_qmi_rules_end"

SUBSYSTEM!="usb", GOTO="mbim_to_qmi_rules_end"

# ignore any device with only one configuration
ATTR{bNumConfigurations}=="1", GOTO="mbim_to_qmi_rules_end"

# force Sierra Wireless MC7710 to configuration #1
ATTR{idVendor}=="1199",ATTR{idProduct}=="68a2",ATTR{bConfigurationValue}="1"

LABEL="mbim_to_qmi_rules_end"

```


After restart Modem Manager offers to create a new broadband connection, after creating that it just works! So far I tested a bit and it is totally stable, after manually discinnecting it reconnects immediately without any problems, also after standby.

**So thank you so much for your quick and brilliant reply! So much appreciated! **

Will the workaround be a problem when the Linux MBIM support is finished and do I have to remove it then? At the moment I have no LTE coverage to test, but will it work when it is available with the workaround? Or is LTE mode not supported, not even with the Linux MBIM support?

Hi there,

After Updating to 13.04, i saw the mobile broadband option once in network-manager and i could connect to the network. after rebooting, it didn't show up again.
So i created a file mc7710.rules and pasted the code above. unfortunately, it didn't work for me. Where or how can i debug this issue?

thanks in advance,
Lere

---

### Post by Cobuntu on 2013-04-30
Did you do a fresh installation? I had this working with 13.04 in beta and it still works now, never had any problem with the modem!
Maybe something went wrong, try my (crude) way exactly:
I used "sudo nautilus", went to /etc/udev/rules.d/ and copied an existing file, deleted its contents and put in the code. I renamed the file: 70-sierra-workaround.rules

---

### Post by lere on 2013-05-02
I did the same as you did, but there is no modem available. I use a fujitsu u772, installed 12.04, updated to 12.10 und finally to 13.04.
I some rare occassions, the modem showed up in network manager in the past

---

### Post by Cobuntu on 2013-05-02
Ok, and do you have the exact same modem with the exact same firmware as I have (compare my output)? Anway, I guess the only guy who can help you is bmork, write him a personal message.

---

### Post by bmork on 2013-05-04
> **Cobuntu said:**
> Ok, and do you have the exact same modem with the exact same firmware as I have (compare my output)? Anway, I guess the only guy who can help you is bmork, write him a personal message.

Thanks for the confidence, but I would have to see a lot more logs and command output to have any clue what's going on here.  So far I've only seen "it doesn't work" and that could have a gazillion different causes.  I'll just wait and see if any useful info shows up

---

### Post by Cobuntu on 2013-05-05
Yeah, if it were the exact same output with the same modem with the exact same firmware it would probably be working as a charm/as mine does! But I am definitely confident that you could help him - cause you're the man!

---

### Post by udine1981 on 2013-06-06
Hi,
I have the same problem, I have a Sierra card in my HP Compaq 8510p and it does not appear in my connection manager, but did in 12.10.
You can see my details below.

[B]uname -mr
[/B]
```
3.8.0-23-generic x86_64
```

[B]lsusb -v
[/B]
```
Bus 004 Device 002: ID 03f0:1e1d Hewlett-Packard Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x03f0 Hewlett-Packard
  idProduct          0x1e1d 
  bcdDevice            0.02
  iManufacturer           1 HP
  iProduct                2 HP hs2300 HSDPA Broadband Wireless Module
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           67
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           7
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval             128
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

```

[B]usb-devices
[/B]
```
T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=03f0 ProdID=1e1d Rev=00.02
S:  Manufacturer=HP
S:  Product=HP hs2300 HSDPA Broadband Wireless Module
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 7 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
```

**lsmod**

```
Module                  Size  Used bynls_iso8859_1          12713  0 
usb_storage            57204  0 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320372  3 vboxnetadp,vboxnetflt,vboxpci
rfcomm                 42641  12 
bnep                   18036  2 
binfmt_misc            17500  1 
sierra                 18149  2 
usbserial              36911  6 sierra
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_analog    93738  1 
coretemp               13355  0 
btusb                  22474  0 
lib80211_crypt_tkip    17379  0 
snd_hda_intel          39619  4 
pata_pcmcia            17074  1 
wl                   3074449  0 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_analog
bluetooth             228619  22 bnep,btusb,rfcomm
r8169                  67446  0 
kvm_intel             132891  0 
snd_hwdep              13602  1 snd_hda_codec
tpm_infineon           17410  0 
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
dm_multipath           22843  0 
snd_seq_midi_event     14899  1 snd_seq_midi
lib80211               14352  2 wl,lib80211_crypt_tkip
snd_rawmidi            30180  1 snd_seq_midi
psmouse                95870  0 
kvm                   443165  1 kvm_intel
cfg80211              510937  1 wl
pcmcia                 49007  1 pata_pcmcia
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
joydev                 17377  0 
scsi_dh                14843  1 dm_multipath
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mei                    41158  0 
snd                    68876  18 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog
hp_accel               26012  0 
hp_wmi                 18048  0 
yenta_socket           31817  0 
sparse_keymap          13890  1 hp_wmi
ppdev                  17073  0 
pcmcia_rsrc            18288  1 yenta_socket
lis3lv02d              20111  1 hp_accel
pcmcia_core            22569  3 pcmcia,pcmcia_rsrc,yenta_socket
input_polldev          13896  1 lis3lv02d
lpc_ich                17061  0 
serio_raw              13215  0 
mac_hid                13205  0 
tpm_tis                18675  0 
microcode              22881  0 
soundcore              12680  1 snd
parport_pc             28152  1 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
btrfs                 785967  0 
zlib_deflate           26885  1 btrfs
libcrc32c              12615  1 btrfs
hid_logitech_dj        18604  0 
usbhid                 47074  1 hid_logitech_dj
hid                   101002  2 usbhid,hid_logitech_dj
dm_raid45              76725  0 
xor                    17116  1 dm_raid45
dm_mirror              21946  0 
dm_region_hash         20820  1 dm_mirror
dm_log                 18529  3 dm_region_hash,dm_mirror,dm_raid45
sdhci_pci              18590  0 
firewire_ohci          40103  0 
firewire_core          64508  1 firewire_ohci
sdhci                  32522  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
radeon                937749  3 
ahci                   25731  2 
libahci                31364  1 ahci
i2c_algo_bit           13413  1 radeon
ttm                    83187  1 radeon
e1000e                198787  0 
drm_kms_helper         49394  1 radeon
drm                   286313  5 ttm,drm_kms_helper,radeon
video                  19390  0 
wmi                    19070  1 hp_wmi

```

[B]dmesg | tail -20
[/B]
```
[ 6501.895114] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 6501.895121] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 6501.895127] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 6501.895133] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 6501.895139] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 6620.302311] cfg80211: Calling CRDA to update world regulatory domain
[ 6620.306702] cfg80211: World regulatory domain updated:
[ 6620.306706] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 6620.306709] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6620.306711] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 6620.306713] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 6620.306715] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6620.306717] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6624.933556] cfg80211: Calling CRDA for country: FR
[ 6624.937851] cfg80211: Regulatory domain changed to country: FR
[ 6624.937855] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 6624.937857] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 6624.937860] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 6624.937862] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 6624.937864] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)

```

[B]cat /var/log/syslog | tail -20
[/B]
```
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  Loaded plugin 'Linktop'
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  Loaded plugin 'Huawei'
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  Loaded plugin 'Option High-Speed'
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  Loaded plugin 'Nokia'
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  Loaded plugin 'AnyData'
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  Loaded plugin 'Sierra'
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  Loaded plugin 'ZTE'
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  Loaded plugin 'Option'
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  Loaded plugin 'X22X'
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  Loaded plugin 'Cinterion'
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  Loaded plugin 'Iridium'
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  Loaded plugin 'Generic'
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  Successfully loaded 20 plugins
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  (ttyS4) opening serial port...
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  (ttyUSB0) opening serial port...
Jun  6 16:34:37 localhost modem-manager[7192]: <warn>  (ttyUSB0): port attributes not fully set
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  (ttyUSB1) opening serial port...
Jun  6 16:34:37 localhost modem-manager[7192]: <warn>  (ttyUSB1): port attributes not fully set
Jun  6 16:34:37 localhost modem-manager[7192]: <info>  (ttyUSB2) opening serial port...
Jun  6 16:34:37 localhost modem-manager[7192]: <warn>  (ttyUSB2): port attributes not fully set

```

[B]rfkill list
[/B]
```
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hp-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

Can you help me ?

I had try to do what's worked for Cobuntu with my specific parameters but no effect for me.
I don't understand what's wrong, in 12.10 I didn't do anything special and this card worked good.
Thanks a lot.

I'm sorry, my english is not really perfect.

---

