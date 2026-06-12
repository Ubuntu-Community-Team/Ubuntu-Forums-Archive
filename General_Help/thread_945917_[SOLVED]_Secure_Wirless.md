---
title: "[SOLVED] Secure Wirless"
date: 2008-10-12
forum: General Help
---

### Post by yarn on 2008-10-12
I just bought a new dell inspiron 1525 laptop and i had the hardest trouble getting my wireless internet to work since dell does not give out (i guess source code for the driver)...but i finally got it to work using a driver called wl. I also am using wicd to manage my networks. My only problem is that I can not connect to any secure networks. I connect to unsecure networks perfectly. I am using a Broadcom Corporation BCM4312 802.11b/g (rev 01) wirless card. Do you have any ideas on this. I am running Ubuntu 8.04 with kernel 2.6.24-19-generic....thank you in advance.

---

### Post by Sam on 2008-10-12
Have you tried [this method](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) ?

---

### Post by bodhi.zazen on 2008-10-12
Can you be more specific ?

What router ? What encryption protocol ? What have your tried ? wicd usually works fairly well ;)

---

### Post by yarn on 2008-10-12
no i have not tried that method but it does look somewhat promising...the router shouldnt matter because i can not connect to any secure network...but it is a belkin router...i am also using wpa.
b
SAM...i read the articla you showed me but dont really understand how or what to do...can you maybe explaine it a little better?  thank you for the replys!!!

---

### Post by Sam on 2008-10-12
First you must have "universe" repository enabled. ([uhelp]community/Repositories/Ubuntu[/uhelp])

Then install the package [b43-fwcutter](apt://b43-fwcutter).

Reboot and try if it works.


Ask if you're stuck somewhere.

---

### Post by yarn on 2008-10-12
i tried it and it didnt change anything. It will just says obtaining IP address...it is like it is finding the router, it goes through a validating stage...then it tries to obtain an ip address for about a minute or so then just says not connected...thank you anywayz...have any other ideas...open to anything...really need this to connect to school network and home network...thanks

---

### Post by bodhi.zazen on 2008-10-13
for wpa I found wicd works better. I struggled with network manager for several weeks, but wicd worked "otu of the box"

wicd is also much more reliable when traveling.

It is quite easy to install :

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Some people have had issues with it, in which case it is easy to revert to network manager.

---

### Post by yarn on 2008-10-13
ok so i ended up having to reinstall ubuntu bcuz i ran something i apparently shouldnt have run in terminal. The way that i have my wirless working is that normally my wl driver which is a restricted driver was checked but not in use...when i would uncheck it and recheck it it would say that i need to restart my comp to use it..so i would do this and it would go back to saying it was checked but not in use. I had to add wl to the modules file in /ect/modules or something. Now it automatically starts when i run ubuntu...now i just still cant connect to secure wireless...i have trying using other drivers and ndswrapper but nothing else will let my wireless work at all except the way i just described...does anybody know of anything that would let me connect to a secure network with these settings...please...any ideas...i really need to be able to connect to my secure network...thank you everyone for your help.

---

### Post by bodhi.zazen on 2008-10-13
did you try wicd ?

as I indicated, I had the exact same problem with network manager.

---

### Post by yarn on 2008-10-13
yea...sorry i forgot to mention that..i have tried both the default network manager and i am currently using wicd...neither will connect to a secure network...only unsecure...thanks for the quick reply...any other ideas?

---

### Post by bodhi.zazen on 2008-10-13
In wicd, in the configuration section, select "WPA 1/2" I think it is called and enter your network password. Take care to use hex or plain text as necessary.

Then try to connect.

If that fails, under options, be sure you are using the correct driver for your card, I think Wext or ndisdriver would be the first two I would try. If they fail you will need to look up your network card and see what driver is advised.

PS: I feel you pain, but to be honest wireless settings are difficult in BOTH Windows and Linux, IMO, due the the multiple protocols and standards ...

---

### Post by yarn on 2008-10-13
thank you...i am at work right now and using windows...i will take a look when i get home...but i know i have already tried every driver under the options and none of them work...lol...ill see if i can find what driver to use momentarily...and when u say look up my driver..do u mean which driver i should use for ubuntu...or which windows driver it is?   thanks again

---

### Post by bodhi.zazen on 2008-10-13
Yes, try to do a google search on your wireless card and see what driver is advised for Ubuntu (it will probably be a windows driver).

---

### Post by yarn on 2008-10-13
ok so i found this [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)  it says that it is new i think but what should i do with the tar.gz file...not sure if it will install by itself or if i just need to open it to get the driver...any thoughts?...still at work so i dont know what iot actually looks like...hopefully i can get this to work and hopefully it is not just another driver i have already tried before.   oh also...how do i know if i should use the 32 bit or the 64 bit...never have really understood the difference but i guess i never have needed to untill now?

---

### Post by bodhi.zazen on 2008-10-14
> **yarn said:**
> ok so i found this [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)  it says that it is new i think but what should i do with the tar.gz file...not sure if it will install by itself or if i just need to open it to get the driver...any thoughts?...still at work so i dont know what iot actually looks like...hopefully i can get this to work and hopefully it is not just another driver i have already tried before.   oh also...how do i know if i should use the 32 bit or the 64 bit...never have really understood the difference but i guess i never have needed to untill now?

You are in luck, directions are in the README.txt

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

If you are running 32 bit arch, use the 32 bit driver. If you are running 64 bit, use the 64 bit driver.

What version of Ubuntu did you install ? Do you know the difference between a 32 bit processor and a 64 bit processor ? Do you know which one you have ?

If not :

```
cat /proc/cpuinfo
```

---

### Post by yarn on 2008-10-14
ok at work again so i cant check to see which bit cpu i have..i want to say it is a 32 bit though...and i read the read me file...and i am pretty sure it says that it is the wl driver in their which is what i am already using?  can u confirm?   or is it possible it is a different driver but the same name or newer version?   thanks again

---

### Post by yarn on 2008-10-16
i ran that code and i didnt see a 32 or 64 bit ?

---

### Post by bodhi.zazen on 2008-10-16
> **yarn said:**
> i ran that code and i didnt see a 32 or 64 bit ?

Please post the output and we will translate :twisted:

You can also 

```
uname -m
```

---

### Post by yarn on 2008-10-16
ok it sais i686  ....do u think that is the same driver i am already using?

---

### Post by bodhi.zazen on 2008-10-17
i686 = 32 bit

I have no idea re: driver

but since yours is not working are to feel there is much to loose.

The README is quiet good, if you get stuck just ask :)

---

### Post by yarn on 2008-10-19
welp i have great news...i finally was able to connect to my secure wireless router...for some reason wpa will still not work...but when while i was at someone elses home...i was able to connect to their secure network which was using WEP encryption...all i had to do was change my encryption on my router...thank you for all the help...really appreciate it...happy ubunting

---

