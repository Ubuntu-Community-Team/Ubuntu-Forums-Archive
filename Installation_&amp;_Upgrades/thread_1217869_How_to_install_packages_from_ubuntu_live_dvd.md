---
title: "How to install packages from ubuntu live dvd"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by akashbhatia on 2009-07-20
Friends please tell me how to install packages from Ubuntu 9.04 live dvd
and kindly give the link to any book or articles for configuring Ubuntu asap.
thanks

---

### Post by jerrrys on 2009-07-20
here's half an answer

[http://www.google.com/search?q=installing+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=installing+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by akashbhatia on 2009-07-20
I have already installed Ubuntu mate.
I just need help with the packages, how to install them from the dvd
n how to configure my ADSL broadband.
kindly clear my queries
thanks

---

### Post by Partyboi2 on 2009-07-20
To install packages from the dvd you should be able to open a terminal and type
```
sudo apt-cdrom add
sudo apt-get update
```
Then you should be able to install packages from the dvd.
Or you can insert the dvd into the dvd rom and a window should open up, asking if you want to open Synaptic using the dvd.

---

### Post by akashbhatia on 2009-07-20
THANK U FOR THE ANSWER 
but when i insert the dvd no such prompt action appears 
I will try out the command line option and let you know the results.
Also I am not able to configure my broadbadn internet
any help with that ?
I gotta dial up modem

---

### Post by Partyboi2 on 2009-07-20
I don't know much about dial up modem connections, I can suggest trying
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) 
or maybe someone else will be able to help you with that.

---

### Post by akashbhatia on 2009-07-20
Thanks but I have found a solution for now.
I have configured my modem so that I am connected to the net as soon as the modem is switched on ...no need to dial the connection so I am able to connect to the net.
While downloading packages from the net several were broken...any solutions to that?
And can any1 plz tell me sm reference manual or any book for ubuntu 9.04 for newbies 
thanks again

---

### Post by Partyboi2 on 2009-07-21
You can download a free Ubuntu guide from [[COLOR=Blue]here[/COLOR]]("http://www.ubuntupocketguide.com/index_main.html")
If you have broken packages you can open a terminal  and type
```
sudo apt-get -f install
```
Can you post any errors you are getting.

---

### Post by Rhyn Weatherhead on 2009-07-29
Can you use the apt get command to get games and programms from the CD too. I have 9.04 but have a 6.10 with every major open source game on it. I can't download them will punish my adsl overtime so I need the games from the CD and have been looing for a command to do it. Found Gtks cdrom/cdromupdate

Anyone know if the APT get opens up the applicatins and games on that CD too?

Best Regards
Rhyn

---

