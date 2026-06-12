---
title: "Acer Travelmate 2200LCi, wireless doesn't work, please help"
date: 2005-03-27
forum: Hardware &amp; Laptops
---

### Post by dalmeida on 2005-03-27
Hi evryone, I just installed Ubuntu on my laptop, I have also tried other distros (Slackware, RedHat) with no luck. I've followed the HowTos found on the forum along with many of the other posts and I'm stuck. My laptop has the intel ipw2200 card. I've tried to use ipw2200, foolowed all the instructions and my card isn't detected. I then used ndiswrapper and he card is seen but I can't set the SSID. I've followed all howtos I could find, I've been working on this for the past 5 days now with no luck, please, anyone, help. Here is the output of iwconfig:

root@mobilepenguin:~ # iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437GHz  Access Point: 00:00:00:00:00:00  
          Bit Rate:1Mb/s   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:DA11-0619-74   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:56/154  Noise level:0/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by dalmeida on 2005-03-27
After entering the commands below, this is what I get (notice the SSID never changed):

root@mobilepenguin:~ # iwconfig wlan0 mode Managed
root@mobilepenguin:~ # iwconfig wlan0 nickname "penguinbase"
root@mobilepenguin:~ # iwconfig wlan0 key restricted MYSECRETKEY
root@mobilepenguin:~ # iwconfig wlan0 essid penguinbase
root@mobilepenguin:~ # ifconfig wlan0 192.168.69.66 broadcast 192.168.69.255 net
mask 255.255.255.0
root@mobilepenguin:~ # ifconfig wlan0 up
root@mobilepenguin:~ # route add default gw 192.168.69.1
SIOCADDRT: File exists
root@mobilepenguin:~ # iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  Nickname:"penguinbase"
          Mode:Managed  Frequency:2.437GHz  Access Point: 00:00:00:00:00:00  
          Bit Rate=1Mb/s   
          RTS thr=2347 B   Fragment thr=2346 B   
          Encryption key:DA11-0619-74   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:56/154  Noise level:0/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by dalmeida on 2005-04-07
Is there anyone in this forum able to help me out? I've been working oon this issue for almost 4 weeks now and nothing. I've tried ndiswrapper and also the ipw2200 drivers, no luck. When I sue the ipw2200 my hardware isn't detected at all and when I use ndiswrapper I can't set the ESSID. Anyone ???? :confused:  :sad:

---

### Post by dalmeida on 2005-12-29
Finally, got it to work, this is what I did:

apt-get install ndiswrapper-utils
wget [ftp://ftp.support.acer-euro.com/notebook/TravelMate_2200_2700/driver/80211bg.zip](ftp://ftp.support.acer-euro.com/notebook/TravelMate_2200_2700/driver/80211bg.zip)
unzip 80211bg.zip
cp -r 80211bg /opt/
ndiswrapper -i /opt/80211bg/Winxp/neti2220.inf
(Ignore error msg "ls: /etc/ndiswrapper: No such file or directory")
ndiswrapper -m
modprobe ndiswrapper
iwconfig wlan0 key restricted 1234567890
iwconfig wlan0 essid youressid
ifconfig wlan0 192.168.69.69 netmask 255.255.255.0 up
route add default gw 192.168.69.2

---

