---
title: "Problems configuring firestarter"
date: 2006-01-03
forum: Installation &amp; Upgrades
---

### Post by mikerobinson on 2006-01-03
I currently have my ubuntu/kubuntu box with eth0 going to the cable modem and eth1 connected to my windows xp box. I have dhcp3-server set up on eth1 to share my internet connection with the XP box. I couldn't get it to work correctly until I installed the firestarter firewall yesterday.

I think I must have done something wrong in configuring it because my XP box can access anything correctly, but my ubuntu box can't seem to access my server (a dedicated server I rent). I can ping it and it replies to me, but when I try to connect via ssh/http/pop/smtp it doesn't do anything.

I told firestarter to allow incoming connections from the 3 IPs from the server, but they still keep showing up in the "blocked" events. The weird thing is that it's just that server that is blocked, and every other website (including this one) works fine.

When I disable the firewall, I can access the server correctly from the ubuntu machine, but the XP one can't even connect to the internet at all.

Where can I look to find out why firestarter is blocking connections from the ubuntu box to this server?

Thanks

---

### Post by mikerobinson on 2006-01-03
For example, this is part of the log file of blocked hosts. I have 72.21.40.205 in my "allow connections from host" section, but they are obviously being blocked:

> Time:Jan  3 13:02:21 Direction: Inbound In:eth0 Out: Port:36341 Source:72.21.40.205 Destination:10.39.1.198 Length:44 TOS:0x04 Protocol:TCP Service:Unknown
Time:Jan  3 13:02:30 Direction: Inbound In:eth0 Out: Port:36275 Source:72.21.40.205 Destination:10.39.1.198 Length:46 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan  3 13:03:22 Direction: Inbound In:eth0 Out: Port:36342 Source:72.21.40.205 Destination:10.39.1.198 Length:44 TOS:0x04 Protocol:TCP Service:Unknown
Time:Jan  3 13:04:21 Direction: Inbound In:eth0 Out: Port:36393 Source:72.21.40.205 Destination:10.39.1.198 Length:44 TOS:0x04 Protocol:TCP Service:Unknown
Time:Jan  3 13:04:30 Direction: Inbound In:eth0 Out: Port:36275 Source:72.21.40.205 Destination:10.39.1.198 Length:46 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan  3 13:05:51 Direction: Inbound In:eth0 Out: Port:36395 Source:72.21.40.205 Destination:10.39.1.198 Length:44 TOS:0x04 Protocol:TCP Service:Unknown
Time:Jan  3 13:06:30 Direction: Inbound In:eth0 Out: Port:36275 Source:72.21.40.205 Destination:10.39.1.198 Length:46 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan  3 13:06:51 Direction: Inbound In:eth0 Out: Port:36397 Source:72.21.40.205 Destination:10.39.1.198 Length:44 TOS:0x04 Protocol:TCP Service:Unknown
Time:Jan  3 13:07:51 Direction: Inbound In:eth0 Out: Port:36398 Source:72.21.40.205 Destination:10.39.1.198 Length:44 TOS:0x04 Protocol:TCP Service:Unknown
Time:Jan  3 13:08:30 Direction: Inbound In:eth0 Out: Port:36275 Source:72.21.40.205 Destination:10.39.1.198 Length:46 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan  3 13:08:52 Direction: Inbound In:eth0 Out: Port:36400 Source:72.21.40.205 Destination:10.39.1.198 Length:44 TOS:0x04 Protocol:TCP Service:Unknown
Time:Jan  3 13:09:52 Direction: Inbound In:eth0 Out: Port:36401 Source:72.21.40.205 Destination:10.39.1.198 Length:44 TOS:0x04 Protocol:TCP Service:Unknown
Time:Jan  3 13:10:30 Direction: Inbound In:eth0 Out: Port:36275 Source:72.21.40.205 Destination:10.39.1.198 Length:46 TOS:0x00 Protocol:TCP Service:Unknown
Time:Jan  3 13:10:51 Direction: Inbound In:eth0 Out: Port:36403 Source:72.21.40.205 Destination:10.39.1.198 Length:44 TOS:0x04 Protocol:TCP Service:Unknown
Time:Jan  3 13:11:51 Direction: Inbound In:eth0 Out: Port:36404 Source:72.21.40.205 Destination:10.39.1.198 Length:44 TOS:0x04 Protocol:TCP Service:Unknown
Time:Jan  3 13:12:51 Direction: Inbound In:eth0 Out: Port:36406 Source:72.21.40.205 Destination:10.39.1.198 Length:44 TOS:0x04 Protocol:TCP Service:Unknown
Time:Jan  3 13:13:52 Direction: Inbound In:eth0 Out: Port:36407 Source:72.21.40.205 Destination:10.39.1.198 Length:44 TOS:0x04 Protocol:TCP Service:Unknown
Time:Jan  3 13:14:52 Direction: Inbound In:eth0 Out: Port:36416 Source:72.21.40.205 Destination:10.39.1.198 Length:44 TOS:0x04 Protocol:TCP Service:Unknown
Time:Jan  3 13:15:52 Direction: Inbound In:eth0 Out: Port:36464 Source:72.21.40.205 Destination:10.39.1.198 Length:44 TOS:0x04 Protocol:TCP Service:Unknown
Time:Jan  3 13:16:52 Direction: Inbound In:eth0 Out: Port:36466 Source:72.21.40.205 Destination:10.39.1.198 Length:44 TOS:0x04 Protocol:TCP Service:Unknown

---

### Post by Peter76 on 2006-01-03
Looks like it's something with the ports... They are really high and change all the time and are not the ports for those services... Or did you configure your server like that? I asume you checked the firestarter manual? Good luck

---

### Post by mikerobinson on 2006-01-03
[QUOTE=Peter76]Looks like it's something with the ports... They are really high and change all the time and are not the ports for those services... Or did you configure your server like that? I asume you checked the firestarter manual? Good luck[/QUOTE]I'm not sure why the ports being accessed are so high. I didn't configure it like that. When I have the firewall disabled, the ports seem to be normal. I checked the firestarter manual, but it seems to be really basic and I can't find anything about this problem. Besides, if I take out all of the firewall blocked/allowed policies it **still** seems to block my server and nothing else.

---

### Post by mikerobinson on 2006-01-03
OK I tried as hard as I could going through every single setting and reading the manual alomst completely. I couldn't figure out why only that one server was being blocked on every protocol, so I just uninstalled it, deleted the /etc/firestarter directory and reinstalled it. Now it seems to be working fine. I just wish I didn't have to go through all this trouble...

Thanks for your help anyway, Peter76 :confused:

---

