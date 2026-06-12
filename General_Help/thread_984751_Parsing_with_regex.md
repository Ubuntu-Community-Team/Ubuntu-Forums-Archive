---
title: "Parsing with regex"
date: 2008-11-16
forum: General Help
---

### Post by deathbywedgie on 2008-11-16
I use grep for finding every line in a file that contains certain text, but how do I extract specific information out of each line without printing the entire line? I've found a number of examples online of scripts in perl and other languages, but they're complex and usually do more than I need. Is there no way to do it in a single command? I'm not versed in those languages and have a difficult time following their logic. I'll get there, I think, but I'm not there yet. heh

As an example, let's say I have a log file from an FTP server that contains a timestamp, an IP address, the result of a connection attempt, and perhaps other information. If I want to use regex to strip out only the IP address of the connecting host in each line of the file, how could I do that?

---

### Post by beren.olvar on 2008-11-17
I usually use cut. If the data you need is alway at the same position you can use it.
for example in ifconfig I get something like
```

wlan0     Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: XXX::XXX:XXXX:XX:XX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          etc

```
so,
ifconfig wlan0 |grep "inet addr" |cut -d: -f 2 |cut -d" " -f 1
will do the trick

the first one gives me the line from the first ":" until the second (192.168.1.107  Bcast)
the second cut gives until the first space 
so it will give my ip address (192.168.1.107).

There are better methods, but this is simple and works well

hope it helps
cheers

---

