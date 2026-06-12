---
title: "Lenovo Laptop Wireless card drivers"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by keevill on 2007-12-22
I am a total newbie to Linux/Ubuntu and am trying to convert from Windows.
I have set up 6.06 on my new Lenovo 3000 G400 Laptop. I am having difficulty getting the inbuilt wireless adapter set up. 
I believe that when I check device manager I see an entry for for a Broadcom Corp Unknown Device 4311 then this is the hardware I need to get started. 
I have checked  the Lenovo website and looked for Linux drivers for this card but there is nothing.
Can someone help me to get this set up ? Or am I going to be unlucky to get this working under Linux ?

---

### Post by bwhite82 on 2007-12-22
Firstly, welcome to Ubuntu!
Now, open up a terminal and type: ifconfig
Please copy and paste the output here.

---

### Post by keevill on 2007-12-22
thanks for helping !!

lenny@lenny-laptop:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:197 errors:0 dropped:0 overruns:0 frame:0
          TX packets:197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15088 (14.7 KiB)  TX bytes:15088 (14.7 KiB)

(even this was a bit challenging.. had to save it in text format such that windows could recog it and transfer onto a usb thumbdrive and then onto my old win pc cos I don't have any network yet on the new UB box )

-keevill-

---

### Post by bwhite82 on 2007-12-22
Hmm...seems that no network devices are configured at all.

Makes things tricky when you aren't connected to the internet on your UB box. You need to install the package "bcm43xx-fwcutter" but how to do this without a net connection? Transferring with your USB will likely not work because of the dependencies. You can try though:

-goto packages.ubuntu.com
-search for the above-mentioned package (for your UB version) transfer it to your USB, put in on  your UB desktop and double click it.

Really though, all of this would be MUCH easier if you simply installed the latest version of Ubuntu, 7.10. Any reason why you chose 6.06?

---

### Post by keevill on 2007-12-22
ok then I will install Ubuntu, 7.10
I guess that should be easy - there's no data or anything to save.
Will post back later when that's done

---

### Post by keevill on 2007-12-22
OK I have now installed ver 7.1.
Here's the ifconfig report

lenny@lenny-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1B:38:07:25:1F   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:21  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by keevill on 2007-12-22
Now I can get to internet and can find the page referred to but I am unsure of how to go about downloading and installing the install the package "bcm43xx-fwcutter" 
What file must I use and how to go about it ?
many thanks for any help here...

---

### Post by Giradman on 2007-12-22
> **keevill said:**
> OK I have now installed ver 7.1.
Here's the ifconfig report.....................

Hmmm - your screen shot shows that your 'wired' ethernet adapter is being recognized (as eth0 w/ its MAC#) - you might want to try a 'wired' connection to your laptop to see if you can connect to the internet directly; if possible, this might simplify your efforts?

I have an old IBM ThinkPad X40 running Ubuntu 7.10 - currently connected via 'wireless' at a hotel, but have also connected successfully w/ a 'wired' connection same place; below is my generated response from 'ifconfig' - both my wireless & wired adapters are recognized as eth1 & eth0, respectively; the connected 'wireless' adapter is showing the current internet connection stats.

So, not sure what the issue may be, but give the 'wired' option a try, and then others hopefully can add some more input - should be an easy fix, I would hope - good luck! :(

---

### Post by bwhite82 on 2007-12-23
> **keevill said:**
> Now I can get to internet and can find the page referred to but I am unsure of how to go about downloading and installing the install the package "bcm43xx-fwcutter" 
What file must I use and how to go about it ?
many thanks for any help here...

OK Ubuntu now seems to be recognizing either your wireless card or your NIC, you don't have to goto that website now.  Goto System>Administration>Network and it will tell you either "Wired Connection" or "Wireless connection". My guess is that its "Wired connection" in which case connect your UB computer to your modem and/or router to put it on the net.

Then simply open a terminal and type:

sudo apt-get install bcm43xx-fwcutter

This package should automagically download firmware for you. After which time, post the result of ifconfig again.

And keep the faith, Linux can sometimes be difficult to get setup (even Ubuntu) but once you do you will rarely encounter problems unless you create them for yourself. Trust me, once you're up and running and you begin to learn Linux, you won't look back.

Alternatively, check out this post: [http://ubuntuforums.org/showthread.php?t=405990]("http://ubuntuforums.org/showthread.php?t=405990")

---

### Post by keevill on 2007-12-23
I did manage to install the package but it didn't seem to work so I disabled it in the restricted drivers manager.
Now when I connect to the Internet via wired lan and issue the command above here is the result of it together with the latest ifconfig.


lenny@lenny-laptop:~$ sudo apt-get install bcm43xx-fwcutter
[sudo] password for lenny:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcm43xx-fwcutter is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package bcm43xx-fwcutter has no installation candidate
lenny@lenny-laptop:~$ 


lenny@lenny-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:38:07:25:1F  
          inet addr:192.168.0.37  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe07:251f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1005 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1271940 (1.2 MB)  TX bytes:188564 (184.1 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1408 (1.3 KB)  TX bytes:1408 (1.3 KB)

---

### Post by keevill on 2007-12-23
Here;s the latest ifconfig after I went thru the process described in the link given above .
The adaptor seems to be working but the lan cannot be browsed not Internet accessed even giving fixed ip or dhcp.
Getting closer perhaps...

---

### Post by keevill on 2007-12-23
sorry forgot to attach the latest lsconfig

lenny@lenny-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:38:07:25:1F  
          inet addr:192.168.0.37  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe07:251f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1810638 (1.7 MB)  TX bytes:397211 (387.9 KB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:1A:73:B2:90:F1  
          inet addr:192.168.0.81  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:976 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:220 (220.0 b)  TX bytes:546 (546.0 b)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2032 (1.9 KB)  TX bytes:2032 (1.9 KB)

---

### Post by bwhite82 on 2007-12-23
Now it looks like you're in business, I see two devices listed. Everything working now?

---

### Post by keevill on 2007-12-23
I am sorry to say that I still cannot connect to the network.
If I go to network settings, I can see both wireless connection and wired connection . The correct Essid is shown.The properties look correct too with wpa personal security and I have input the network password. I have also given a static ip within the network in case dhcp has a problem. Also I have manually input the gateway ip
There is nothing shown in the Location box at top of the network settings applet.
If I go to Network tools and select the correct ethernet interface (eth1)  it all looks correct. If I click on configure for the network device it all looks correct.
Pinging the gateway or another machine on the network produces no reply.
Can I give you any other info to help me sort out this thing.
Of course the hard wired network interface works fine.

---

### Post by keevill on 2007-12-23
does this help anyone to point me in right direction ?

lenny@lenny-laptop:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311" 
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid    
          Bit Rate=1 Mb/s   Tx-Power=18 dBm    
          RTS thr:off   Fragment thr:off 
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by keevill on 2007-12-23
I got it working. 
I noticed that the ping command 192.168.0.83 ( my router ip) came back with another ip as unresolved.
Something like.
ping 192.168.0.83 ....

pinging 192.168.0.37 ureachable ... ( NOTE the incorrect ip address )
This ip was the ip of my unconnected wired lan. 
I had prev given a fixed ip to the hard wired connection and although the cable was disconnected it seemed to be interfering. 
I changed the hard wired lan to be dhcp AND disabled it for good measure and hey presto wireless worked .
Hoorah and thanks for help !!

---

### Post by bwhite82 on 2007-12-23
Glad to see you got it working. :guitar:

---

### Post by keevill on 2007-12-24
well my happy exp was short lived. I found the network very unreliable - only unable to connect to one network in my office whereas other machines (win) had no problem connecting to the other local wireless networks.
Then, the machine hung and when it came  back, the network adaptor is now not showing.
Attempts to re-install the broadcom wrapper etc have failed.I see the error message that the broadcom chipset cannot be found - pls use lspci command to verify I have such a chipset. I do and it shows up.
Perhaps , it's time to give up installling UB on this box. 
Disappointing really, I was hoping to get rid of Win but I know if I stick in my win install cd it will find everything and all will be running fine for a while anyway.......

---

