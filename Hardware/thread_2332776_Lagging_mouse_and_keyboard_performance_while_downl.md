---
title: "Lagging mouse and keyboard performance while downloading anything"
date: 2016-08-03
forum: Hardware
---

### Post by chaosonion on 2016-08-03
Hello,

I'm running a Lenovo G410. I've recently upgraded to Ubuntu  16.04 from Ubuntu 14.04. Whenever i try downloading something ,  be it through a web browser, torrent, or apt-get my wireless, 2.6Ghz, logitech  mouse and keyboard start to lag. This problem persists until the  download is finished. I've checked top and there doesn't really seem to  be anything awry but I must admit I'm not exactly sure what it is I  should be looking for *exactly*. I normally use wifi and have checked if this could be the problem but the problem persists even when using an ethernet connection. At this point I'm at a loss  since I can't find any other articles/posts which pertain to this  specific problem. I hope someone will be able to help me troubleshoot  this and fix the issue. BTW, This problem also manifests itself on Debian 8.5.0.

Thanks!

PS
I'm including the output of lsmod and xinput just in case:

lsmod:
```
Module                  Size  Used by
ctr                    12927  1 
ccm                    17577  1 
binfmt_misc            16949  1 
pci_stub               12429  1 
vboxpci                23077  0 
vboxnetadp             25443  0 
vboxnetflt             27598  0 
vboxdrv               344446  3 vboxnetadp,vboxnetflt,vboxpci
nfsd                  267128  2 
auth_rpcgss            51211  1 nfsd
oid_registry           12419  1 auth_rpcgss
nfs_acl                12511  1 nfsd
nfs                   188136  0 
lockd                  83389  2 nfs,nfsd
fscache                45542  1 nfs
sunrpc                237402  6 nfs,nfsd,auth_rpcgss,lockd,nfs_acl
nls_utf8               12456  1 
nls_cp437              16553  1 
vfat                   17135  1 
fat                    61986  1 vfat
rtsx_usb_ms            16899  0 
memstick               13696  1 rtsx_usb_ms
x86_pkg_temp_thermal    12951  0 
intel_powerclamp       17159  0 
intel_rapl             17356  0 
coretemp               12820  0 
kvm_intel             139116  0 
kvm                   388784  1 kvm_intel
snd_hda_codec_hdmi     45118  1 
crc32_pclmul           12915  0 
iTCO_wdt               12831  0 
iTCO_vendor_support    12649  1 iTCO_wdt
arc4                   12536  2 
ath9k                  90245  0 
aesni_intel           151423  2 
ath9k_common           21746  1 ath9k
ath9k_hw              391172  2 ath9k_common,ath9k
aes_x86_64             16719  1 aesni_intel
lrw                    12757  1 aesni_intel
i915                  837235  5 
gf128mul               12970  1 lrw
ath                    26067  3 ath9k_common,ath9k,ath9k_hw
mac80211              474216  1 ath9k
cfg80211              405538  4 ath,ath9k_common,ath9k,mac80211
ideapad_laptop         17447  0 
glue_helper            12695  1 aesni_intel
ablk_helper            12572  1 aesni_intel
sparse_keymap          12818  1 ideapad_laptop
evdev                  17445  26 
joydev                 17063  0 
cryptd                 14516  2 aesni_intel,ablk_helper
drm_kms_helper         49210  1 i915
drm                   249998  4 i915,drm_kms_helper
snd_hda_codec_conexant    17841  1 
serio_raw              12849  0 
pcspkr                 12595  0 
rfkill                 18867  3 cfg80211,ideapad_laptop
efi_pstore             12805  1 
snd_hda_codec_generic    63181  1 snd_hda_codec_conexant
snd_hda_intel          26407  5 
efivars                17257  1 efi_pstore
ac                     12715  0 
video                  18096  1 i915
snd_hda_controller     26646  1 snd_hda_intel
snd_hda_codec         104500  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              13148  1 snd_hda_codec
snd_pcm                88662  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_timer              26614  1 snd_pcm
battery                13356  0 
ie31200_edac           12511  0 
shpchp                 31121  0 
snd                     65244  18  snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
soundcore              13026  2 snd,snd_hda_codec
i2c_algo_bit           12751  1 i915
mei_me                 17941  0 
mei                    74977  1 mei_me
i2c_i801               16965  0 
i2c_core               46012  5 drm,i915,i2c_i801,drm_kms_helper,i2c_algo_bit
edac_core              47321  1 ie31200_edac
lpc_ich                20768  0 
processor              28221  0 
button                 12944  1 i915
fuse                   83350  5 
parport_pc             26300  0 
ppdev                  16782  0 
lp                     17074  0 
parport                35749  3 lp,ppdev,parport_pc
autofs4                35529  2 
ext4                  473801  1 
crc16                  12343  1 ext4
mbcache                17171  1 ext4
jbd2                   82514  1 ext4
rtsx_usb_sdmmc         25280  0 
mmc_core              102374  1 rtsx_usb_sdmmc
rtsx_usb               17541  2 rtsx_usb_sdmmc,rtsx_usb_ms
mfd_core               12601  2 lpc_ich,rtsx_usb
usb_storage            56215  1 
sg                     29973  0 
sd_mod                 44356  6 
sr_mod                 21903  0 
crc_t10dif             12431  1 sd_mod
cdrom                  47424  1 sr_mod
crct10dif_generic      12581  0 
hid_generic            12393  0 
usbhid                 44460  0 
hid                   102264  2 hid_generic,usbhid
ahci                   33334  3 
libahci                27158  1 ahci
crct10dif_pclmul       13387  1 
crct10dif_common       12356  3 crct10dif_pclmul,crct10dif_generic,crc_t10dif
crc32c_intel           21809  0 
ehci_pci               12512  0 
libata                177508  2 ahci,libahci
ehci_hcd               69837  1 ehci_pci
xhci_hcd              152977  0 
scsi_mod              191405  5 sg,usb_storage,libata,sd_mod,sr_mod
psmouse                99249  0 
alx                    36175  0 
mdio                   12599  1 alx
usbcore               195468  6 rtsx_usb,usb_storage,ehci_hcd,ehci_pci,usbhid,xhci_hcd
thermal                17559  0 
usb_common             12440  1 usbcore
thermal_sys            27642  5 video,intel_powerclamp,thermal,processor,x86_pkg_temp_thermal


```

