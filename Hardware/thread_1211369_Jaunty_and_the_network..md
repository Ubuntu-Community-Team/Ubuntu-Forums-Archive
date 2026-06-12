---
title: "Jaunty and the network."
date: 2009-07-12
forum: Hardware
---

### Post by sieger007 on 2009-07-12
[COLOR="Blue"]Hi Folks
I  Wanted  to make the most "featured" Linux Build on my Toshiba X305 Laptop.Its a 64 Bit Machine
I tried Fedora 11 Live   ( Not so impressive looks, Network keeps disconnecting much the same as here and Skye was problematic )  so finally got Jaunty on EXT2 
I don't know about other folks.PLEASE SOMEONE CAN YOU HELP WITH THIS ?
--- My Wireless DOES work BUT will take 5 times longer to search results compared to any Windows OS.Sometimes is spontaneously disconnects and at other times,  the connection is there but addressed will not be resolved and I have to close FF and restart it couple of times.
 I think there is some messed up. 
Here is some  101 Info :
uxxx@ToshDebLX94599:~$ version
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"
Linux ToshDebLX94599 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux

My T-Shooting approaches were as follows :

<> Windows Wrapper Driver :
I heard of this . Is  that a better option that using the Native Linux Driver.
Has anyone had better luck. 
How do you install it on linux
<> IWCONFIG : Is there something I should be doing that I am not .
Can someone advise commonly tweaked settings here .
Has anyone HAD BETTER LUCK GETTING THE WI-FI to work with  changing the settings  like freq etc.BTW I am in CA.
<> Change the Drivers :
Here is what I found out :
[http://www.atheros.cz/](http://www.atheros.cz/)
There is a Linux Driver out there for 928X.
is this one the SAME as ath9k dirver currently installed ?. Currently 
the speed shows up as UNKNOWN or 1mbps.
I downloaded this driver and tried to compile it . Initially there were errors but I stepped through them
That took me to some other driver page madwifi drivers and there I found that madwifi was incompatible with Kernel 2.6.x something.But Ill  dont know if IO succeeded in compiling that driver. HOW DO I KNOW that ?  How  can I use the new driver at all ? 

This connection between //www.atheros.cz/  and madwifi being part of the same theme was ASSUMED, but is that so ...? or I am just trying to connected 2 unrelated dots here ....

My Card  is 802.11N speed. Why Cant I get this speed on Jaunty ?

<> Finally on Windows I noticed there are bunch of protocols installed Teredo Tunneling, IPV6 ...etc 
Would that be the reason? 
Do things improve if you install all that stuff or become worse ...


[/COLOR]

---

### Post by KoKuToru on 2009-07-12
I don't think you will have more luck with a other dist.

The ath9k driver you can install with (but it's backports..)
```
sudo apt-get install linux-backports-modules-jaunty
```

[http://www.atheros.cz/](http://www.atheros.cz/) haven't tried them yet.. 

You can try is set the IP to static..
DHCP sometimes didn't work on Ubuntu for me.. with the WLAN..

---

