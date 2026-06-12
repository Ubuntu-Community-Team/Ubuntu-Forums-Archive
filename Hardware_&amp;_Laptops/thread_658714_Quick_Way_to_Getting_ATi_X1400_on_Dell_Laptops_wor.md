---
title: "Quick Way to Getting ATi X1400 on Dell Laptops working"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by UnresponsiveBeeVictim on 2008-01-04
1. Download the Alternate version of Gutsy Gibbons
2. Install and Reboot
3. The boot will error out when X tries to load.  Press control-alt-F1, this will bring you to a console
4. Login to your user account

5. Your laptop's wifi will be auto detected, find your network essid
```
sudo iwlist eth0 scanning
```
You should see something like
```
mars@universe:~$ sudo iwlist eth0 scanning
eth0      Scan completed :
          Cell 01 - Address: 00:18:39:4A:3D:65
                    **ESSID:"linksys"**
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=76/100  Signal level=-58 dBm  Noise level=-58 dBm
                    Extra: Last beacon: 40ms ago

```

6. Connect to your network
```
sudo iwconfig essid networknamehere
```
You should now have your wireless listed if you do
```
ifconfig
```
Something like this will appear.
```
mars@universe:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:02:B1:87:9A  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:feb1:879a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3465 errors:9 dropped:497 overruns:0 frame:0
          TX packets:3178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3391702 (3.2 MB)  TX bytes:417618 (407.8 KB)
          Interrupt:17 Base address:0xc000 Memory:dfcff000-dfcfffff 
```

7. Get your internet working
```
sudo dhclient eth0
```

8. Test your internet by pinging something
```
ping google.com
```
Hopefully you'll get a reply... if so we can continue.

9. You'll want to update your repositories and upgrade all of your applications at this point... I personally skipped this and did it when I had time.
```
sudo apt-get update
sudo apt-get dist-upgrade
```

10. Time to download/install the ATi driver
```
sudo apt-get install xorg-driver-fglrx
```

11. Make sure all the modules are there.
```
 depmod -a
```
There should be no errors returned.

12. Configure X to use the ATi driver.
```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```

13. Reboot, you'll be thrown in to X if everything here was completed successfully.


I typed this quick guide up after seeing how confusing it was to do this for your Ubuntu newbie.  Hopefully it helps someone.

Keywords: ATi x1400 mobility radeon fglrx dell inspiron e1705 1705 e1505 1505 e1605 1605 laptop

---

