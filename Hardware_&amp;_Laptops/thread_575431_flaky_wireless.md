---
title: "flaky wireless"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by midnightToker on 2007-10-14
I have a Thinkpad T61 running Gutsy - fully updated (2.6.22-14-generic kernel).  I've had a consistent problem with my wireless connection that is getting really annoying.  Sometimes it just stops working.  When I first boot it always works perfectly - it connects automatically to my access point using WPA and I can get online.  But after a random interval (can be as little as 15 min or as long as 3-4 hours) it just stops working.  Usually network manager shows 0 bars for signal strenth, and if I hover over the icon it will say it is connected to my network with 0% signal strength.  Where it normally shows the 6 or 7 other networks near me though, when it is not working I see only the one I am "connected" to.

When this happens, I can usually manually rmmod iwl4965, then modprobe it, then iwconfig wlan0 essid any, and then use network manager to reconnect.  This does not always work though - sometimes after removing and reinserting the iwl4965 module network manager simply states that no networking devices have been detected and I have to reboot.

I just downloaded the latest snapshot of the iwl4965 driver (1.1.17) and successfully installed it (got no errors, at least) and it works just fine but has the same flakiness.  

I'm not sure it is a problem with the driver, because I noticed these strange entries in my dmesg:

[ 7107.556000] wlan0: Initial auth_alg=0
[ 7107.556000] wlan0: authenticate with AP 00:11:50:f2:4b:06
[ 7107.556000] wlan0: RX authentication from 00:11:50:f2:4b:06 (alg=0 transaction=2 status=0)
[ 7107.556000] wlan0: authenticated
[ 7107.556000] wlan0: associate with AP 00:11:50:f2:4b:06
[ 7107.560000] wlan0: authentication frame received from 00:11:50:f2:4b:06, but not in authenticate state - ignored
[ 7107.560000] wlan0: RX ReassocResp from 00:11:50:f2:4b:06 (capab=0x411 status=0 aid=3)
[ 7107.560000] wlan0: associated
[ 7107.560000] wlan0: CTS protection enabled (BSSID=00:11:50:f2:4b:06)
[ 7125.876000] wlan0: no IPv6 routers present
[ 8805.348000] wlan0: RX deauthentication from 00:11:50:f2:4b:06 (reason=4)
[ 8805.348000] wlan0: deauthenticated
[ 8805.852000] wlan0: RX WEP frame with unknown keyidx 1 (A1=01:80:c2:00:00:00 A2=00:11:50:f2:4b:06 A3=00:14:a5:81:88:5c)
[ 8806.348000] wlan0: authenticate with AP 00:11:50:f2:4b:06
[ 8806.348000] wlan0: RX authentication from 00:11:50:f2:4b:06 (alg=0 transaction=2 status=0)
[ 8806.348000] wlan0: authenticated
[ 8806.348000] wlan0: associate with AP 00:11:50:f2:4b:06
[ 8806.352000] wlan0: RX ReassocResp from 00:11:50:f2:4b:06 (capab=0x411 status=0 aid=3)
[ 8806.352000] wlan0: associated
[ 8806.352000] wlan0: CTS protection enabled (BSSID=00:11:50:f2:4b:06)
[ 8806.356000] iwl4965: TX Power requested while scanning!
[ 8806.356000] iwl4965: Error setting Tx power (-11).
[ 8806.356000] iwl4965: TX Power requested while scanning!
[ 8806.356000] iwl4965: Error setting Tx power (-11).
[ 8807.900000] wlan0: RX WEP frame with unknown keyidx 1 (A1=01:80:c2:00:00:00 A2=00:11:50:f2:4b:06 A3=00:14:a5:81:88:5c)
[ 8808.808000] wlan0: RX deauthentication from 00:11:50:f2:4b:06 (reason=15)
[ 8808.808000] wlan0: deauthenticated
[ 8809.808000] wlan0: authenticate with AP 00:11:50:f2:4b:06
[ 8809.848000] wlan0: RX WEP frame with unknown keyidx 1 (A1=01:80:c2:00:00:00 A2=00:11:50:f2:4b:06 A3=00:14:a5:81:88:5c)
[ 8810.008000] wlan0: authenticate with AP 00:11:50:f2:4b:06
[ 8810.208000] wlan0: authenticate with AP 00:11:50:f2:4b:06
[ 8810.408000] wlan0: authentication with AP 00:11:50:f2:4b:06 timed out
[ 8816.924000] iwl4965: Microcode SW error detected.  Restarting 0x2000000.
[ 8827.608000] ADDRCONF(NETDEV_UP): wlan0: link is not ready


