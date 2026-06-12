---
title: "Acer Aspire V3-571G Unreliable Wireless"
date: 2012-10-06
forum: Hardware
---

### Post by GCoffee on 2012-10-06
Hello All,

I've just installed the x64 Desktop edition of 12.04 on my Acer Aspire V3 571G. The wireless does connect, though it can take a while. The problem is the wireless only stays connected for 45 minutes max. before it drops out, and then it continually 'reconnects' (never actually connecting to the network) until I either switch between a few networks or turn wireless off and on again. 

I'm using the ath9k driver that Ubuntu provides, and (although it shouldn't make a difference) GNOME3.

Is there a more stable wireless driver available that I could use? 

Regards,
Ben.

---

### Post by alxkarpun on 2012-10-06
Same here, with Acer v5-471.
I found (lspci | grep -i net):
Atheros Communications Inc. AR9462 Wireless Network Adapter (rev01)
and (cat /var/log/kern.log | tail -100) says that:
wlan0: deauthenticated from xx:xx:xx:xx:xx:xx (Reason: 2)

and ubuntu request to enter wireless password from time to time.

Will be appreciated for any help

---

### Post by teaker1s on 2012-10-11
AR9462 aspire  v3-551 same issue, the odd thing is that it runs fine first install and then after a while it drops association.
logs show that wireless associates and then times out.

bug reports show we are far from alone.
The strange bit is it works fine then dies

---

### Post by gijake on 2012-10-18
Same problem would really like a fix for this it seems to be getting worse not better

---

### Post by gratzimilian on 2012-11-21
Is this issue still present in 12.10?

---

### Post by froanas on 2012-11-25
I've had the same problem for months now, and I just found this fix:

```
sudo rmmod ath9k
sudo modprobe ath9k nohwcrypt=1
```

It seems to work so far, fingers crossed.

EDIT:
To make this permanent:
1. create a file name ath9k.conf under /etc/modprobe.d (touch /etc/modprobe.d/ath9k.conf - for example )
2. nano /etc/modprobe.d/ath9k.conf and introduce one line containing the following:

```
options ath9k nohwcrypt=1
```

3.Save the file
4.Reboot, OR do

```
rmmod ath9k
modprobe -b ath9k
```

---

### Post by gratzimilian on 2012-11-26
Any other issues experienced with the V3-571G laptops? All other hardware works as expected?? Thinking about getting one..

Thanks in advance!

---

### Post by andreadi on 2012-11-26
Just set up one V3-571G

Works perfect.

First thing you have to do before anything. 
*Do not download Nvidia drivers yourself.

1. Install bumblebee [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee) it will download what is needed.

