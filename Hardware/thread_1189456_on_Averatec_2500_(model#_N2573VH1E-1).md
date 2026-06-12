---
title: "on Averatec 2500 (model# N2573VH1E-1)"
date: 2009-06-16
forum: Hardware
---

### Post by lgambit on 2009-06-16
I recently bought an Averatec 2500 from MicroCenter. This little laptop comes with quite a bit of power for the price.  
 

 This should get all your hardware working properly.

BIOS
Bios v: A1222AT9 Ver 7.01
I bought mine with a different BIOS. I had to download and flash my BIOS to this version
                               
OS
Ubuntu 9.04 (Jaunty) amd64
I upgraded the kernel to 2.6.30. I used this repository from [[COLOR=#000080]_voria._[/COLOR]]("https://launchpad.net/%7Evoria/+archive/ppa/+build/1058404")
                               
Video
ATI RS690T Integrated Graphics (ATI Radeon X1270)              
radeon or radeonhd Open source driver  (radeon or radeonhd) works fine. 3D acceleration will only support up to 2048x2048 screen resolution
 ATI Proprietary driver will not work with Xorg 1.6.
             
Sound
[FONT=OfficinaSans-Book, Apple LiSung Light, sans-serif][SIZE=2]Azalia interface [/SIZE][/FONT]Codec ALC888              
ALSA-1.0.20  Edit &#8220;/etc/modprobe/alsa-base.conf&#8221; and add the following line: &#8220;options snd-hda-intel model=targa-2ch-dig probe_mask=1 position_fix=1&#8221; attached is my &#8220;/etc/asound.state&#8221; file 
Select &#8220;Front Mic&#8221; for integrated Mic. turn up the volume for it. Do not turn up the &#8220;Mic Boost&#8221; volume
[[COLOR=#000080]_Instructions to upgrade ALSA_[/COLOR]]("http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/")
                   
[FONT=OfficinaSans-Book, Apple LiSung Light, sans-serif][SIZE=2]SD/ MMC/ MS[/SIZE][/FONT]
Run out of the box, nothing extra to do
                               
LAN
Realtek Semiconductor Co., Ltd. RTL8111/8168B              
Run out of the box, nothing extra to do
                               
WLAN
Atheros Communications Inc.              
madwifi &#8211; Subversion version 
Disable ath5k module by blacklisting it. Compile the latest version of Madwifi drivers and you are set. 
You can find instructions [[COLOR=#000080]_here_[/COLOR]]("http://nowardev.wordpress.com/2009/05/06/kubuntu-904-atheros-communications-inc-ar242x-80211abg-wireless-pci-express-adapter-rev-01/").                           
                               
USB
 Works out of the box
                               
Touchpad              
Works out of the box

---

