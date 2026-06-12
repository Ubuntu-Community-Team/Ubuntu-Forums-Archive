---
title: "Neatgear V300 and Ubuntu"
date: 2007-08-31
forum: Hardware &amp; Laptops
---

### Post by lonoy on 2007-08-31
Hi,

I have just purchased a Netcomm V300 VOIP Telephone Adaptor which I have connected to a DLink DSL-502T modem. My problem is that I can get the VOIP working fine but I loose all Internet access once the V300 is connected to the modem.

The technician I talked to over the phone was not familar with Ubuntu and said I needed to create a static IP address so he could check if the Adaptor was working okay or not as my modem works fine with my current adaptor. 

I have checked this page for advice: 

[http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/) 

but I am still rather confused as to what I should do as my original VOIP adapter worked fine without any need to carry out the above. 

I have noted that when my original VOIP adaptor was connected to the modem Ubuntu Network Settings/DNS would see 10.1.1.1 which was what it should be. When I connected the V300 it would change to 192.168.0.1 which was somehow connected to the modem but would only allow limited Internet access. eg I can only go to Google or Yahoo but no further.

Any advice would be appreciated thanks.

---

### Post by bapoumba on 2007-09-01
You suggest it might be a DNS problem, am I correct?
DNS are set up in /etc/resolv.conf. Please open a terminal (> Applications > Terminal) and paste the output to:
```
cat /etc/resolv.conf
```

---

### Post by lonoy on 2007-09-01
Thanks

```
nameserver 192.168.30.1
nameserver 0.0.0.0
```


My original adapter shows 

[HTML]nameserver 10.1.1.1[/HTML]

which works fine.

---

### Post by bapoumba on 2007-09-01
Please try to change to the DNS that work. Open a terminal and run:
```
sudo nano -B /etc/resolv.conf
```
nano is a small text editor.
Replace the first line with:
```
nameserver 10.1.1.1
```
CTRL-O will save the file (same name, hit <enter>)
CTRL-X will exit nano.

Does this work ?

---

### Post by lonoy on 2007-09-01
No luck sorry. I changed the DNS to 10.1.1.1 and saved but still no Internet access. Then when I rebooted the DNS settings reverted back to the original non-working ones.

Please note that I do get limited access with the 192.168.30.1 settings, I can reach Google, Yahoo! and alike but no further. I can reach this site for example nor download emails.

---

### Post by bapoumba on 2007-09-02
Hmm. could you post the output to:
```
cat /etc/network/interfaces
cat /etc/resolv/conf
ifconfig
```

I'm not that good with networking, but others will have a look at it :)

---

### Post by lonoy on 2007-09-03
cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

-------------------------------------

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:48:04:FF:18  
          inet6 addr: fe80::20a:48ff:fe04:ff18/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5792 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3020722 (2.8 MiB)  TX bytes:1039407 (1015.0 KiB)
          Interrupt:16 Base address:0x2000 

eth0:avah Link encap:Ethernet  HWaddr 00:0A:48:04:FF:18  
          inet addr:169.254.5.27  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0I can't find a flo
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1444 (1.4 KiB)  TX bytes:1444 (1.4 KiB)
----------------------------

cat /etc/resolv/conf
cat: /etc/resolv/conf: No such file or directory


------------------------
Thanks

---

### Post by bapoumba on 2007-09-03
Okay thanks. And sorry, there was a typo in one of the commands:
```
cat /etc/resolv.conf
```

So looks you have DHCP on. From the link you gave in the first post, you have an example of how a static IP is set in /etc/network/interfaces.

But anyway, I think it's something specific to your router. I have seen several threads regarding this, try to search the forums with your router specs.
[http://ubuntuforums.org/showthread.php?t=255394]("http://ubuntuforums.org/showthread.php?t=255394")
[http://ubuntuforums.org/showthread.php?t=312213]("http://ubuntuforums.org/showthread.php?t=312213")

---

### Post by lonoy on 2007-09-03
Here is the final code:

cat /etc/resolv.conf
# generated by NetworkManager, do not edit!



nameserver 10.1.1.1


Thanks for all your help. I will check out those links and see if I can get any further.


Cheers
Lonoy

---

### Post by lonoy on 2007-09-15
Have finally got Internet access thanks to info on this page:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106958](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106958)

Using the following advice found on that page:

```
sudo sysctl -w net.ipv4.tcp_window_scaling=0
```

Or

append "net.ipv4.tcp_window_scaling=0" in /etc/sysctl.conf

My download speed does seem a lot slower than with my previous (working) configuration, not sure if the above settings are the cause of that or not. If anyone has experience with the above changes then please let me know if I should expect a speed reduction thanks.

---

### Post by bapoumba on 2007-09-15
Glad to see you got it to work :)

---

### Post by snelo on 2008-01-03
Forgive me but....
Ohhhh I love you .... thanks for posting the solution.... I've been trying to find the solution all day...

I even tried Netcomm support... hmmm.

---

