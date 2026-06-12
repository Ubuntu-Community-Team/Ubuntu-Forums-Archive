---
title: "Please help with Ubuntu 17.10 on Dell XPS 15 9560 late 2017"
date: 2017-11-06
forum: Hardware
---

### Post by jackdale on 2017-11-06
I needed a new laptop and I had seen good reviews of this one for ubuntu in early 2017 but I'm having problems with freezing as follows

Terminal - lspci and lshw will cause a total system freeze most times I try to use them
Terminal - reboot and shutdown commands every single time
NOT a problem if boot into console mode, only from terminal on GUI
Cannot login to X.org session (total system freeze on attempt)
wireless card will stop working (resisting attempts to restart it and requires system reboot to work again) when connecting to my iphone's hotspot

System: Ubuntu 17.10, fresh install from ubuntu repo, verified with md5, dual boot with windows 10 pro on ahci mode (default is RAID and SSD not detected)
Dell XPS 15 9560
7th Generation Intel Core i7-7700HQ Quad Core Processor (8 Threads) (6M cache; at default settings)
15.6" 4K Ultra HD (3840 x 2160) InfinityEdge touch display (works well by the way and ubuntu natively detects the correct size - whereas in debian and kali, everything is tiny)
RAM 32GB, DDR4, 2400MHz
1TB PCIe SSD
Graphics: NVIDIA GeForce(R) GTX 1050 with 4GB GDDR5
Killer 1535 802.11ac 2x2 WiFi and Bluetooth (Qualcomm Atheros QCA6174 802.11ac; ath10k)

I'm not too bothered by the wifi card but the terminal stuff is my main concern.
I've made a bug report under ubuntu-terminal.app but no one seems too interested by it, which means I must be the only one, perhaps.
any suggestions would be welcome.
THanks

---

### Post by oldfred on 2017-11-06
Most Dell users have had to turn RAID off and turn AHCI on.
And you need nVidia driver from Ubuntu repository or ppa.
And you have to update Dell UEFI to latest version and Samsung firmware to latest version.

 Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444) 
      
 Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)

---

### Post by jackdale on 2017-11-07
Thanks for making the effort to reply.  As per my post, AHCI is already on and RAID off (as installation does not work otherwise); I've already got the latest nVidia driver and all firmware is up to date.

I am able to run everything else that I want without any problems, but as soon as I use lspci or lshw or reboot or shutdown from the terminal, it all goes downhill.  Even other hardware-heavy terminal commands (such as crunch) are fine and I'm otherwise happy with the laptop (apart from wishing that the wifi card ran on ath9k)


FWIW - I tried a debian 9 live USB and a kali 2017.2 live usb with no problems; ubuntu live usb did not work on this computer (although all three live usbs work fine on my oldish Asus laptop).

---

### Post by oldfred on 2017-11-07
On my Skylake system I manually updated Intel code, but now see that repository has new version from my synaptic and fix released in bug report.
 Skylake Best to have newest microcode from Intel version 3.20160714.1 or later
grep microcode /proc/cpuinfo
cat /proc/cpuinfo should be microcode 0x9d or 0x9e or newer in hex 


 Issue affecting some Skylake/Kaby Lake processors if hyper-threading enabled.
[https://ubuntuforums.org/showthread.php?t=2364663](https://ubuntuforums.org/showthread.php?t=2364663)
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-HT-Bug-KBL095](http://www.phoronix.com/scan.php?page=news_item&px=Intel-HT-Bug-KBL095)


 intel-microcode is out of date, version 20170707 fixes errata on 6th and 7th generation platforms 

[https://bugs.launchpad.net/ubuntu/xenial/+source/intel-microcode/+bug/1700373](https://bugs.launchpad.net/ubuntu/xenial/+source/intel-microcode/+bug/1700373)
fred@Asusz97:~$ dpkg-query -W intel-microcode
intel-microcode	3.20170707.1~ubuntu16.04.0

---

### Post by jackdale on 2017-11-07
I just came in to report that I ran the latest update and it seems to all be fixed.

Oldfred, thanks for trying to help anyway but it all seems to have fixed itself.

as for the microcode, I'm on 0x5e but it seems to have no problems, but I'll keep it in mind and wait for an update to propagate.

<code>
cat /proc/cpuinfo | grep microcode
microcode	: 0x5e
microcode	: 0x5e
microcode	: 0x5e
microcode	: 0x5e
microcode	: 0x5e
microcode	: 0x5e
microcode	: 0x5e
microcode	: 0x5e
</code>

---