2. To get wireless working update all packages and then
sudo apt-get update && sudo apt-get upgrade
again and it got things fixed for me
[http://www.upubuntu.com/2012/10/how-to-fix-unity-and-wireless-problems.html](http://www.upubuntu.com/2012/10/how-to-fix-unity-and-wireless-problems.html)

3. To get brighness controls
[http://askubuntu.com/questions/128463/brightness-controls-dont-work-on-an-acer-4741g](http://askubuntu.com/questions/128463/brightness-controls-dont-work-on-an-acer-4741g)

---

### Post by gratzimilian on 2012-11-26
> **andreadi said:**
> Just set up one V3-571G

Works perfect.

First thing you have to do before anything. 
*Do not download Nvidia drivers yourself.

1. Install bumblebee [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee) it will download what is needed.


I was a bit confused by this as I thought they were either Intel *OR* NVidia and there wasn't an Optimus option, went to investigate the Acer website and found [this]("http://www.acer.co.uk/ac/en/GB/content/compare/NX.RYFEK.016-NX.RZJEK.010-NX.RZLEK.004"). All with the same model number but with differing submodel numbers.

NX.RYFEK.016 - being Intel 3000 card
NX.RZJEK.010 - being a 1GB NVidia GT630M
NX.RZLEK.004 - being a 2GB Nivida GT630M

Is there an Optimus version as well somewhere? Are there issues with the latest nvidia drivers included with the official ubuntu repos?

Finally, what is real world battery experience like? Specifications are quite often over stated so it would be useful to know what battery is like in common scenarios if you're able to advise? I'm currently torn between the NX.RZLEK.004 and a Lenovo Z580, differences being better quoted battery life on the Lenovo but better NVidia card (2GB) on the Acer and the fact that it has Bluetooth built in (and version 4!).

Thanks

---

### Post by gratzimilian on 2012-11-26
> **andreadi said:**
> 
2. To get wireless working update all packages and then
sudo apt-get update && sudo apt-get upgrade
again and it got things fixed for me
[http://www.upubuntu.com/2012/10/how-to-fix-unity-and-wireless-problems.html](http://www.upubuntu.com/2012/10/how-to-fix-unity-and-wireless-problems.html)

Also, does this mean the card is a broadcom wireless card? Earlier posts suggest it's an Atheros (ath9)..Another potential difference in models?

---

### Post by froanas on 2012-11-26
> **gratzimilian said:**
> Also, does this mean the card is a broadcom wireless card? Earlier posts suggest it's an Atheros (ath9)..Another potential difference in models?

No, it is an Atheros chip, gratzimilian was wrong. His post was about moving from 12.04 to 12.10, and had nothing to do with the V3-571G.

Also, I'm sad to report that the method in my previous post does not seem to work :(

---

### Post by gratzimilian on 2012-11-27
> **froanas said:**
> No, it is an Atheros chip, gratzimilian was wrong. His post was about moving from 12.04 to 12.10, and had nothing to do with the V3-571G.

Hey it was andreadi who was wrong :P Shame it's not working, they do look like pretty good hardware for the money. Can you lspci and post the exact details of the device?

Have you had any other issues at all froanas? Brightness control was an issue on my previous (old) acer.

---

### Post by Medion on 2012-12-02
Hi,

Not sure if I should make a new tread or not. I'm also having trouble with Acer and wireless.

I have tried all of the above an nothing works. I'm using a new install of ubuntu 12.10 in dualboot with windows 8. In the installer wireless doesnt work at first (when the 3 checkmarks displays - enough storage and so on), but later I get a question if I want to connect to wireless and then it works, but only the first time and until i reboot. 

I have an acer aspire v3 571g.

Output:

lsmod:

ken@ken-Aspire-V3-571G:~$ lsmod
Module                  Size  Used by
btusb                  18334  0 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
ghash_clmulni_intel    13180  0 
aesni_intel            51037  0 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  11 btusb,bnep,rfcomm
joydev                 17457  0 
lpc_ich                17061  0 
snd_hda_intel          33491  3 
microcode              22803  0 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
psmouse                95552  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              13215  0 
snd_seq_midi           13324  0 
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
snd_rawmidi            30512  1 snd_seq_midi
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
mei                    40690  0 
i915                  520519  3 
drm_kms_helper         46784  1 i915
drm                   275528  4 i915,drm_kms_helper
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13413  1 i915
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
acer_wmi               32453  0 
sparse_keymap          13890  1 acer_wmi
mac_hid                13205  0 
video                  19335  2 i915,acer_wmi
wmi                    19070  1 acer_wmi
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
sdhci_pci              18616  0 
sdhci                  32645  1 sdhci_pci


lshw:

ken@ken-Aspire-V3-571G:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: b8:88:e3:06:4f:c9
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=sb ip=192.168.1.102 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:b3830000-b383ffff memory:b3840000-b384ffff memory:b3850000-b38507ff
  *-network UNCLAIMED
       description: Network controller
       product: BCM43228 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:b3900000-b3903fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
ken@ken-Aspire-V3-571G:~$ 


Ouput when tried methods in link from andreadi:

method 2:

ken@ken-Aspire-V3-571G:~$ sudo apt-get install --reinstall bcmwl* firmware-b43-lpphy-installer b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'bcmwl-kernel-source' for regex 'bcmwl*'
Note, selecting 'bcmwl-modaliases' for regex 'bcmwl*'
The following packages will be REMOVED:
  firmware-b43-installer
The following NEW packages will be installed:
  bcmwl-kernel-source firmware-b43-lpphy-installer
0 upgraded, 2 newly installed, 1 reinstalled, 1 to remove and 1 not upgraded.
Need to get 0 B/1,204 kB of archives.
After this operation, 3,608 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 167715 files and directories currently installed.)
Removing firmware-b43-installer ...
(Reading database ... 167712 files and directories currently installed.)
Preparing to replace b43-fwcutter 1:015-14 (using .../b43-fwcutter_1%3a015-14_amd64.deb) ...
Unpacking replacement b43-fwcutter ...
Selecting previously unselected package bcmwl-kernel-source.
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb) ...
Selecting previously unselected package firmware-b43-lpphy-installer.
Unpacking firmware-b43-lpphy-installer (from .../firmware-b43-lpphy-installer_1%3a015-14_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:015-14) ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
Building only for 3.5.0-17-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Setting up firmware-b43-lpphy-installer (1:015-14) ...
No chroot environment found. Starting normal installation
No supported card found.
Use proper b43 or b43legacy firmware.
Aborting.
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
ken@ken-Aspire-V3-571G:~$ 


Method 3:

ken@ken-Aspire-V3-571G:~$  sudo apt-get remove bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 3,609 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 167771 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
ken@ken-Aspire-V3-571G:~$ 

ken@ken-Aspire-V3-571G:~$ sudo apt-get install firmware-b43-installer b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following packages will be REMOVED:
  firmware-b43-lpphy-installer
The following NEW packages will be installed:
  firmware-b43-installer
0 upgraded, 1 newly installed, 1 to remove and 1 not upgraded.
Need to get 0 B/3,532 B of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 167716 files and directories currently installed.)
Removing firmware-b43-lpphy-installer ...
Selecting previously unselected package firmware-b43-installer.
(Reading database ... 167712 files and directories currently installed.)
Unpacking firmware-b43-installer (from .../firmware-b43-installer_1%3a015-14_all.deb) ...
Setting up firmware-b43-installer (1:015-14) ...
No chroot environment found. Starting normal installation
This card is actually not tested. Please install the driver manually.
ken@ken-Aspire-V3-571G:~$ 


