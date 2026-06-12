---
title: "Delete"
date: 2008-09-04
forum: General Help
---

### Post by Nylo on 2008-09-04
1shw -c network is not working.  I tried Lshw -c network and I get nothing about my wireless.

---

### Post by Peter09 on 2008-09-04
its not 1(one) its l (alpha) so the command is

```
lshw -C network
```

:)

---

### Post by Nylo on 2008-09-04
> **Peter09 said:**
> its not 1(one) its l (alpha) so the command is

```
lshw -C network
```

:)

I tried that but I get a "print program version" with no info on my wireless.

---

### Post by Peter09 on 2008-09-04
In Linux the case of the text matters, its a capital C.

---

### Post by Nylo on 2008-09-04
> **Peter09 said:**
> In Linux the case of the text matters, its a capital C.

That did it.  

Learning Linux is fun....  I think.   :confused:

---

### Post by Peter09 on 2008-09-04
Yes- its a challenge, but rewarding

---

### Post by Nylo on 2008-09-04
> **Peter09 said:**
> Yes- its a challenge, but rewarding

So far the reward keep getting taken away.

Upon my initial loading of Ubuntu, and much tweaking, I finally got the WiFi to work.  Then there was a Ubuntu update which afterward I lost my WiFi and cannot get it back no matter what I do. Any ideas?

Intel 82815
Netgear WG511U WiFi card

ps.  I found it strange that the update had 112 items.  One of which was Firefox 3.0.....  Which was already on my Sony Vaio.

---

### Post by Peter09 on 2008-09-04
Can you post the out put of the ```
lshw -C network
``` command and also the output of the ```
ifconfig
``` command

---

### Post by Nylo on 2008-09-04
> **Peter09 said:**
> Can you post the out put of the ```
lshw -C network
``` command and also the output of the ```
ifconfig
``` command

I have them but I'm not sure how to get them into my desk top from my laptop.  I tried to drop the doc file in my thumb drive but Ubuntu wont let me.  Solution?

((((I just figured it out))))
--------
WARNING: you should run this program as super-user. 
  *-network                
       description: Ethernet interface 
       product: 82801BA/BAM/CA/CAM Ethernet Controller 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@0000:01:08.0 
       logical name: eth0 
       version: 03 
       serial: 08:00:46:40:ac:61 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes 
  *-network 
       description: Wireless interface 
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: wifi0 
       version: 01 
       serial: 00:0f:b5:34:f7:75 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g 

-------

ath0      Link encap:Ethernet  HWaddr 00:0f:b5:34:f7:75   
          inet6 addr: fe80::20f:b5ff:fe34:f775/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
ath0:avahi Link encap:Ethernet  HWaddr 00:0f:b5:34:f7:75   
          inet addr:169.254.8.59  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
 
eth0      Link encap:Ethernet  HWaddr 08:00:46:40:ac:61   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2374 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2374 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:119084 (116.2 KB)  TX bytes:119084 (116.2 KB) 
 
wifi0     Link encap:UNSPEC  HWaddr 00-0F-B5-34-F7-75-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:7262 errors:0 dropped:0 overruns:0 frame:11 
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:199  
          RX bytes:1378845 (1.3 MB)  TX bytes:4050 (3.9 KB) 
          Interrupt:9

---

### Post by Peter09 on 2008-09-04
Can you connect your laptop through a wired link?

---

### Post by Nylo on 2008-09-04
> **Peter09 said:**
> Can you connect your laptop through a wired link?

Read post #10

---

### Post by Peter09 on 2008-09-04
This appears to show that your wireless connection is running.

Have to tried to configure it to connect to your network?

---

### Post by Nylo on 2008-09-04
> **Peter09 said:**
> This appears to show that your wireless connection is running.

Have to tried to configure it to connect to your network?

Have I tried?  Like 20 times.  Like I said after fighting with this BUGGY network manager it finally was up and running....  That is until I received the 112 item Ubuntu update.  Now I cannot get it to budge.

---

### Post by Peter09 on 2008-09-04
:)

OK.

When you right click on the network manager icon do you get the options to enable the wireless network?

What do you see when you left click on the network manager icon?

---

### Post by Nylo on 2008-09-04
> **Nylo said:**
> Have I tried?  Like 20 times.  Like I said after fighting with this BUGGY network manager it finally was up and running....  That is until I received the 112 item Ubuntu update.  Now I cannot get it to budge.

One interesting thing is when I go back and check my passphrase it has more characters than I put it..

---

### Post by Peter09 on 2008-09-04
Are you seeing your wireless network when you right-click - if so you should be able to connect.

---

### Post by Nylo on 2008-09-04
> **Peter09 said:**
> :)

OK.

When you right click on the network manager icon do you get the options to enable the wireless network?

What do you see when you left click on the network manager icon?

Right click: Launch, Properties, etc....
Left click: It launches network manager.

---

### Post by Peter09 on 2008-09-04
What connection options do you see when you right click?

---

### Post by Peter09 on 2008-09-04
Hang on --- do you have two icons for the network manager?

If you right click does it give you the option to remove from panel?

---

### Post by Nylo on 2008-09-04
> **Peter09 said:**
> What connection options do you see when you right click?

I have never encountered anything more **[SIZE="4"]B U G G Y[/SIZE]** than this Network manager!

Its now working and I didn't do a thing.

---

### Post by Peter09 on 2008-09-04
OK - well lets hope it keeps going :) I'm off to get some sleep, not sure where you are but its midnight over here.

---

### Post by Nylo on 2008-09-04
> **Nylo said:**
> I have never encountered anything more **[SIZE="4"]B U G G Y[/SIZE]** than this Network manager!

Its now working and I didn't do a thing.
My passphrase has six characters.  When I go back to check I find it has gone from six to filling the entire passphrase window.  Have you seen anything like this?

---

### Post by Peter09 on 2008-09-04
Yes,
its normal - its stops people coming along and finding how many characters are in your phasephrase.

---

### Post by Nylo on 2008-09-04
> **Peter09 said:**
> OK - well lets hope it keeps going :) I'm off to get some sleep, not sure where you are but its midnight over here.

Hey Peter09, 

Thanks for your help.  I really do appreciate you taking the time to resolve this issue.

Its 4:19 pm, sunny, and 91 degrees here in the San Francisco Bay Area.  I'm burning up!  :)

Be well,
Nylo

---

