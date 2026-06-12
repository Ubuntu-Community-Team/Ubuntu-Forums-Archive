---
title: "how do I compile a driver for Netgear wnda4100-100nas usb lan adpater"
date: 2013-07-08
forum: Hardware
---

### Post by hotwaxdripping on 2013-07-08
I just stumbled my way through an installation of Ubuntu 13.04, but cannot get my netgear wireless lan adapter to work.  it is recognized by the computer, and uses a Ralink RT3573 chipset, i used the lsusb command to find out.  I downloaded a driver, but I don't know how to compile it.  I don't even know what compiling is, and I only know a few basic terminal commands that were spelled out step by step on the internet.  Is there anything else you need to know about my computer's specs in order to help me?  I downloaded the RT3573sta linux driver from 
[http://wikidevi.com/wiki/Netgear_WNDA4100](http://wikidevi.com/wiki/Netgear_WNDA4100)

I'm pretty sure that's the right driver.  By the way, I installed Ubuntu through the windows wubi.exe file.  Does my problem have anything to do with that?  Thank you for your help.  I just want to know what to type, step by step.  thanks.

p.s.  this is also my first time actually posting on any online forum, btw.

---

### Post by varunendra on 2013-07-08
Welcome to the forums hotwaxdripping !

> **hotwaxdripping said:**
> I downloaded the RT3573sta linux driver from 
[http://wikidevi.com/wiki/Netgear_WNDA4100](http://wikidevi.com/wiki/Netgear_WNDA4100)

What is the name of the downloaded driver file? I would recommend to download the driver from Ralink's official site here : [http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)

[INDENT]1) Download the [RT3573 USB]("http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5034") driver. Copy this downloaded file to your desktop. Then -

2) Right-click on it > Extract here. This will extract a folder named "20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO".

3) Open the file "config.mk" in "os/linux" directory within the extracted folder.

4) Change line #31 from "HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**[COLOR="#FF0000"]n[/COLOR]**" to "HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**[COLOR="#006400"]y[/COLOR]**". Save and close the file.

5) Now open a terminal (ctrl+alt+T) and run following commands :
```
cd ~/Desktop/20120911_RT3573_Linux_STA_v2.5.0.0_Rev1_DPO
make
sudo make install
```
Watch out for errors, and post back if there are any, especially during the "make" process. Exactly one error in the last (regarding "tftpboot") is normal and can be safely ignored. Post back the exact error message(s) if there are more.[/INDENT]

You may additionally have to do -
```
sudo modprobe -v rt3573sta
```
..or simply reboot.

Let us know the outcome. :)

---

### Post by hotwaxdripping on 2013-07-09
followed directions exactly and it worked for the most part.  The netgear wnda4100 connects to my router, and shows other broadcasting SSID's.  Had to use the modprobe command to achieve a connection, then the computer froze up.  Now the WNDA4100 connects but as soon as I open my browser the computer freezes up.  Is this related to the recently made changes?

---

### Post by varunendra on 2013-07-09
> **hotwaxdripping said:**
> Now the WNDA4100 connects but as soon as I open my browser the computer freezes up.  Is this related to the recently made changes?

Maybe. I have been seeing freezing issues with compiled ralink drivers + 13.04 combination, but not with this one so far. If it seems to lockup only while opening the browser, can you use internet otherwise? Try (in increasing level/scope of test) -
```
ping *<IP of your gateway>*
ping google.com
sudo apt-get update
```
Does it fail/freeze at any step above? Which one?

And please follow the "Wireless Script" link in my signature, run the script as suggested in the linked post and post back the report it generates.

---

### Post by hotwaxdripping on 2013-07-09
First off,  let me say thank you for all your time and effort.  This is my first experience with linux and I think I like it!  Now to business...

I pinged my gateway and it worked find, latency was between 2-3ms.  I pinged google.com and it worked fine, lattency was between 65-70ms.  But when I tried the update, the computer froze at 17%.  I tried the update again, and it froze, but  this time a black screen with a lot of info on it came on saying something about a panic occuring.  I couldn't even cut and pasteit because the pc froze.   

I ran the wireless script, and here are the results:

