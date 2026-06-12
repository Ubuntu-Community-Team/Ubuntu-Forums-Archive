---
title: "Cable unplugged even if plugged Realtek RTL-8110SC/8169SC"
date: 2013-10-21
forum: Hardware
---

### Post by Con7e on 2013-10-21
Hello to all.

I have just installed the system and I have one, major, problem: it says that my network cable is unplugged, even if it's plugged.

I have a Realtek RTL-8110SC/8169SC Gigabit Ethernet and with Windows it works with no problem.

If I do ***ifconfig*** in the terminal, I get:

```

enp7s1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 14:da:e9:21:fd:bf  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 384  bytes 30176 (29.4 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 384  bytes 30176 (29.4 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



```

The "enp7s1" should be my card (I recognise the MAC), but usually isn't it "eth***X***" ?

Also, here is the output for ***lsmod*** command:

```

Module                  Size  Used by
rfcomm                 51153  4 
fuse                   74541  3 
raid1                  27772  1 
bnep                   11037  2 
usblp                  12722  0 
bluetooth             308366  10 bnep,rfcomm
rfkill                 15666  3 bluetooth
iTCO_wdt                5407  0 
iTCO_vendor_support     1929  1 iTCO_wdt
mxm_wmi                 1467  0 
evdev                   9880  5 
joydev                  9663  0 
hid_generic             1153  0 
md_mod                105782  1 raid1
coretemp                6038  0 
kvm_intel             128977  0 
kvm                   376330  1 kvm_intel
snd_hda_codec_hdmi     29733  1 
microcode              13172  0 
psmouse                85132  0 
serio_raw               5041  0 
snd_hda_codec_realtek    35645  1 
**r8169                  57640  0 **
lpc_ich                12849  0 
mii                     4027  1 r8169
i2c_i801               11237  0 
snd_hda_intel          35309  5 
snd_hda_codec         147506  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep               6332  1 snd_hda_codec
snd_pcm                77765  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc          7202  2 snd_pcm,snd_hda_intel
snd_timer              18718  1 snd_pcm
snd                    58950  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_hda_codec,snd_hda_intel
acpi_cpufreq           10502  0 
soundcore               5418  1 snd
mperf                   1203  1 acpi_cpufreq
i7core_edac            17669  0 
edac_core              44137  2 i7core_edac
asus_atk0110           12000  0 
wmi                     8283  1 mxm_wmi
processor              27755  1 acpi_cpufreq
button                  4669  0 
nfs                   145074  0 
lockd                  76805  1 nfs
sunrpc                221055  2 nfs,lockd
fscache                44575  1 nfs
ext4                  456475  1 
crc16                   1359  2 ext4,bluetooth
mbcache                 5866  1 ext4
jbd2                   81946  1 ext4
hid_logitech_dj        10567  0 
usbhid                 41466  0 
hid                    88502  3 hid_generic,usbhid,hid_logitech_dj
sr_mod                 14898  0 
sd_mod                 30730  4 
cdrom                  34848  1 sr_mod
ata_generic             3370  0 
pata_acpi               3387  0 
crc32c_intel           14185  0 
firewire_ohci          31837  0 
firewire_core          51955  1 firewire_ohci
ahci                   22792  5 
uhci_hcd               24531  0 
ehci_pci                4120  0 
libahci                21169  1 ahci
crc_itu_t               1363  1 firewire_core
xhci_hcd               89423  0 
ehci_hcd               47672  1 ehci_pci
libata                171016  4 ahci,pata_acpi,libahci,ata_generic
usbcore               177151  6 usblp,uhci_hcd,ehci_hcd,ehci_pci,usbhid,xhci_hcd
scsi_mod              127772  3 libata,sd_mod,sr_mod
usb_common              1648  1 usbcore
radeon                807573  2 
i2c_algo_bit            5391  1 radeon
drm_kms_helper         35438  1 radeon
ttm                    65324  1 radeon
drm                   231136  4 ttm,drm_kms_helper,radeon
i2c_core               23720  5 drm,i2c_i801,drm_kms_helper,i2c_algo_bit,radeon


```

I already tried to change the interface from "down" to "up", but it remains down without displaying any errors. How can I solve this?

P.S: Excuse me for my english, of course.

---

### Post by varunendra on 2013-10-23
Hello Con7e, Welcome to the forums !

Yes, the interface name is usually ethx, but some drivers may force it to be something else and is no big deal.

Do you have any way to connect this system to Internet? Like wifi or a USB dongle/modem etc. If you have, please install 'ethtool' -
```
sudo apt-get update && sudo apt-get install ethtool
```

Then post back the output of following commands -
```
uname -mr
lspci -nnk | grep -A2 0200
nm-tool
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
cat /etc/udev/rules.d/70-persistent-net.rules
sudo ethtool enp7s1
```
If you can not install ethtool, replace the last command with "**sudo mii-tool -vv enp7s1**", hopefully, that is pre-installed.

---

### Post by Con7e on 2013-10-23
[COLOR=#DD4814]Hi [varunendra]("http://ubuntuforums.org/member.php?u=1043629")[/COLOR][COLOR=#000000] 

Thank you for your post, but I've actually figured out bu myself how to fix the issue :).

I had all the drivers correctly installed, I just had to "force" it to work, like:

```
mii-tool -F 100baseTx-FD
```

or, with ethtool:

```
ethtool -s eth0 speed 100 duplex full autoneg on[/COLOR]
```

Thank you anyway!

---

### Post by varunendra on 2013-10-23
Haha.. glad the old trick worked for you :P

Please mark the thread as [SOLVED] using the "**Thread Tools**" link above the top post. It helps others by indicating that the thread contains a potential solution to the topic. :)

---

