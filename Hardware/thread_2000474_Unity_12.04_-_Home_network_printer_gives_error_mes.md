---
title: "Unity 12.04 - Home network printer gives error message"
date: 2012-06-09
forum: Hardware
---

### Post by marco07 on 2012-06-09
Hello All:
I have ubuntu unity 12.04 installed on my both desktop (Gateway DX 200s) and laptop(Thinkpad R60). The desktop printer is set up OK, prints well from desktop and is also used as a home net work printer. The laptop through wireless connection to this home network, using samba, sees the lan printer and it is set up correct. However, I get the following error message when I try to print from the laptop:

Idle - NT_STATUS_ACCESS_DENIED opening remote spool print_txt

How can I resolve this issue?
Thanks in advance!

---

### Post by trukker on 2012-06-17
Same here... I upgraded from 11.10 and cannot print over the network. :-(

---

### Post by Morbius1 on 2012-06-17
In 12.04 cups and samba had a big fight and are no longer talking to each other. Counselors have been dispatched but it may take a while for the 2 to resolve their differences. The workaround for this is don't use Samba but connect to cups directly.

If the client is Windows: [http://ubuntuforums.org/showpost.php?p=12027719&postcount=8](http://ubuntuforums.org/showpost.php?p=12027719&postcount=8)

If the client is another Ubuntu box set the "Device URI" to something like this:
> [ipp://192.168.0.100:631/printers/Printer-Name]("ipp://192.168.0.100:631/printers/HP970-Draft")

---

### Post by fireoftroy on 2012-12-27
I tried ipp://<server IP>:631/printers/Printer-Name and now it just states the printer is not connected.

---

### Post by Tranas on 2012-12-30
> **Morbius1 said:**
> In 12.04 cups and samba had a big fight and are no longer talking to each other. Counselors have been dispatched but it may take a while for the 2 to resolve their differences. The workaround for this is don't use Samba but connect to cups directly.

If the client is Windows: [http://ubuntuforums.org/showpost.php?p=12027719&postcount=8](http://ubuntuforums.org/showpost.php?p=12027719&postcount=8)

If the client is another Ubuntu box set the "Device URI" to something like this:

This is the type of nonsense that explains why Linux is used by <5% users. 

You are forced to go through some sort of byzantine geek command line gibberish over a period of years to perform what should be simple and is obviously intended to be addressed by an existing GUI -

**>> print from Windows to a printer on an Ubuntu machine <<**

blaming this issue on a pissing contest between rival geek clans is disingenuous at best. The issue is ***YEARS OLD*** and is simply incompetent coders imho - and Ubuntu could care less....

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/967410)

but it is much older than that bug report ... and **certainly** preceeds 12.04

[http://forums.linuxmint.com/viewtopic.php?f=42&t=28397&p=618065#p618065](http://forums.linuxmint.com/viewtopic.php?f=42&t=28397&p=618065#p618065)

ymmv

---