Output when tried method from froanas:

ken@ken-Aspire-V3-571G:~$ rmmod ath9k
ERROR: Module ath9k does not exist in /proc/modules
ken@ken-Aspire-V3-571G:~$ 


I've also tried to blacklist acer-wmi from this tread, but it didn't help: [http://ubuntuforums.org/showthread.php?t=2070002&highlight=aspire+571g+wireless](http://ubuntuforums.org/showthread.php?t=2070002&highlight=aspire+571g+wireless)

---

### Post by gratzimilian on 2012-12-02
And lspci?

---

### Post by Medion on 2012-12-02
lspci:

ken@ken-Aspire-V3-571G:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 630M] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)
02:00.2 System peripheral: Broadcom Corporation Device 16be (rev 10)
02:00.3 System peripheral: Broadcom Corporation Device 16bf (rev 10)
03:00.0 Network controller: Broadcom Corporation BCM43228 802.11a/b/g/n

---

### Post by Broken Candain on 2012-12-02
To all those still having this problem,
I have an Acer Aspire V3-771G, I had the same problems described here running Ubuntu 12.04 and all of the problems seemed to be corrected in 12.10.  I have been running 12.10 since it came out and have yet to have wireless issues

---

### Post by gratzimilian on 2012-12-03
Does [this]("http://askubuntu.com/questions/215226/broadcom-bcm43228-802-11a-b-g-n-wireless-adapter-stopped-working-on-update") help anyone with the V3-571G? I have a broadcom wifi card on a Dell laptop that is equally unstable under Ubuntu, when I first started using it the connection would peak and gradually drop to almost zero when doing a speed test (however under Windows 7 it was solid and stable at high speed all the time). I changed Ubuntu drivers and ended up with a stable but data rate was about a 10th of that under Windows.

---

### Post by Medion on 2012-12-03
I finally got it working, at least for a few hours and no problems at all. I don't know what made it work. What I did different from last time was this: I installed the 32-bit version  of Ubuntu, and I left the cable in during installation. Then it was just to choose the wireless icon in the top corner an choose my network. Thank you all.

---

### Post by gratzimilian on 2012-12-04
Maybe fixed with the latest kernel update? I believe this was recently only in the last few days.. 3.5.0-19?

---

### Post by tereshkosg on 2013-01-20
I have 

03:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)

in my V3-571. Wireless was reconnecting every 5 to 10 seconds. After trying:

1) nohwcrypt ... 
2) power management off 
3) IPV6 off  

without any luck. Found another post suggesting to blacklist "acer_wmi".


Running 
```

sudo modprobe -rfv acer_wmi
``` Immediately fixed the problem. Then i blacklisted the module and now everything seems okay.

Now, however, I am wondering what have a lost by removing this module ?


EDIT: Actually, I celebrated too early .. still facing unreliable wireless :(

---

### Post by AlexandertheGreat on 2013-02-11
I use windows 7 home prem 64 and i had the same problems. 

I found a Czech Republic unofficial atheros website, where i found a driver that solved disconnections problem.

It is a driver problem not a hardware problem as i initially thought.

With this, i hope i help you to find a solution on linux platform.

---