```

*************** info trace ***************

***** uname -a *****

Linux ubuntu 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

***** lspci *****

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express [14e4:167a] (rev 02)
    Subsystem: Dell OptiPlex 745 [1028:01da]
    Kernel driver in use: tg3

***** lsusb *****

Bus 001 Device 003: ID 0846:9012 NetGear, Inc. WNDA4100 802.11abgn 3x3:3 [Ralink RT3573]
Bus 002 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 006 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 007 Device 002: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** iwconfig *****

ra0       Ralink STA  ESSID:"Verizon-890L-BE70"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.442 GHz  Access Point: <MAC address removed>   
          Bit Rate=65 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-20 dBm  Noise level:-31 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


***** rfkill *****


***** lsmod *****

rt3573sta             721036  1 
rt2800usb              26854  0 
rt2x00usb              20635  1 rt2800usb
rt2800lib              66507  1 rt2800usb
rt2x00lib              54869  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              606457  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              510937  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: ra0  [Wi-Fi connection 1] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            usb
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    I'vegoturmacaddress: Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 99 WPA
    2WIRE809:        Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    2WIRE671:        Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    2WIRE410:        Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    CRUSADER:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    2WIRE878:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    jacobpeepee:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 16 Mb/s, Strength 42 WPA WPA2
    BHNSBG6580FFBE:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 16 Mb/s, Strength 42 WPA
    SilverDolphin:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 16 Mb/s, Strength 35 WPA WPA2
    BHNSBG658001DA:  Infra, <MAC address removed>, Freq 2412 MHz, Rate 16 Mb/s, Strength 32 WPA
    2WIRE120:        Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 42 WEP
    jacobpeepee-guest: Infra, <MAC address removed>, Freq 2437 MHz, Rate 16 Mb/s, Strength 45
    SilverDolphin-guest: Infra, <MAC address removed>, Freq 2412 MHz, Rate 16 Mb/s, Strength 35
    chi5:            Ad-Hoc, <MAC address removed>, Freq 2412 MHz, Rate 11 Mb/s, Strength 42
    *Verizon-890L-BE70: Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 100 WPA2
    CGD24G7D:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    lucerofanshier:  Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

ra0       Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"CRUSADER"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/100  Signal level=-79 dBm  Noise level=-74 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
          Cell 02 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"SilverDolphin"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/100  Signal level=-81 dBm  Noise level=-89 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 03 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"SilverDolphin-guest"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/100  Signal level=-81 dBm  Noise level=-89 dBm
                    Encryption key:off
                    Bit Rates:144 Mb/s
          Cell 04 - Address: <MAC address removed>
                    Protocol:802.11b
                    ESSID:"chi5"
                    Mode:Ad-Hoc
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/100  Signal level=-75 dBm  Noise level=-83 dBm
                    Encryption key:off
                    Bit Rates:11 Mb/s
          Cell 05 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"BHNSBG658001DA"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/100  Signal level=-81 dBm  Noise level=-76 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
          Cell 06 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"Verizon-890L-BE70"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality=89/100  Signal level=-55 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 07 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"I'vegoturmacaddress"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality=100/100  Signal level=-37 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"2WIRE120"
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality=37/100  Signal level=-75 dBm  Noise level=-77 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 09 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"jacobpeepee"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/100  Signal level=-79 dBm  Noise level=-81 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 10 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"jacobpeepee-guest"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/100  Signal level=-77 dBm  Noise level=-79 dBm
                    Encryption key:off
                    Bit Rates:144 Mb/s
          Cell 11 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"BHNSBG6580FFBE"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/100  Signal level=-73 dBm  Noise level=-75 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
          Cell 12 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"2WIRE878"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/100  Signal level=-83 dBm  Noise level=-85 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:""
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=7/100  Signal level=-87 dBm  Noise level=-82 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"2WIRE410"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality=7/100  Signal level=-87 dBm  Noise level=-89 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"2WIRE671"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality=26/100  Signal level=-79 dBm  Noise level=-86 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"2WIRE809"
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality=42/100  Signal level=-73 dBm  Noise level=-80 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"lucerofanshier"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality=23/100  Signal level=-81 dBm  Noise level=-76 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD260050F204104A0001101044000102104900140024E26002000101600000020001600100020001
          Cell 18 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"CGD24G7D"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=13/100  Signal level=-85 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102


***** resolv.conf *****

nameserver 127.0.1.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** dmesg *****

[   22.683022] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.683370] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.789867] wlan0: authenticate with <MAC address removed>
[   25.853778] wlan0: send auth to <MAC address removed> (try 1/3)
[   25.856066] wlan0: authenticated
[   25.864120] wlan0: associate with <MAC address removed> (try 1/3)
[   25.885132] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=7)
[   25.894606] wlan0: associated
[   25.894644] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1366.840013] phy0 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffff8802].
[ 1366.840288] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1376.258083] rtusb init rt2870 --->
[ 1376.963948] <==== rt28xx_init, Status=0
[ 1377.820075] <==== rt28xx_init, Status=0
[ 1378.650324] <==== rt28xx_init, Status=0
[ 1379.493699] <==== rt28xx_init, Status=0
[ 1380.314824] <==== rt28xx_init, Status=0

****************** done ******************

```

