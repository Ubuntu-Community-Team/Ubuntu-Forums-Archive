---
title: "wireless internet suddenly doesn't work"
date: 2010-01-01
forum: Hardware
---

### Post by cailamaia on 2010-01-01
Hi everyone, I have a question for y'all.

This morning, my wireless internet connection decided not to work. I have no idea why, as it was working fine yesterday evening. The wired connection is fine, and is how I am able to post this.

I just tried following [this excellent guide (linked here)]("http://ubuntuforums.org/showthread.php?t=571188"), but it didn't work for some reason. Here is the log of my terminal output:


```

selma@Horation:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  Mode:Managed  Frequency:2.437 GHz  
          Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

selma@Horation:~$ sudo ifconfig wlan0 down
selma@Horation:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:16:ea:c3:52:28
Sending on   LPF/wlan0/00:16:ea:c3:52:28
Sending on   Socket/fallback
selma@Horation:~$ sudo ifconfig wlan0 up
selma@Horation:~$ sudo iwconfig wlan0 essid “gruetzi”
selma@Horation:~$ sudo iwconfig wlan0 key 8FD11DE0D267F9D3280046A674
selma@Horation:~$ sudo iwconfig wlan0 key restricted
selma@Horation:~$ sudo iwconfig wlan0 mode Managed
selma@Horation:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:16:ea:c3:52:28
Sending on   LPF/wlan0/00:16:ea:c3:52:28
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.


```

As you can see, it didn't give me any errors, but I cannot connect despite that.

---

### Post by seedreaper on 2010-01-01
not positive but try unpluging the router for five minutes they some times need to be reset.

---

### Post by cailamaia on 2010-01-01
Hmm. I don't think that's the problem. The rest of the fam (on windows boxes) can connect just fine. It's mine that's being stubborn.

---

### Post by IcarusR on 2010-01-02
Rebooting router can do no harm. Others have had same problem & this has resolved issue.

---

