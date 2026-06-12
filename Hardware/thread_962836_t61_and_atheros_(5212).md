---
title: "t61 and atheros (5212)"
date: 2008-10-29
forum: Hardware
---

### Post by abnewbie on 2008-10-29
Hi,

I am running Ubuntu 8.04 on an IBM T61 laptop. In it, I have a wireless card (Atheros 5212). When I run NetworkManager I can see all the available wireless networks. However when I try to connect to one - Ubuntu hangs for a few seconds and then says there is no network connection. If I try to connect to a network with WPA encryption, I get a prompt for my password, but then again the network doesn't connect. Does anyone have any suggestion as to where else I can look?

Thanks

---

### Post by fendres on 2008-10-30
I couldn't get wireless to work on my T60 (also with some kind of atheros 5xxx) with NetworkManager. I solved it by removing NetworkManager from the startup process (I deleted the link in /etc/rc2.d/SxxNetworkManager) and wrote a script that starts wpa_supplicant (and restarts it once in a while, if it does not connect) and dhclient. Also I had to install the windows driver using ndiswrapper. However this is by no means an elegant solution and sometimes it takes forever to connect, so I will try to find a better solution in the next week. Maybe drop me a personal message in a while.

Meanwhile this tutorial has a lot of useful information:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

Update:
My solution is a little strange, but right now it works ok. I have a WPA encrypted network, therefore wpa_supplicant is needed. But it didn't work out of the box, so I figured out the following:
What is the output of the command:"ps ax|grep wpa_supplicant|grep -v grep"
If there is a line showing a some numbers and a command, try to kill that command ("sudo killall wpa_supplicant").
Then try the following:
sudo wpa_supplicant -d -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -D wext
This requires however, that you have a valid config file at /etc/wpa_supplicant/wpa_supplicant.conf
In case you wonder about it, -D wext is for the wext driver, not for ndiswrapper. I do not know why this works, but otherwise it doesn't.

There is a man page for wpa_supplicant.conf (in Konqueror navigate to #wpa_supplicant.conf including the #) with good examples in case you need help.
The command will output a lot of garbage (which I do not understand either) but for me this is connecting faster than normal operation mode.
When the output stops, start a new shell (or press ctrl-Z) and type: 
sudo wpa_cli status
to verify that the encrypted connection works. Output should be like:
Selected interface 'wlan0'
bssid=XX:XX:XX:XX:XX:XX
ssid=XXXXXX
id=3
pairwise_cipher=TKIP
group_cipher=TKIP
key_mgmt=WPA-PSK
wpa_state=COMPLETED
ip_address=192.168.XXX.XX

If so or similar type:
sudo dhclient wlan0
to use the connection to get an IP address (only necessary if you use a dhcp server which is included in most wireless routers).
Then it hopefully works fine. Tell me whether this works for you and I can tell you how to set wireless up during boot process.

---

### Post by abnewbie on 2008-11-04
Hi again.

I tried but still no luck. I got ndswrapper using the package manager and the atheros driver from windows (inf file) The ndiswrapper gui shows the driver and says "Hardware Present: Yes"

Then I went to a terminal and typed sudo ps -ef | grep Network and killed all the jobIDs I could find. Finally I typed:

sudo  wpa_supplicant -d -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -D wext 

I unlocked my wireless network and made it open and set my wpa_supplicant.conf to:

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        key_mgmt=NONE
}


This is the results I got at the prompt with the spa_supplicant call:

Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
Priority group 0
   id=0 ssid=''
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
WEXT: Operstate: linkmode=1, operstate=5
ioctl[SIOCGIFINDEX]: No such device
Failed to add interface wlan0
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: No such device
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: No such device
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: No such device
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: No such device
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
WEXT: SIOCSIWAUTH(param 7 value 0x0) failed: No such device)
Failed to disable WPA in the driver.
wpa_driver_wext_set_drop_unencrypted
WEXT: SIOCSIWAUTH(param 5 value 0x0) failed: No such device)
wpa_driver_wext_set_countermeasures
WEXT: SIOCSIWAUTH(param 4 value 0x0) failed: No such device)
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
ioctl[SIOCSIWAP]: No such device
WEXT: Operstate: linkmode=0, operstate=6
ioctl[SIOCGIFFLAGS]: No such device

thanks

---

### Post by fendres on 2008-11-05
Hi, please check if you have other wpa_supplicant processes running. To kill NetworkManager is good, because it might respawn killed wpa_supplicants, but you also need to kill those which are already running.

If that is not the solution, I do not know what the problem is. Perhaps a driver issue? Otherwise you could give encryption a try with these setttings from my wpa_supplicant.conf:

ctrl_interface=/var/run/wpa_supplicant

network={
ssid="<yournetworkname>"
scan_ssid=1
proto=WPA
key_mgmt=WPA-PSK
pairwise=TKIP
group=TKIP
psk="<yourpassphrase>"
}

Good luck,
Felix

---