---

### Post by varunendra on 2013-07-09
No problem, that's fun ! :)

Can't say if this could be the cause but this is not good -
> **hotwaxdripping said:**
> 
```

***** lsmod *****

rt3573sta             721036  1 
[COLOR="#FF0000"]rt2800usb              26854  0 
rt2x00usb              20635  1 rt2800usb
rt2800lib              66507  1 rt2800usb
rt2x00lib              54869  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              606457  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              510937  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib[/COLOR]

```
The native rt2800usb driver is still loading and would be conflicting with the rt3573sta we compiled. Blacklist it to prevent it from loading -
```
ehco "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Now reboot and run "lsmod | grep rt2" again to see if any of the above (in red) are still loaded. There should be only rt3573sta.

---

### Post by hotwaxdripping on 2013-07-09
I blacklisted rt2800usb and ran the wireless script program again and rt3573sta was all that was listed under ****lsmod*** section.  (the "lsmod | grep rt2" command didn't seem to do anything and didn't show any results.)  computer froze up immediately when I opened firefox.  It went to the black screen again, and the last line said:

drm_kms_helper:  panic occurred, switching back to text console.

---

### Post by varunendra on 2013-07-09
> **hotwaxdripping said:**
> computer froze up immediately when I opened firefox.  It went to the black screen again, and the last line said:

drm_kms_helper:  panic occurred, switching back to text console.

I'm not sure if it is network or wireless related, because "drm_kms_helper" is a graphics related driver.

I'm also not sure if it cab be triggered by wireless or networking in any way, nor do we have any clue (apart from it happening when you open browser) about what exactly it is triggered by. If you are sure it is triggered by wireless, you can try a few things -

[INDENT]1) First, try booting with "[nomodeset]("https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation")" parameter to boot with low graphics mode, and see if you can use your wireless without problems.

2) Try turning the N-channel off in your router. That is, if it is set to use b/g/n or a/b/g/b channels, change it to b/g only > save and reboot the router.

3) In addition to above (if required), try forcing a lower speed on your wireless interface - ```
sudo iwconfig ra0 rate 48M auto
``` This will force a bit rate of 48 Mb/s max.

4) The loading of rt2800usb indicates that it recognizes yourcard. We may try disabling the rt3573sta, and try to make that one work.
[/INDENT]


**EDIT:**
As per this thread, at least one user had better luck with newer kernel version (3.9x) : [http://ubuntuforums.org/showthread.php?t=2142150](http://ubuntuforums.org/showthread.php?t=2142150) (post #4)
You may try that if you wish, I personally don't consider a WUBI installation worth so much trouble though. If the above tricks don't work for you, I'd suggest to do a proper installation of 12.04 LTS instead.

---

### Post by hotwaxdripping on 2013-07-10
I'm giving up on the netgear wnda4100 adapter altogether.  I've aquired a B-link adapter with a Realtek RTL8188CUS chipset apparently using the rtl8192 native driver.  computer seems snappy and fast.  am definately considering a bootable usb install, though.

---

### Post by kurt18947 on 2013-07-11
> **hotwaxdripping said:**
> I'm giving up on the netgear wnda4100 adapter altogether.  I've aquired a B-link adapter with a Realtek RTL8188CUS chipset apparently using the rtl8192 native driver.  computer seems snappy and fast.  am definately considering a bootable usb install, though.

It's interesting that RTL8188CUS works 'out of the box' for you.  Generally that chipset has required RealTek's driver but there's no arguing with what works.:D

---

### Post by varunendra on 2013-07-11
kurt18947,

rtl8192cu (as well as ce/se) used to work very well before 12.04, it seems there has been some regression in these drivers due to recent changes in kernel code. And who knows if they still work great for a majority of users. Afterall, only those come here who have problems ! ;)

---

### Post by kurt18947 on 2013-07-11
> **varunendra said:**
> kurt18947,

rtl8192cu (as well as ce/se) used to work very well before 12.04, it seems there has been some regression in these drivers due to recent changes in kernel code. And who knows if they still work great for a majority of users. Afterall, only those come here who have problems ! ;)

Two steps forward, one step back, eh?  And true that  those with problems - or an axe to grind - post here.  My experience has been that for the most part newer distros have better wifi support.  I have an ath9k adapter and a couple RTL-8192SU adapters that required patches/additional software to work in Ubuntu prior to about 11.04.  Now they just work.

---

