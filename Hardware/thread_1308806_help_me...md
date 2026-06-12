---
title: "help me.."
date: 2009-10-31
forum: Hardware
---

### Post by muhan on 2009-10-31
How do I apply this patch to my wireles driver?
I am totally new to Linux and Ubuntu 9.0.4 but I want to learn more about how to use it. I am running Ubuntu 9.0.4 inside 
VirtualBox on my netbook and I need to apply these two patches to my wireless driver:
[http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch](http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch)
[http://patches.aircrack-ng.org/rtl8187-mac80211-injection-speed-2.6.28-rc6.patch](http://patches.aircrack-ng.org/rtl8187-mac80211-injection-speed-2.6.28-rc6.patch)
to my RTL8187B/RTL8197 USB wireless card. I have had problems with people breaking the wireless security on my home 
network and I want to test the security on my new wireless connection to make sure that it is secure and that the 
attackers can't get back in.
 
There is more information about it at this page:
[http://www.aircrack-ng.org/doku.php?id=mac80211](http://www.aircrack-ng.org/doku.php?id=mac80211)
Can anybody give me any help, tips or suggestions on how to do this?

---

### Post by cariboo on 2009-10-31
What you want to do won't work in Virtualbox, as you are only using a virtual nic. You have to do your check with the native wireless device. To keep people from using your wireless access point set up a strong password. Use a service like [this]("http://www.yellowpipe.com/yis/tools/WPA_key/generator.php") to generate a good password.

---

### Post by muhan on 2009-10-31
Actually, this is not a virtual device driver because this is a USB wireles NIC and I tunneled the USB direct through to VirtualBox, so the VirtualBox Virtual Machine has direct access to the wireless NIC without using any virtualized driver.
 
Can you please explain how I would apply this patch in Ubuntu Linux:
 
[http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch](http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch)
 
I don't know how to apply patches to device drivers in Ubuntu Linux. I am trying to improve my Linux system administrator skills and knowing how to apply a patch to a device driver is an important Linux system administration skill.
 
Thanks again for all your help!

---

### Post by muhan on 2009-10-31
Do you think I could apply patches by running the patch as a "shell script"?
 
Maybe I could copy and paste the text from the patch into a file called "patch.sh"
 
and add this line at the top:
 
#!/bin/bash
 
and then
 
chmod 755 patch.sh
 
and then
 
sudo ./patch.sh
 
Do you think that doing it this way would apply the patch?
 
I am not sure if it would work as I have never applied patch before.

---

### Post by muhan on 2009-10-31
This is what I see from the command line in my Ubuntu:
 
root@a:~# sudo airmon-ng stop wlan0
 
Interface Chipset Driver
wlan0 RTL8187 rtl8187 - [phy0]
(monitor mode disabled)
root@a:~# 
 
[EMAIL="root@a"]root@a[/EMAIL]:~# iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit: 7   RTS thr: off   Fragment thr=2352 B   
          Encryption key: off
          Power Management: off
          Link Quality: 0  Signal level: 0  Noise level: 0
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0
pan0      no wireless extensions.
[EMAIL="root@a"]root@a[/EMAIL]:~#

---

