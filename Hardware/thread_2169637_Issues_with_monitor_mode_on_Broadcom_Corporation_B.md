---
title: "Issues with monitor mode on Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN C"
date: 2013-08-22
forum: Hardware
---

### Post by ravenresource on 2013-08-22
I need just a little help I hope I don't usually post anything I usually just read but, I am having an issue. I am trying to use wifite and it seems to work but it always say's scanning for wireless devices...[+] enabling monitor mode on eth1... done[+] enabling monitor mode on eth1... done[+] enabling monitor mode on eth1... done[+] enabling monitor mode on eth1... done, and it just keeps going I have asked friends and I have tried to ask others who say they are hackers or what ever they seem not to be able to answer my questions.

I have done allot of sudo things as I see in the posts but I never see it work.

 iwconfig show's me this.


lo        no wireless extensions.


eth0      no wireless extensions.


eth1      IEEE 802.11abg  ESSID:"HOME-B118"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:F3:7C:B1:18   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

All the answers to others seem to do nothing for me. I'm using a Dell Inspiron mini 1011.

If some one can tell me what you need to see from my end and how to get it I will comply. I really need help here and getting frustrated, I have btw checked out every book I could find from the library I have poured over hundreds or pages now looking but finding nothing. So it's not cuz I'm not trying I just don't want to mess this up. Oh yeah I followed one person's advice and had to re-install everything once already.

---

### Post by ravenresource on 2013-08-22
I'm hoping to error on the side of to much information so it will go faster.

 sudo airmon-ng start wlan0 1




