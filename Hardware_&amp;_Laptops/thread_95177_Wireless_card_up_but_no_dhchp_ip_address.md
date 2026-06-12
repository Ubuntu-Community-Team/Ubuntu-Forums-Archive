---
title: "Wireless card up but no dhchp ip address"
date: 2005-11-25
forum: Hardware &amp; Laptops
---

### Post by bruce147 on 2005-11-25
Here are some config files. What is my problem???
eth0      IEEE 802.11b  ESSID:"Suki"  Nickname:"ipw2100" ##this is correct
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:50:F2:C8:1B:44
          Bit Rate=11 Mb/s   Tx-Power:off ##frequency and bit rate are correct
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-49 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

bruce@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:04:23:5F:EE:11
          inet6 addr: fe80::204:23ff:fe5f:ee11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:24 dropped:24 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2016 (1.9 KiB)
          Interrupt:10 Base address:0xe000 Memory:e0200000-e0200fff

I can only get internet connection by ethernet card. If I umplug from the network my machine takes forever to boot and then has no internet connection !!!

eth1      Link encap:Ethernet  HWaddr 00:40:CA:C3:AC:D4
          inet addr:192.168.2.28  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fec3:acd4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2603 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2612 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2322178 (2.2 MiB)  TX bytes:378927 (370.0 KiB)
          Interrupt:10 Base address:0x2000

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1

---

### Post by Florian Hufsky on 2005-11-26
What encryption does your access point use?
Out-of-the-box ubuntu only supports WEP.
WPA must be added manually (in an insane painful process - console).

See [https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

---

### Post by bruce147 on 2005-11-26
You were right about it being the WEP key. I had entered that into the GUI listed under System/Administration/Networking. I did that early on in efforts. I don't know if it stuck over several days of effort to get the wireless up. 
In the end, I downloaded gtkwifi and installed it. It immediately detected the network and asked for my WEP key. And then I was connected!

But now I have another annoying problem. When booting up, Ubuntu stalls, while waiting for network connections. It actually breaks out of the splash screen and goes to text only for several minutes. Then it says something like network setup failed and continues a text screen bootup until it opens the login screen.

Any ideas?

---

### Post by Florian Hufsky on 2005-11-26
i have this problem too. it's teh suck!

i was unable to get rid of it yet.

and even if wlan is on and lan plugged out it will wait until BOTH got their adresses asigned (and the default lan dhcp timeout seems to be something like 30-40 seconds) - yaiks!

i posetd it under [http://ubuntuforums.org/showthread.php?t=95272](http://ubuntuforums.org/showthread.php?t=95272) , but got no reply so far.

---

### Post by bruce147 on 2005-11-26
Florian, I found this thread [http://ubuntuforums.org/showthread.php?t=77380](http://ubuntuforums.org/showthread.php?t=77380)

I took this from post #5. The others in the thread may have found some other solutions. I have not had the time to carefully read and try these suggestions yet, but I will, and post the results

Quote:
One tip for the long boot times though is to lower your DHCP timeout. This is normally the reason for long boot times when not connected to a network. On my laptop I have edited the file '/etc/dhcp3/dhclient.conf' and uncommented the line '#timeout 60;' (removed the #) and changed the value to 10. This lowers the pause on boot to ten seconds instead of a minute. You may find that you can use a lower value than ten seconds, however it will depend on how quickly your DHCP server responds to requests. NOTE: I did this in Hoary, but I assume it will also work in Breezy. Try it at your own risk! :)

---

### Post by Florian Hufsky on 2005-11-26
thanks.

overall i'm shocked by ubuntu boot times. 53 seconds to login and 23 seconds till gnome is up.

windows is 25seconds to login and 6 for the gui to show up.

---

### Post by bruce147 on 2005-11-26
I tried the fix of changing the DHCP time out to 10 and removing the #. A major improvement, but still a little slow. When I had only the ethernet connection configued, my boot time was faster than it is now, even after making this fix.

I don't know if that is the best fix. Maybe this will bite me somewhere else!

Before I had this problem, I would say Ubuntu and Windows XP boot up at about the same speed on my laptop. So I am happy with Ubuntu. Your window boot speed is impressive!

---

### Post by Florian Hufsky on 2005-11-26
It's even more impressive when i hibernate to the disk. Windows is up and running in about 10-15 seconds. (I have 1024GB DDR ram and a clean windows install with most service disabled so i need ~150mb usually. maybe that has to do with it ;) )

Ubuntu hibernate to disk... boot = crash :(

---

### Post by bruce147 on 2005-11-26
I suspected you had a new or clean install of windows. If you keep using it, it will slow down. 
I discovered the hibernate,  boot, crash trick a few hours ago. 

I

---

