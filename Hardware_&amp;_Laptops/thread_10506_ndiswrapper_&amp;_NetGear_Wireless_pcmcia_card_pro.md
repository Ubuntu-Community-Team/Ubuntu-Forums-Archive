---
title: "ndiswrapper &amp; NetGear Wireless pcmcia card problem"
date: 2005-01-08
forum: Hardware &amp; Laptops
---

### Post by macintof on 2005-01-08
I currently have a laptop with ubuntu 2.6.8.1-4-386.
I install ndiswrapper to use windows drivers ndiswrapper seems to be well installed when i modprobe ndiswrapper it returns that in /var/log/messages
Jan  8 18:54:16 localhost kernel: ndiswrapper version 0.10 loaded (preempt=yes,smp=no)
Jan  8 18:54:16 localhost kernel: ndiswrapper: driver wg511icb.sys (NETGEAR,04/06/2004, 2.1.22.0) added

it seems okay, but he should also show me the device and his mac address 

root@Yuna:~ # iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      NOT READY!  ESSID:"NetGear"  
          Mode:Managed  Channel:6  Access Point: 00:00:00:00:00:00  
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B   
          Encryption key: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I try to configure eth1 with dhcp or ifconfig or the app in gnome but none of this method seems to work.
After every manipulation on eth1 i see this in /var/log/messages
Jan  9 00:24:08 localhost kernel: eth1: timeout waiting for mgmt response
Jan  9 00:24:12 localhost last message repeated 3 times
Jan  9 00:24:12 localhost kernel: eth1: mgmt tx queue is still full
Jan  9 00:24:28 localhost last message repeated 55 times
etc .... 

I allready tryed to use WINXP, WIN2K and WIN9x drivers it didn't change everything
I've also done every manipulation with eth0 unplugged

I really don't understand if someone has any idea  :confused: 
thanks !

---

### Post by Krash1201 on 2005-01-09
have you tried the new version of ndis wrapper?  i am in the process of trying that with my mini pci, but have no time to finish and test it.  just a thought.

---

### Post by rupe on 2005-01-14
I've just switched to Ubuntu and I'm using (i think) the same network card. I've got a netgear WG511 and it works fine. I **didn't install ndiswrapper** or anything at all. I did have a few problems getting it going, but when I turned the comp on again the next day it was working... 

Sorry I can't remember exactly what i did... definitely found this useful: [http://www.ubuntulinux.org/wiki/WiFiHowto](http://www.ubuntulinux.org/wiki/WiFiHowto)

Also, I remember it worked easily when I turned off WEP on my access point, but failed with it on. Watching tail -f /var/log/syslog while it tried to connect showed some problem with DHCP. The solution was to assign my laptop a static IP address. Bit of a fudge i know, but I'm happy now!

Hope that helps a bit!

---

### Post by littlepaul on 2005-02-03
in the german forum there was a similar thread.
There is an workarround by using /etc/hotplug/blacklist for this issue.
[http://www.ubuntuusers.de/viewtopic.php?t=1722](http://www.ubuntuusers.de/viewtopic.php?t=1722)

---

### Post by mrguytx on 2005-06-29
I had the same 'no wireless extensions' problem.

The fix was to uninstall ndiswrapper, download version 1.2 of ndiswrapper and reinstall it with the W2k drivers for the WG511.

I still have one issue, even though it works, if I leave it plugged in when I boot up the system hangs at hotplug section.
Can't figure that one out.

---

