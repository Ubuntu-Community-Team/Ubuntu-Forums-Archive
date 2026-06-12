---
title: "Need Wireless Help"
date: 2005-12-05
forum: General Help
---

### Post by eJamesPC on 2005-12-05
Hi I have been trying to get wireless working on Kubuntu 5.10.  I actually am able to type this on my wired connection, but alas no wireless

I have blacklisted acx_pci -- because it doesn't work with my card. 
I have ndsiwrapper installed with the correct drivers, but cannot get the Essid to work.
sudo iwconfig wlan0 essid ejamespc 
-- no errors

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr:4096 B   Fragment thr:4096 B
          Power Management:off
          Link Quality:100  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Does any one know what sit0 is?  Should it be there?  

  Cell 04 - Address: 00:14:BF:0C:10:CD
                    ESSID:"eJamesPC"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:0/100  Signal level:-40 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
Can see the AP in the scan, but can't set the essid  

I have read about GTkwifi but still have to install.  This laptop will not travel much, so I just want to set it up on my home AP.  I am not sure why this is so difficult, was really easy under Mandrake (IMO Mandrva SUCKS!)  Any help would be appreciated.

---

### Post by funkydan2 on 2005-12-05
Does you network use WEP or WPA encryption?  

Have you specified the key for the network anywhere?

What does your /etc/network/interfaces file look like?

---

### Post by skyboy on 2005-12-06
Well, it make a difference between capital letter or small ones, so be sure you type the same ESSID, here you have eJamesPC and then ejamespc
instead of using ifconfig, setup the /etc/network/interfaces file and then  $sudo ifup wlan0 to bring the interface up.

this is my /etc/network/interfaces file, copy paste it. If you really want you can also specify your ESSID but be sure to include capital letters.
```


# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map wlan0

iface wlan0 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid any

auto wlan0

```

---

### Post by fog on 2005-12-06
[QUOTE=eJamesPC]
Does any one know what sit0 is?  Should it be there?  
[/quote]
sit0 is your firewire, its ok to be there.

---

### Post by eJamesPC on 2005-12-06
I have tried it with and without WEP enabled.
Current settings:
ell 05 - Address: 00:14:BF:0C:10:CD
                    ESSID:"eJamesPC"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-41 dBm  Noise level:-256 dBm
                    Encryption key:off
interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid eJamesPC

---

### Post by skyboy on 2005-12-07
your quality is 0/100 !! Bizarre
 check that you are allowed to connect to the router, maybe it has MAC-control enabled.

---

### Post by eJamesPC on 2005-12-15
Hi All... 
I got it working!!!  I found more information at ndiswrapper about this specific Linksys card 104c:9066 -- I had to eject the card, re-install it and set it up.  There is a short note about setting the same settings over and over again until the card takes the settitngs.  I found that using iwconfig wlan0 **ESSID** #name# worked.  I have been using the command line and now need to figure out how to get it to set up every boot.

Thanks for everyones help :)

---

### Post by towsonu2003 on 2005-12-15
[QUOTE=eJamesPC]Hi All... 
I got it working!!!  I found more information at ndiswrapper about this specific Linksys card 104c:9066 -- I had to eject the card, re-install it and set it up.  There is a short note about setting the same settings over and over again until the card takes the settitngs.  I found that using iwconfig wlan0 **ESSID** #name# worked.  I have been using the command line and now need to figure out how to get it to set up every boot.

Thanks for everyones help :)[/QUOTE]
you could just write a script and put your commands in that script, and execute it every time you want to go online with only one command (script's name)... Unfortunately, I don't know much about the scripts... I prefer giving commands one by one everytime to practice :) you could search the forum for script writing maybe?

---

