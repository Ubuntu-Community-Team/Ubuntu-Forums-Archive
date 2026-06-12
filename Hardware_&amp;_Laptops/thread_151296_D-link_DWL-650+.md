---
title: "D-link DWL-650+"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by Raucom on 2006-03-27
Hi,

I have latest ubuntu distro in my compaq armada laptop. I am trying to install D-Link wlan card. All setting, ip addressess, routes, essid, password and DNS are set, but i cannot access the web. I can ping localhost and my wlan0 ip. But i cant ping anywhere else. Signal strength is good and packets move to AP and back. But not anywhere else. 

I have another machine running with same ubuntu, except it is a desktop and using eth0, but it has same setting and it goes thru same AP. Yes i have wlan and switch on same device. I had working setting on my fedora distro, same laptop but ndiswrapper and win drivers.

Does anyone know what could be wrong, or anything that helps..

Thank for advance.

---

### Post by ssalman on 2006-03-27
[FONT=Verdana]Do you have [/FONT][FONT=Verdana]encryption turned on? WEP or WPA?[/FONT]

---

### Post by Raucom on 2006-03-27
I have WEP encryption enabled.

---

### Post by ssalman on 2006-03-28
That may be the problem, try to establish a working connection to the web without the WEP, that will at least test your hardware without the complication of encryption. once we have accomplished that, we can move on to setup a working WEP connection... post back your findings.

---

### Post by Raucom on 2006-03-28
Allright, i remowed encryption and disabled network from GUI, then

ifconfig wlan0 down
iwconfig wlan0 up 192.168.0.2
iwconfig wlan0 mode managed
iwconfig wlan0 key off
route add default gw 192.168.0.1

I have use wep encryption with ascii password..

---

### Post by ssalman on 2006-03-28
You need to have a line like the below to connect to your wireless ESSID, also did you turn off the encryption at your router? (Sorry if I&#8217;m asking the obvious :))

iwconfig essid Your_ESSID

Using the above line with the setup you have in your previous post, you should be able to ping your router 192.168.2.1 (is that correct?) but to be able to browse the net with names (like [www.google.com)]("http://www.google.com%29"), you need to have your DNS setup, check your "/etc/resolv.conf" file. You need to make sure you have a line that reads &#8220;nameserver 192.168.2.1&#8221; (if 192.168.2.1 is your router)

Alternatively, did you try DHCP?? If it is enabled in your router, it will make your life a lot easier, it will setup the IP address, the gateway, the routing table, the DNS, you can use "dhclient wlan0" to enable it after you setup your connection using iwconfig.
   
  If still can&#8217;t connect, post your output of a complete trial of connection so I can see the results of each command. It would help to post the output of the following commands:
   
  iwlist wlan0 scan
  iwconfig wlan0
  ifconfig wlan0
   
  Hope it will work for you.

---

### Post by Raucom on 2006-03-29
Yes, 

I disabled encryption at router and after that connection worked. I read somewhere that ubuntu has problems with wep enabled and password is in ascii mode?? Is that true, because that was the situation and all seemed to works just fine, but i could not ping my AP or anything else, just my own IP. I there any solution to that problem??

I allso tried to enable wep with hex password, but my crappy router (cheap) did not accept any kind on password. Or every time i made the change, saved the configuration and checked, there was nothing. So i am fighting now with my router now to enable HEX password. 

I live in quiet neighbourhood and there arent many houses there, so my connection is pretty safe, and i prefer to use certain ip addresses, because if someone wants to use my connection, he/she must now IP what to use.

But i will keep on fighting :)

---

### Post by ssalman on 2006-03-29
Okay, great, now we know all your setup work just fine, and we have isolated the WEP as the problem... to tell you the truth I had a very hard time setting up WEP on a previous wifi card that I used to own... eventually I gave up and got another card.

Now, let's try a couple of stuff:
1- string WEP key: when you enter the key use 
```
 iwconfig wlan0 key s:xxxxx
```
where your string key is xxxxx, the "s:" prefix is to tell the iwconfig command that you are using a string key...

2- if that does not work, try to setup a 128-bit hex key on your router, if it is supported. if not 64 will be fine. when you enter the key use:
```
 iwconfig wlan0 key xxxxx
```
and if that does not help try:
```
 iwconfig wlan0 key xxxx-xxxx-xxxx-xx
```
placing a dash every 4 digits... sometimes this will help

and post back your findings... and keep on fighting ;)

---