Sometimes I see lots and lots of that one line about "RX WEP frame with unknown keyidx" repeated.  

I've tried to research the problem, but none of my searches have yielded anything useful.  I seem to remember seeing something a while back about killing wpa_supplicant after the connection was established, but now I can't find any reference to that.  

Any ideas?

---

### Post by superbrose on 2007-10-27
Unfortunately I have the same problem. :(

Some more googling revealed a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/149214") in linux-ubuntu-modules-2.6.22.

This problem occurs on my Sony Vaio VGN-FZ240E, which has an integrated Intel wireless card that should work with the iwl4965 kernel module. I am using WPA-PSK TKIP encryption (wpa_supplicant in roaming mode). The wireless connection always works fine after a fresh reboot and eventually dies after an unpredictable interval.

```
$ dmesg
[19.868000] wlan0: authenticate with AP 00:a7:23:51:00:d9
[19.968000] wlan0: RX authentication from 00:a7:23:51:00:d9 (alg=0 transaction=2 status=0)
[19.872000] wlan0: authenticated
...
[8614.108000] wlan0: No ProbeResp from current AP 00:a7:23:51:00:d9 - assume out of range
[8616.088000] wlan0: No STA entry for own AP 00:a7:23:51:00:d9
...
[8626.056000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[8630.696000] wlan0: RX deauthentication from 00:a7:23:51:00:d9 (reason=1)
[8630.696000] wlan0: deauthenticated
...
[8636.788000] wlan0: RX deauthentication from 00:a7:23:51:00:d9 (reason=7)
...
[12345.388000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

I hope that there will be a fix soon, as this bug is highly annoying.

---

### Post by saitoh on 2007-10-27
I recently fixed a friends computer that was having the same issues. However he had a Broadcom which have pretty bad support in Linux. Anyways I used ndiswrapper and installed the windows driver, ever since he has had no problems. You guys might want to consider using the windows drivers until they manage to fix the bug.

---

### Post by skamithi on 2007-11-10
I had the same problem on my new t61p when authenticating to my 802.11g AP with WPA2-Personal setup. I have gentoo and run iwlwifi 1.1.21 and iwl4965-ucode 4.44.1.18, but thought this might still be helpful.

fix for me is to enable the hwcrypto option in the iwl4965 modules.conf config.

options iwl4965 hwcrypto=1

---

### Post by damko on 2007-12-27
I have the same problem on a thinkpad T61 type 7664-18G

it seems to be solved.
have a look at [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149214](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149214)

I tried this tgz [http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-4.44.1.20.tgz](http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-4.44.1.20.tgz) 
and I installed it 3 minutes ago following the istructions in the readme file included (note it's  different from what wrote Anton in his post [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149214/comments/24](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149214/comments/24)

I'm waiting to see if it works

Dam

---

### Post by damko on 2007-12-27
it seems to work for now. It never stopped since the firmware upgrade

Dam

---

### Post by deniswal on 2008-01-22
Nope it doesn't work for me...

xxx.ucode was put at the right place since it ls marked as missing if not there.

This doesn't solve this bug for me.

ASUS laptop.

Thanks for suggesting anyway.

Denis

---

### Post by deniswal on 2008-02-24
I went to kernel version 2.6.24-rc8, hoping to get a fix for iwl4965 brought along with it. It is much better but on heavy loads it still breaks.
I am using the laptop to backup a Windows machine using backuppc and the backup can never complete. The wireless connection breaks with:
Feb 24 11:43:25 denis-laptop kernel: [48983.700183] iwl4965: Microcode SW error detected.  Restarting 0x2000000.
Feb 24 11:43:29 denis-laptop kernel: [48987.271291] iwl4965: Can't stop Rx DMA.

There is a way to avoid the reboot using the following script though:
#!/usr/bin/env bash
gksudo rmmod iwl4965
gksudo modprobe iwl4965

Denis

---

