---
title: "My DWL-G650 wireless network card doesn't work"
date: 2004-11-11
forum: Hardware &amp; Laptops
---

### Post by darkell on 2004-11-11
I have recently installed ubuntu linux but am having a lot of problems getting my wireless network working.

When I look for the card using the lspci command it doesn't show up and in this page [http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards/view?searchterm=dwl-g650](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards/view?searchterm=dwl-g650)
the comment says "Does not work for me unless I recompile the pci_acx module with latest patches. After that it works. WEP not yet supported for acx111 cards".

I would like to do this but I don't know how can someone help me please?

---

### Post by metasyntax on 2004-11-11
I have a dwl-g520 working (It should use the same driver) with no recompiles.

here are the drivers that I have loaded:

$ lsmod | grep ath
ath_pci                56036  0
wlan                  118748  3 wlan_wep,ath_pci
ath_hal               129488  2 ath_pci

if that works, see if the device is there:
$ iwconfig
...
ath0      IEEE 802.11g  ESSID:"xxx"
          Mode:Managed  Frequency:2.462GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54Mb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry: off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=17/94  Signal level=-78 dBm  Noise level=-95 dBm
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries:12865  Invalid misc:12865   Missed beacon:55
...

if you get this far, I'll tell you haw I set up WEP... not sure the "proper" way in ubuntu, I just did it the same as debian.

HTH,
meta

---

### Post by Starwoid on 2004-11-13
I second the post above, my G650 worked out of the box okay (although I had to install wpa for 'g' network support). 

Not sure why it doesn't work for you though, sorry.

---

### Post by Razvan on 2004-11-13
[QUOTE=Starwoid]I second the post above, my G650 worked out of the box okay (although I had to install wpa for 'g' network support). 

Not sure why it doesn't work for you though, sorry.[/QUOTE]
 the difference between you people is, that Starwoid seems to have a rev a1 card with prism chipset and you other guys a rev b1 with the atheros chipset :-)

i have a atheros too and its not running yet, but i havent spent any effort yet...besides noticing that its not working outta the box

cheers

---

### Post by Starwoid on 2004-11-13
Oh I have to disagree... :wink:

I have a revision B card, well I think I do, it has HW B2 written on the card anyway.

If I run lsmod I can also see things like: ath_pci, ath_hal, etc

Unless I'm mistaken, madwifi only supports atheros chipsets? Well I used to run gentoo a while back on my current setup, and had my wireless working nicely by hand-running madwifi and wpa_supplicant. However ubuntu worked out of the box, apart from, as I mentioned before, the wpa issue.

---

### Post by egon on 2004-12-28
[QUOTE=Starwoid]Oh I have to disagree... :wink:

I have a revision B card, well I think I do, it has HW B2 written on the card anyway.

If I run lsmod I can also see things like: ath_pci, ath_hal, etc

Unless I'm mistaken, madwifi only supports atheros chipsets? Well I used to run gentoo a while back on my current setup, and had my wireless working nicely by hand-running madwifi and wpa_supplicant. However ubuntu worked out of the box, apart from, as I mentioned before, the wpa issue.[/QUOTE]
 Sorry - what is wpa?

---

