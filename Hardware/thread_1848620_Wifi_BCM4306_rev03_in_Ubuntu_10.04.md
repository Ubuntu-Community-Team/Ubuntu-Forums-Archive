---
title: "Wifi BCM4306 rev03 in Ubuntu 10.04"
date: 2011-09-22
forum: Hardware
---

### Post by SraM on 2011-09-22
Hi everyone,

I was using Ubuntu 9.10 and my chipset Broadcom 4306 worked perfectly with the additional proprietary drivers made available. But when I upgraded to 10.04 I realized that my WiFi was not working anymore. 

I saw that the STA drivers have been included to the kernel but my chipset has not been added to these drivers. I have a BCM4306 rev03 in my Compaq Presario R3000.

I tried installing the proprietary drivers but nothing happened. Could someone help me fix it? Upgrading to the next versions does not solve the problem so I hope I can find a solution that I will be able to use in the next LTS release as well!

I have already installed bcmwl-modaliases et b43-fwcutter. The button for the wifi does not seem to be working (always LED off ) and before (Ubuntu 9.10 and prior) it was almost constantly ON.

Thank you in advance for your help.

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"

```
```
~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
~$ lspci -nn | grep -i net
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

```
```
~$ sudo lshw -C network 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:48:ec:9c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.***.*** latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:18 ioport:7000(size=256) memory:e8104000-e81040ff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:e8100000-e8101fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: **:**:**:**:**:**
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```
```
~$ lsmod
Module                  Size  Used by
nls_utf8                1069  1 
udf                    78785  1 
crc_itu_t               1371  1 udf
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
binfmt_misc             6587  1 
pcmcia                 30784  0 
snd_intel8x0           25652  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                    1153  2 
nouveau               467048  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    50103  1 nouveau
joydev                  8740  0 
drm_kms_helper         29329  1 nouveau
snd                    54244  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
b43                   163556  0 
yenta_socket           20408  2 
drm                   162377  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            5028  1 nouveau
ppdev                   5259  0 
rsrc_nonstatic         10015  1 yenta_socket
mac80211              205402  1 b43
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
amd64_agp               7165  1 
soundcore               6620  1 snd
cfg80211              126144  2 b43,mac80211
video                  17375  0 
output                  1871  1 video
k8temp                  3152  0 
psmouse                63677  0 
serio_raw               3978  0 
agpgart                31724  3 ttm,drm,amd64_agp
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
parport_pc             25962  1 
shpchp                 28835  0 
led_class               2864  1 b43
i2c_nforce2             5199  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
8139too                18545  0 
8139cp                 16186  0 
ssb                    38934  1 b43
mii                     4381  2 8139too,8139cp
pata_amd                8766  4 

```
```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr **:**:**:**:**:**  
          inet adr:192.168.***.***  Bcast:192.168.***.***  Masque:255.255.255.0
          adr inet6: ****::***:****:****:****/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:2929 erreurs:0 :0 overruns:0 frame:0
          TX packets:3075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1044573 (1.0 MB) Octets transmis:406865 (406.8 KB)
          Interruption:18 Adresse de base:0x7000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:8 erreurs:0 :0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:480 (480.0 B) Octets transmis:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr **:**:**:**:**:**  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

```
```
~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```
```
~$ uname -r -m 
2.6.32-33-generic i686

```
```
~$ cat  /etc/network/interfaces
auto lo
iface lo inet loopback

```
```
~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto Eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        **:**:**:**:**:**

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.***.***
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.***.***

    DNS:             192.168.***.***


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        **:**:**:**:**:**

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

