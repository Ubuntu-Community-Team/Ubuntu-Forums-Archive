---
title: "atheros chipset problems with monitor mode problem"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by adub on 2007-01-06
ok im lost to wits end i have installed patches and downloaded different versions and to no avail no luck

iwconfig mode monitor 

Error : unrecognised wireless request "monitor"

wlanconfig ath0 create wlandev wifi0 wlanmode monitor ath0
wlanconfig: unknown create option ath0


the list goes on please someone help me show me the way on this
oh btw the card is a ubquiti 300 mW 802.11g/b/a

thanks to all who reply

---

### Post by tturrisi on 2007-01-06
[http://madwifi.org/wiki/UserDocs/MonitorMode](http://madwifi.org/wiki/UserDocs/MonitorMode)
[http://madwifi.org/wiki/UserDocs/MonitorModeInterface](http://madwifi.org/wiki/UserDocs/MonitorModeInterface)

---

### Post by adub on 2007-01-07
i issue the commands for the old driver and the new driver still nothing same results

Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.

well i installed new driver and my next line of output for the new command is

ath0

but when i try to run airodump and sniff packets i get

ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead.  Make sure RFMON is enabled:
run 'ifconfig ath0 up; iwconfig ath0 mode Monitor channel <#>'

also iwpriv shows no monitor mode in listing 

i dont know if the new command is throwing me in monitor mode or not

odd thing is kismet works fine so i know im monitoring maybe im doing something wrong in airodump

# airodump ath0 0

other mixtures of commands as well even tried airodump-ng

---

### Post by clocker on 2007-02-08
i have a similiar problem and i am using a dlink wna atheros based card.  is their a solution?

---

### Post by shredswithpiks on 2007-02-11
I'm having the same issue with a D-Link atheros wireless card... kismet works fine, but I can't get the card into monitor mode in order to work with airodump.

I've read that the command

wlanconfig ath1 create wlandev wifi0 wlanmode monitor

should create an ath1 reference to the wireless card and put it into monitor mode... however, I get a "command not found" error when I try to run wlanconfig.

any solutions?

---

### Post by OnkiDonki on 2007-02-20
Hi,
in 6.10 only the madwifi driver is included. You must install
a packet I think it's called Wireless-tools to use that "wlanconfig".
You can download that packet from debian!!!!!!
In my case I can use now that "wlanconfig" but I have the same 
problem that I cannot switch to monitor mode!!!!!

---

### Post by lswim on 2007-05-25
wlanconfig is part of the madwifi-tools package and to use it to put your card into monitor mode do :

 remove existing interface with
[COLOR="Red"]wlanconfig ath0 destroy[/COLOR]

make a new one (monitor mode)
[COLOR="Red"]wlanconfig ath0 create wlandev wifi0 wlanmode monitor[/COLOR]

If you do iwconfig now you should see something similar to 

ath1   IEEE 802.11g  ESSID:""
          Mode:Monitor  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=0/3
          Retry: off   RTS thr: off   Fragment thr: off
          Encryption key: off
          Power Management: off
          Link Quality=16/94  Signal level=-77 dBm  Noise level=-93 dBm
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag:  0
          Tx excessive retries: 0  Invalid misc: 0   Missed beaco: 0

hope that helps :)

---

