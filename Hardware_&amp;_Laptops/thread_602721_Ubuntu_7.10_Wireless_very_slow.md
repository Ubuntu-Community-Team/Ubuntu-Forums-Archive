---
title: "Ubuntu 7.10 Wireless very slow:"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by dyous87 on 2007-11-04
I recently formatted my computer which was running Ubuntu 7.04 and installed 7.10 and my wireless is recognized and works but is dreadfully slow. 

I have a Sony Vaio VGN-FZ140E and it has the Intel Wireless 4965 AGN card which is supported by Gutsy Gibbon. I couldn't get the native drivers working with  Feisty Fawn but I was successful in using the ndiswrapper drivers to work with it. The speeds were decent the only problem was the wireless would make the entire computer lock up and require a reboot occasionally.

Anyway, I upgraded to Gutsy Gibbon and my wireless is recognized all though the radio light does not go on or off. Also my wireless seed is incredibly slow and downloads top at about 17kb/s. Network manager never shows a connection stronger then 85% even if I am sitting right in front of my router. 

I wasn't having any of these problems with ndiswrapper and Feisty. Does anyone have any idea what is causing this?

Thanks,
David

---

### Post by Vevmesteren on 2007-11-04
I'd like to second that. I am on a Dell M1210. When the wireless finally connects (and it does not drop [which it seems to be doing A LOT]) then my connection which rarely exceed 90% as well. Though I do not have the speed issue. I get well above the speeds described here, but I do have troubles keeping a connection.

a little edit:
I secured my network (it used to be open), and th connectivity issue seems solved now. It seems that Ubuntu does not like unsecured networks. Anyone else had that problem?

---

### Post by elj4176 on 2007-11-04
I'm having the same problems. I have the bc43xx wireless that was using the windows driver on feisty. Now after the upgrade I think it is using the cutter driver and crawls. I can't even stream music from a file server on my LAN.
Maybe if I blacklist the cutter driver it might get back to the speed it had before?
any idea how to do that?

---

### Post by dyous87 on 2007-11-06
Well I have been playing around with it and have been unable to make any progress with my wireless speeds so I decided to go back to using ndsiwwrapper.

I downloaded and installed the latest ndiswrapper from the official site and I made sure that I uninstalled any ndiswrapper or ndiswrapper-utils packages that came preinstalled by default. I then compiled ndiswrapper and installed the 'NETw4x32.INF' driver.

A simple:
```
sudo rmmod iwl4965
```and then a:
```
sudo modprobe ndiswrapper
```got my wirless working perfectly! :)

There must be some kind of glitch or bug with the native intel drivers.

Oh before you modprobe ndiswrapper make sure you have your wirless turned off through the hardware switch. You may turn it back on after ndiswrapper is modprobed. 

Here is a link to download the 4965agn windows drivers at intel's site incase anyone needs them: [http://downloadcenter.intel.com/detail_desc.aspx?agr=N&ProductID=2259&DwnldID=13000&strOSs=44&OSFullName=Windows*%20XP%20Professional&lang=eng]("http://downloadcenter.intel.com/detail_desc.aspx?agr=N&ProductID=2259&DwnldID=13000&strOSs=44&OSFullName=Windows*%20XP%20Professional&lang=eng")

Hope this can help some people.

David

---

### Post by imopen on 2008-01-17
I have the same issue :(

I replaced the iwl4965 with ndiswrapper and windows driver and things are better and faster now, but often the connection freezes, I have to restart networking with "sudo /etc/init.d/networking stop" and then with the corresponding start. :(

Do you have some tips? 

Thank you in advance. :)

---

### Post by dyous87 on 2008-01-17
Hmm that's strange. I've been using it with the ndiswrapper drivers for quite some time now and I haven't had any problems. Can it possible be a problem with your wireless router?

---

### Post by foppeh on 2008-01-17
Do check Network ->Wireless-> DNS. I've seen on two systems the first adress is the computer's IP. It won't find a nameserver there. This slows the connection. So if it is 192/168/xyz.xyz remove this entry.

If this is not related to your problem, simply ignore me :-|

Good luck

---

### Post by imopen on 2008-01-18
Thank you for answers.

No it isn't a DNS problem, I use static DNS pointed to opendns ones.  The connection simply freezes, I am unable to ping the router  (192.168.1.1) too.  After restart networking with /etc/init.d script the connection begins again to work. :confused:

On the log (syslog, messages) I notice nothing interesting.


I don't know if it is a router problem, I use a dlink g604t and I never had problems with old computer (the one got problem is a brand new). I'll give a try with another router (a friend of mine got double). I'll let you know. :popcorn:


Anyway do you ever tried compiling and using the open driver (iwl4965) in its latest release? If so, it's faster than Ubuntu release?


Thank you again. ;)

---

### Post by imopen on 2008-01-19
I think I found the problem ;)

After few minutes the driver stop to talk with my router because of the encryption. Using none encryption it works well, without problems. :)

Waiting April, the next release of Ubuntu (and probably new official driver), I'll use none encryption and I'll filter only on mac address... it's a good temporaly compromise. 

Thank you all ;)

---