xinput:
```
&#9121; Virtual core pointer                       id=2   [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                 id=4   [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                      id=10   [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                 id=13   [slave  pointer  (2)]
&#9123; Virtual core keyboard                      id=3   [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                id=5   [slave  keyboard (3)]
    &#8627; Power Button                               id=6   [slave  keyboard (3)]
    &#8627; Video Bus                                  id=7   [slave  keyboard (3)]
    &#8627; Power Button                               id=8   [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                      id=9   [slave  keyboard (3)]
    &#8627; Ideapad extra buttons                      id=11   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard               id=12   [slave  keyboard (3)]

```

---

### Post by chaosonion on 2016-08-04
Unfortunately this problem also shows itself in 14.04. I did not notice it before but i guess it must have been there in the past. So, to sum up, this problem manifests in 16.04, debian 8.5, and 14.04.4. i'm including output from inxi : 

```
black@lemmy:~$ inxi -Fxz
System:    Host: lemmy Kernel: 4.2.0-42-generic x86_64 (64 bit, gcc: 4.8.4) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: LENOVO product: 20237 version: Lenovo G410
           Mobo: LENOVO model: INVALID version: 31900058Std Bios: LENOVO version: 79CN50WW(V3.09) date: 10/20/2014
CPU:       Dual core Intel Core i5-4200M CPU (-HT-MCP-) cache: 3072 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9978.08 
           Clock Speeds: 1: 2518.359 MHz 2: 1204.199 MHz 3: 1642.675 MHz 4: 1262.695 MHz
Graphics:  Card: Intel 4th Gen Core Processor Integrated Graphics Controller bus-ID: 00:02.0 
           X.Org: 1.17.2 drivers: intel (unloaded: fbdev,vesa) Resolution: 1600x900@60.0hz 
           GLX Renderer: Mesa DRI Intel Haswell Mobile GLX Version: 3.0 Mesa 11.0.2 Direct Rendering: Yes
Audio:     Card-1: Intel 8 Series/C220 Series High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 
           Card-2: Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller driver: snd_hda_intel bus-ID: 00:03.0 
           Sound: Advanced Linux Sound Architecture ver: k4.2.0-42-generic
Network:   Card-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter driver: ath9k bus-ID: 02:00.0
           IF: wlan0 state: up mac: <filter>
           Card-2: Qualcomm Atheros QCA8172 Fast Ethernet driver: alx port: 3000 bus-ID: 03:00.0
           IF: eth0 state: down mac: <filter>
Drives:    HDD Total Size: 1124.4GB (11.0% used) 1: id: /dev/sda model: ST1000LM024_HN size: 1000.2GB temp: 41C 
           2: USB id: /dev/sdb model: Ultra size: 124.2GB temp: 0C 
Partition: ID: / size: 524G used: 8.1G (2%) fs: ext4 ID: swap-1 size: 8.50GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 48.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 214 Uptime: 1 day Memory: 1914.7/7896.3MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 
```

---