```

---

### Post by garvinrick4 on 2011-09-22
Open synaptics type bcm in search window and install the 2 marked and make sure nothing else bcm installed. Make sure you hit green apply arrow so as to install.
Take wired cable out and reboot.

---

### Post by SraM on 2011-09-23
> **garvinrick4 said:**
> Open synaptics type bcm in search window and install the 2 marked and make sure nothing else bcm installed. Make sure you hit green apply arrow so as to install.
Take wired cable out and reboot.

In Ubuntu 10.04 I can't find firmware-b43-installer. I think I would get that with 10.10 or 11.04. Are you sure it is available in the repositories?

Maybe I should upgrade in order to get this firmware-b43-installer...

Is there another way to fix it in the LTS without using firmware-b43-installer?

---

### Post by garvinrick4 on 2011-09-23
You know I do not have a 10.04 left on my system. I should load one just for this reason. I cannot remember
what repository (restricted in 10.04) the bcm or b43 drivers are in. Try typing b43 in the search window of synaptic's, 
You have got to have the cards driver and 10.04 worked with the broadcom cards there are just a ton
of machines with those cards, Dells seemed to have just about all broadcom.  This will bump it up there
will be a user with a 10..04 around to tell you where those drivers are. I am going to try to find out for you
do the b43 thing, and make sure your repositorys are open in "software sources" main, univers, restricted
multiverse then do a 
```
sudo apt-get update 
```So they are refreshed, then check you Synaptics, I will be back, let me know if you found the drivers for bcm
or b43.

---

### Post by garvinrick4 on 2011-09-23
**b43 - Internet access**

 If you have some other kind of Internet access on your computer, you can download the firmware by simply installing the b43-fwcutter package which does the download and setup for you automatically.  
[IMG]https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?action=AttachFile&do=get&target=b43-fwcutter.png[/IMG] 
**Step 1.** 
To install b43-fwcutter issue the following command in a **terminal** (under the desktop menu **Applications > Accessories > Terminal**) and follow the prompts: 

~$ ```
sudo apt-get install b43-fwcutter
```
### Use the tab key and the arrow keys and the enter key when toggling in the terminal.
This should do you for 10.04.

---

### Post by SraM on 2011-09-23
> **garvinrick4 said:**
> **b43 - Internet access**

 If you have some other kind of Internet access on your computer, you can download the firmware by simply installing the b43-fwcutter package which does the download and setup for you automatically.  
[IMG]https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?action=AttachFile&do=get&target=b43-fwcutter.png[/IMG] 
**Step 1.** 
To install b43-fwcutter issue the following command in a **terminal** (under the desktop menu **Applications > Accessories > Terminal**) and follow the prompts: 

~$ ```
sudo apt-get install b43-fwcutter
```
### Use the tab key and the arrow keys and the enter key when toggling in the terminal.
This should do you for 10.04.

Hi,

Thank you for your help.

I had already installed b43-fwcutter installed but it never showed me this window and I guess that's why the drivers are not installed.

I tried to remove it in Synaptics and then install it from the terminal.
```
~$ sudo apt-get install b43-fwcutter
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les NOUVEAUX paquets suivants seront installés*:
  b43-fwcutter
0 mis à jour, 1 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 0o/17,9ko dans les archives.
Après cette opération, 115ko d'espace disque supplémentaires seront utilisés.
Préconfiguration des paquets...
Sélection du paquet b43-fwcutter précédemment désélectionné.
(Lecture de la base de données... 129910 fichiers et répertoires déjà installés.)
Dépaquetage de b43-fwcutter (à partir de .../b43-fwcutter_1%3a012-1build1_i386.deb) ...
Traitement des actions différées («*triggers*») pour «*man-db*»...
Paramétrage de b43-fwcutter (1:012-1build1) ...

``` 

Sorry it is in French but basically it installs it and never asks me if I want to extract the firmware...

Any idea why?

---

### Post by garvinrick4 on 2011-09-23
In additional drivers are they activated? Synaptics has them installed? You rebooted and took out the wired connection?
b43-fwcutter and firmware-b43-installer are installed?
Nothing else right all other has been removed.

```
rfkill list
```
Nothing blocked if so.
```
sudo rfkill unblock all
```

---

### Post by Bernmeister on 2011-12-15
This may help: [http://ubuntuforums.org/showthread.php?p=11539545#post11539545]("http://ubuntuforums.org/showthread.php?p=11539545#post11539545")

---

