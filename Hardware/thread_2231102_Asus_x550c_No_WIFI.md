---
title: "Asus x550c No WIFI"
date: 2014-06-22
forum: Hardware
---

### Post by zugzwan6 on 2014-06-22
help please asus x550c came pre installed with w8.installed ubuntu 14.04 and no wifi ever.only ethernet.please help im fairly new to ubuntu(can copy paste though) :D
any suggestions are welocomed.i have followed other threads instructions and to no success.thx in advance to anyone
also i dont mind to reinstall if that would help my problem

---

### Post by Vladlenin5000 on 2014-06-22
@[**[COLOR=#000000]zugzwan6[/COLOR]**]("http://ubuntuforums.org/member.php?u=1930663")

Welcome!

It's generally NOT a good idea to hijack other user's threads but since you already did it, AT LEAST make sure you read previous posts. Thank you.

---

### Post by Frogs Hair on 2014-06-23
Moved to own thread.

---

### Post by varunendra on 2014-06-23
Welcome to the forums zugzwan6!

Did you check/try the things suggested in the thread where you originally made your post?

If not, please follow the link in [post #2]("http://ubuntuforums.org/showpost.php?p=12985072") of that thread, and let us have your report.

If yes (you already checked that link and tried the suggestions there), please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by zugzwan6 on 2014-06-24
davy@davy-jones:~$ lspci -nnk | grep -A2 0280
02:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
    Subsystem: Foxconn International, Inc. Device [105b:e074]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5289] (rev 01)
davy@davy-jones:~$ lsmod | grep -e ath9k -e asus
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi
davy@davy-jones:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
davy@davy-jones:~$

---

### Post by zugzwan6 on 2014-06-24
> **varunendra said:**
> Welcome to the forums zugzwan6!

Did you check/try the things suggested in the thread where you originally made your post?

If not, please follow the link in [post #2]("http://ubuntuforums.org/showpost.php?p=12985072") of that thread, and let us have your report.

If yes (you already checked that link and tried the suggestions there), please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

here is script report,thnx a lot for the help


```
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

davy-jones 3.13.0-29-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5-3337U CPU @ 1.80GHz
Memory : 7871 MB
Uptime : 17:00:02 up 18 min,  2 users,  load average: 0.51, 0.71, 0.66


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
    Subsystem: Foxconn International, Inc. Device [105b:e074]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5289] (rev 01)
--
03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b3f2 Chicony Electronics Co., Ltd 
Bus 001 Device 006: ID 03eb:8a0b Atmel Corp. 
Bus 001 Device 003: ID 0489:e069 Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface               Soft blocked  Hard blocked
0: asus-wlan: Wireless LAN        no            no
1: asus-bluetooth: Bluetooth      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi


module parameters ~~~~~~~~~~~~~~~~~~

asus_nb_wmi   (1): wapf=1
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=======o========o==============o=========o===========o==============o===========
 Interface & ID             | Type  | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=======o========o==============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired | r8169  | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.96
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254
    DNS:             192.168.1.254
----------------------------+-------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search home


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.254 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.585/0.632/0.679/0.047 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.077/0.079/0.082/0.009 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_GB.UTF-8")
country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
asus_nb_wmi.conf  : options asus_nb_wmi wapf=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic.efi.signed root=UUID=9bcde95a-d0b3-4c65-86ea-af4aa54f9d6d ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.830650] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.830957] audit: initializing netlink socket (disabled)
[    1.154828] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.100270] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   13.666336] wmi: Mapper loaded
[   13.887277] asus_wmi: ASUS WMI generic driver loaded
[   13.919830] asus_wmi: Initialization: 0x1
[   13.919881] asus_wmi: BIOS WMI version: 7.9
[   13.919937] asus_wmi: SFUN value: 0x4a0877
[   13.921202] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input14
[   14.011959] asus_wmi: Backlight controlled by ACPI video driver
[   15.871959] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

    ======== Done ========
```

---

### Post by varunendra on 2014-06-25
> **zugzwan6 said:**
> ```
02:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter **[COLOR="#FF0000"][14c3:7630][/COLOR]**
```
Like I mentioned in the PM, this is a relatively new card from Ralink for which they have not yet released a publicly available driver yet, nor have the developers could include support for it in existing open source drivers. In short, it is currently a card with no publicly available driver. See here : [https://wikidevi.com/wiki/USI_unk._model_MT7630E_(HP)](https://wikidevi.com/wiki/USI_unk._model_MT7630E_(HP))

I couldn't spend much time on searching for a solution, but whatever I could find in a quick search suggests that probably you have only two options with this card, at least for now -

**1)** Either buy a cheap USB wifi adapter that is well supported in Linux. Browse the forum (Networking & Wireless section) and take a look at this page for reference : [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

or,

**2)** Install an older version of Ubuntu that uses kernel 3.5 or earlier, then try the solution suggested here : [http://askubuntu.com/a/441447](http://askubuntu.com/a/441447)
I personally don't recommend using such an older kernel, but if it works well for everything, could be an acceptable compromise.

Oh, and of course there is a third option that you asked in your PM - switch back to Windows if wifi is so important for you and buying a new adapter is not an acceptable option.

For a permanent solution, please add yourself to the "Affects Me" list of the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146"), as well as adding your comment there.

---

### Post by cqfd93 on 2014-09-01
Hi,

Check out comment #161 (and if it doesn't work for you, comment #125) of bug #1220146

[https://bugs.launchpad.net/ubuntu/+s...6/comments/161]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/161")
[https://bugs.launchpad.net/ubuntu/+s...6/comments/125]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1220146/comments/125")

Hope this helps

---

