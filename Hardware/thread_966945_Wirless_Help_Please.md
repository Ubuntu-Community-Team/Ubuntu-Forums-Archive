---
title: "Wirless Help Please"
date: 2008-11-01
forum: Hardware
---

### Post by userx9 on 2008-11-01
Hello everybody, and thanks for your help.  I have an HP nx9420 with an intel 3945abg wireless card.  I just installed ubuntu 8.10 x86 desktop edition yesterday and I was able to use wireless, and since normally wireless does not work with previous ubuntu distros I've tried and didn't work at first with 8.10, I thought maybe it was working because I pressed the wireless button on my laptop during bootup, but today when I press the button the wireless light on my laptop doesn't come on (even if i press the button during bootup) and I cannot get a listing of wireless networks to connect to in ubuntu.  I've read something about a wireless 'killswitch', but I'm assuming they are referring to the button on my laptop.  All software is up to date including the kernel.  I did no updates between the time when it worked and the time that it didn't.  Any help would be greatly appreciated.  

Here are some results from some commands I ran:

rand@rand:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



rand@rand:~$  ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:07:96:c2  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe07:96c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:621 errors:0 dropped:0 overruns:0 frame:0
          TX packets:660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:561366 (561.3 KB)  TX bytes:128546 (128.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24186 (24.1 KB)  TX bytes:24186 (24.1 KB)


EDIT: I also ran this command:

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5753M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 21
       serial: 00:16:d4:07:96:c2
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5753m-v3.56 ip=192.168.1.105 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:46:1d:79
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 36:74:b0:4c:9b:1b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by teaker1s on 2008-11-01
your output shows the firmware is not loaded have you tried ```
lsmod | more
``` to check that you have it listed including rfkill switch
Try (as root):
```
 modprobe iwl3945
```
Then
```
 lsmod | grep iwl3945
```

---

### Post by userx9 on 2008-11-01
Thank you for your reply.

I hadn't done that.  The results are shown below.  I'm not sure what to make of them, or even what rfkill is.  If you have any more advice, it would be nice to hear.  I'll look around some more as well.


EDIT: here are the commands I ran in response to your edit:

```
rand@rand:~$ sudo modprobe iwl3945
[sudo] password for rand: 
rand@rand:~$ sudo lsmod | grep iwl3945
iwl3945                98804  0 
rfkill                 17176  2 iwl3945
mac80211              216820  1 iwl3945
led_class              12164  1 iwl3945
cfg80211               32392  2 iwl3945,mac80211
```




EDIT: Full lsmod below (i ran the command before I saw your edit)


```
:~$ lsmod | more
Module                  Size  Used by
af_packet              25728  2 
ipv6                  263972  10 
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
rfcomm                 44432  0 
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    14600  0 
pci_slot               12552  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
lp                     17156  0 
pcmcia                 43052  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
iwl3945                98804  0 
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
joydev                 18368  0 
sdhci_pci              15360  0 
rfkill                 17176  2 iwl3945
yenta_socket           31756  1 
psmouse                45200  0 
evdev                  17696  14 
pcspkr                 10624  0 
sdhci                  23940  1 sdhci_pci
serio_raw              13444  0 
tifm_7xx1              13824  0 
mac80211              216820  1 iwl3945
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
tifm_core              16028  1 tifm_7xx1
mmc_core               58268  1 sdhci
iTCO_wdt               18596  0 
led_class              12164  1 iwl3945
parport_pc             39204  1 
iTCO_vendor_support    11652  1 iTCO_wdt
parport                42604  3 ppdev,lp,parport_pc
cfg80211               32392  2 iwl3945,mac80211
snd_seq_dummy          10884  0 
fglrx                1813960  30 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_m
idi_event
container              11520  0 
tpm_infineon           17064  0 
tpm                    22848  1 tpm_infineon
tpm_bios               14080  1 tpm
video                  25104  0 
output                 11008  1 video
intel_agp              33724  0 
snd_timer              29960  2 snd_pcm,snd_seq
wmi                    14504  0 
agpgart                42184  2 fglrx,intel_agp
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmi
di,snd_seq
battery                18436  0 
ac                     12292  0 
button                 14224  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm
,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usbhid                 35840  0 
hid                    50560  1 usbhid
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
pata_acpi              12160  0 
ahci                   37132  3 
ata_piix               24580  0 
libata                177312  4 ata_generic,pata_acpi,ahci,ata_piix
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  4 usbhid,ehci_hcd,uhci_hcd
tg3                   129924  0 
libphy                 27392  1 tg3
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3
```

---

### Post by teaker1s on 2008-11-01
there are various report's of bugs, haven't found anything conclusive except both ubuntu-geek quotes issue in hardy 
[http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html]("http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html")

or simple thing to try first, you can use the Restricted Drivers Manager-Uncheck the box for the ipw3945 and restart.

---

### Post by userx9 on 2008-11-01
> or simple thing to try first, you can use the Restricted Drivers Manager-Uncheck the box for the ipw3945 and restart.
Unfortunately, only the ATI driver is listed in the restricted drivers manager with no option to add any more.

I installed the backport packages and restarted.  While booting up, the blue wireless light came on for a split second and went off, and will not turn on.

Since this is the 6th ubuntu distribution in a row that wireless has not worked for my laptop, I think it might be time to move on to a different distro.

---