```
Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID    Name
612    avahi-daemon
616    avahi-daemon
782    NetworkManager
853    wpa_supplicant
6556    dhclient
Process with PID 6556 (dhclient) is running on interface eth1




Interface    Chipset        Driver


eth1        Unknown     wl - [phy0]


black@black-Inspiron-1011:~$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


eth1      IEEE 802.11abg  ESSID:"HOME-B118"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:F3:7C:B1:18   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
black@black-Inspiron-1011:~$ sudo apt-get install madwifi-ng
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package madwifi-ng
black@black-Inspiron-1011:~$ sudo iwconfig wlan1 mode master
[sudo] password for black: 
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; No such device.
black@black-Inspiron-1011:~$ sudo airmon-ng start wlan1




Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID    Name
612    avahi-daemon
616    avahi-daemon
782    NetworkManager
853    wpa_supplicant
6556    dhclient
Process with PID 6556 (dhclient) is running on interface eth1




Interface    Chipset        Driver


eth1        Unknown     wl - [phy0]


black@black-Inspiron-1011:~$ sudo iwconfig wlan1 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; No such device.
black@black-Inspiron-1011:~$ iw list
Wiphy phy0
    Band 1:
        Frequencies:
            * 2412 MHz [1] (27.0 dBm)
            * 2417 MHz [2] (27.0 dBm)
            * 2422 MHz [3] (27.0 dBm)
            * 2427 MHz [4] (27.0 dBm)
            * 2432 MHz [5] (27.0 dBm)
            * 2437 MHz [6] (27.0 dBm)
            * 2442 MHz [7] (27.0 dBm)
            * 2447 MHz [8] (27.0 dBm)
            * 2452 MHz [9] (27.0 dBm)
            * 2457 MHz [10] (27.0 dBm)
            * 2462 MHz [11] (27.0 dBm)
            * 2467 MHz [12] (disabled)
            * 2472 MHz [13] (disabled)
            * 2484 MHz [14] (disabled)
        Bitrates (non-HT):
            * 1.0 Mbps
            * 2.0 Mbps (short preamble supported)
            * 5.5 Mbps (short preamble supported)
            * 11.0 Mbps (short preamble supported)
            * 6.0 Mbps
            * 9.0 Mbps
            * 12.0 Mbps
            * 18.0 Mbps
            * 24.0 Mbps
            * 36.0 Mbps
            * 48.0 Mbps
            * 54.0 Mbps
    Band 2:
        Frequencies:
            * 5160 MHz [32] (disabled)
            * 5170 MHz [34] (disabled)
            * 5180 MHz [36] (17.0 dBm)
            * 5190 MHz [38] (17.0 dBm)
            * 5200 MHz [40] (17.0 dBm)
            * 5210 MHz [42] (17.0 dBm)
            * 5220 MHz [44] (17.0 dBm)
            * 5230 MHz [46] (17.0 dBm)
            * 5240 MHz [48] (17.0 dBm)
            * 5250 MHz [50] (disabled)
            * 5260 MHz [52] (20.0 dBm) (radar detection)
            * 5270 MHz [54] (20.0 dBm) (radar detection)
            * 5280 MHz [56] (20.0 dBm) (radar detection)
            * 5290 MHz [58] (20.0 dBm) (radar detection)
            * 5300 MHz [60] (20.0 dBm) (radar detection)
            * 5310 MHz [62] (20.0 dBm) (radar detection)
            * 5320 MHz [64] (20.0 dBm) (radar detection)
            * 5330 MHz [66] (disabled)
            * 5340 MHz [68] (disabled)
            * 5350 MHz [70] (disabled)
            * 5360 MHz [72] (disabled)
            * 5370 MHz [74] (disabled)
            * 5380 MHz [76] (disabled)
            * 5390 MHz [78] (disabled)
            * 5400 MHz [80] (disabled)
            * 5410 MHz [82] (disabled)
            * 5420 MHz [84] (disabled)
            * 5430 MHz [86] (disabled)
            * 5440 MHz [88] (disabled)
            * 5450 MHz [90] (disabled)
            * 5460 MHz [92] (disabled)
            * 5470 MHz [94] (disabled)
            * 5480 MHz [96] (disabled)
            * 5490 MHz [98] (disabled)
            * 5500 MHz [100] (20.0 dBm) (radar detection)
            * 5510 MHz [102] (20.0 dBm) (radar detection)
            * 5520 MHz [104] (20.0 dBm) (radar detection)
            * 5530 MHz [106] (20.0 dBm) (radar detection)
            * 5540 MHz [108] (20.0 dBm) (radar detection)
            * 5550 MHz [110] (20.0 dBm) (radar detection)
            * 5560 MHz [112] (20.0 dBm) (radar detection)
            * 5570 MHz [114] (20.0 dBm) (radar detection)
            * 5580 MHz [116] (20.0 dBm) (radar detection)
            * 5590 MHz [118] (20.0 dBm) (radar detection)
            * 5600 MHz [120] (disabled)
            * 5610 MHz [122] (disabled)
            * 5620 MHz [124] (disabled)
            * 5630 MHz [126] (disabled)
            * 5640 MHz [128] (disabled)
            * 5650 MHz [130] (disabled)
            * 5660 MHz [132] (20.0 dBm) (radar detection)
            * 5670 MHz [134] (20.0 dBm) (radar detection)
            * 5680 MHz [136] (20.0 dBm) (radar detection)
            * 5690 MHz [138] (20.0 dBm) (radar detection)
            * 5700 MHz [140] (20.0 dBm) (radar detection)
            * 5710 MHz [142] (disabled)
            * 5720 MHz [144] (disabled)
            * 5725 MHz [145] (disabled)
            * 5730 MHz [146] (disabled)
            * 5735 MHz [147] (disabled)
            * 5740 MHz [148] (disabled)
            * 5745 MHz [149] (30.0 dBm)
            * 5750 MHz [150] (30.0 dBm)
            * 5755 MHz [151] (30.0 dBm)
            * 5760 MHz [152] (30.0 dBm)
            * 5765 MHz [153] (30.0 dBm)
            * 5770 MHz [154] (30.0 dBm)
            * 5775 MHz [155] (30.0 dBm)
            * 5780 MHz [156] (30.0 dBm)
            * 5785 MHz [157] (30.0 dBm)
            * 5790 MHz [158] (30.0 dBm)
            * 5795 MHz [159] (30.0 dBm)
            * 5800 MHz [160] (30.0 dBm)
            * 5805 MHz [161] (30.0 dBm)
            * 5810 MHz [162] (30.0 dBm)
            * 5815 MHz [163] (30.0 dBm)
            * 5820 MHz [164] (30.0 dBm)
            * 5825 MHz [165] (30.0 dBm)
            * 5830 MHz [166] (disabled)
            * 5840 MHz [168] (disabled)
            * 5850 MHz [170] (disabled)
            * 5860 MHz [172] (disabled)
            * 5870 MHz [174] (disabled)
            * 5880 MHz [176] (disabled)
            * 5890 MHz [178] (disabled)
            * 5900 MHz [180] (disabled)
            * 5910 MHz [182] (disabled)
            * 5920 MHz [184] (disabled)
            * 5930 MHz [186] (disabled)
            * 5940 MHz [188] (disabled)
            * 5950 MHz [190] (disabled)
            * 5960 MHz [192] (disabled)
            * 5970 MHz [194] (disabled)
            * 5980 MHz [196] (disabled)
            * 5990 MHz [198] (disabled)
            * 6000 MHz [200] (disabled)
            * 6010 MHz [202] (disabled)
            * 6020 MHz [204] (disabled)
            * 6030 MHz [206] (disabled)
            * 6040 MHz [208] (disabled)
            * 6050 MHz [210] (disabled)
            * 6060 MHz [212] (disabled)
            * 6070 MHz [214] (disabled)
            * 6080 MHz [216] (disabled)
            * 6090 MHz [218] (disabled)
            * 6100 MHz [220] (disabled)
            * 6110 MHz [222] (disabled)
            * 6120 MHz [224] (disabled)
            * 6130 MHz [226] (disabled)
            * 6140 MHz [228] (disabled)
        Bitrates (non-HT):
            * 6.0 Mbps
            * 9.0 Mbps
            * 12.0 Mbps
            * 18.0 Mbps
            * 24.0 Mbps
            * 36.0 Mbps
            * 48.0 Mbps
            * 54.0 Mbps
    max # scan SSIDs: 1
    max scan IEs length: 0 bytes
    Coverage class: 0 (up to 0m)
    Supported Ciphers:
        * WEP40 (00-0f-ac:1)
        * WEP104 (00-0f-ac:5)
        * TKIP (00-0f-ac:2)
        * CCMP (00-0f-ac:4)
        * CMAC (00-0f-ac:6)
    Available Antennas: TX 0 RX 0
    Supported interface modes:
         * IBSS
         * managed
    software interface modes (can always be added):
    interface combinations are not supported
    Supported commands:
         * set_interface
         * new_key
         * join_ibss
         * set_pmksa
         * del_pmksa
         * flush_pmksa
         * connect
         * disconnect
black@black-Inspiron-1011:~$ sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; No such device.
black@black-Inspiron-1011:~$ sudo airodump-ng wlan0 --channel 6
Interface wlan0: 
ioctl(SIOCGIFINDEX) failed: No such device
black@black-Inspiron-1011:~$
```

---

### Post by ravenresource on 2013-09-08
So no answer for a first timer huh? Excellent! How wonderful, seem's there are 120 or so people looking for this answer also so It might be a good I deal to answer the question? I don't know.

If I need to put more info or more useful info please advise.

---

### Post by Frogs Hair on 2013-09-08
Ubuntu Forums is a volunteer organization and apparently none of those who viewed the thread had a suggestion or solution. It has been my experience that when a forum member  has an answer or suggestion those members are and have been more than eager to share it. You may bump your thread  every 24 hours as needed, but there is no paid technical support here .

---

### Post by ravenresource on 2013-09-11
I realize that. I had thought maybe I was not giving the correct information. As I said I have no idea what could help. is there a program that will give me information I might use to check myself? In some circles there are preferred data people like to see if going to help... As I sit and read I find there are some things not to hard but then you get peoples preference involved you might ask all day and never say the right phrase to get the answer.

I'm a Seeker of information and only ask if I am providing useless information. Why ask if I didn't think about it first? I figure people just thought I was saying something else like I expected some paid support from a free world I enjoy very much and support with all my effort.

---

### Post by ravenresource on 2013-10-02
lol, I'm starting to see why Ubuntu and free OS's are not doing well.

---

