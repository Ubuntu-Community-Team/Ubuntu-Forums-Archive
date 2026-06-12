---
title: "Internet connectovoty"
date: 2008-07-15
forum: General Help
---

### Post by jtesolin on 2008-07-15
Hello,

After an upgrade to hardy, I seem to be having internet issues. I am unable to connect to Firefox, or update Ubuntu. I tried changing the settings through the Gui in the toolbar with no luck. 

I am assigned an IP through my internet provider. This computer is connected to Apple airport extreme as the host computer (is that the right term?). Before upgrade I was able to connect fine. :confused:

The above set-up worked fine before the upgrade. Is there anything else I should post here? i.e. ifconfig output?

Thanks in advance.

---

### Post by Kevbert on 2008-07-15
Please post the output of
```
ifconfig
iwconfig

```

---

### Post by jtesolin on 2008-07-18
> **Kevbert said:**
> Please post the output of
```
ifconfig
iwconfig

```

Sorry for the delay!  The output is below.  Thanks, Jenn

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:2a:ae:fb:05  
          inet6 addr: 2002:63e1:e874:0:214:2aff:feae:fb05/64 Scope:Global
          inet6 addr: fe80::214:2aff:feae:fb05/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4838 (4.7 KB)  TX bytes:5813 (5.6 KB)
          Interrupt:20 

eth0:avahi Link encap:Ethernet  HWaddr 00:14:2a:ae:fb:05  
          inet addr:169.254.6.120  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66328 (64.7 KB)  TX bytes:66328 (64.7 KB)





iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by Kevbert on 2008-07-18
OK. Sorry, no help there then.  Please post the terminal output of
```
lspci
```
Also, what's the make and model of your PC.
If you check in the /lib/firmware directory you should find some firmware files (ending in .fw).  The names of these may give a clue as to what your wireless adapter is.

---

### Post by jtesolin on 2008-07-18
> **Kevbert said:**
> OK. Sorry, no help there then.  Please post the terminal output of
```
lspci
```
Also, what's the make and model of your PC.
If you check in the /lib/firmware directory you should find some firmware files (ending in .fw).  The names of these may give a clue as to what your wireless adapter is.

Whoops perhaps I am not explaining right. The machine that Ubuntu is on is actually what the router is fed through (so it should be accessing a wired connection not wireless). 

It is an Acer Aspire E500 (P4 3.06 ghz). Dual boot with WinXp (sadly ;) )

I am at work, so I cannot get the firmware, but will post as soon as possible.  I will also try to disconnect the lan from the router and a direct connection to the internet.

---

### Post by Kevbert on 2008-07-18
I've just had a look on the Acer [[COLOR="Red"]website.[/COLOR]]("http://support.acer-euro.com/drivers/desktop/aspire_e500.html")  It looks like your ethernet controller is a Marvell Yukon LAN.  I could not see the model number but hopefully it's the one in this [COLOR="Red"][[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=781022&highlight=Marvell+Yukon+Ethernet+Controller")[/COLOR].  If this does not work you could try searching on the Ubuntu Forums for Marvell Yukon Ethernet Controller as there seem to be many hits on the search.  Sorry I can't help further.

---

