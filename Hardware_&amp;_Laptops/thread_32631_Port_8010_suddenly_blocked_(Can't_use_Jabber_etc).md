---
title: "Port 8010 suddenly blocked (Can't use Jabber etc)"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by dolny on 2005-05-08
I was browsing the web and installing new kde themes when my Psi (Jabber client) crashed, or maybe I rebooted the system and tried to launch Psi, I don't remember.
Anyway, it suddenly stopped working, saying that the port 8010 cannot be used to transmit the data :| I checked another communicator and it didn't work also - crashed with no msg. Please help me, I cannot use anny communicator now.

I'm using Kubuntu 5.04. I have no idea what might happened. What logs should I submit for you to check? How can I enable this port? I haven't got a firewall (well I installed one now, after the port problem but it's disabled).

HELP! PLEASE!

PS. This distribution is great, despite the port issue...

I have a Thomson Cable Modem (dhcp, interface: eth0).
Rebooting the system didn't help.

---

### Post by alastair on 2005-05-08
You could see if somethings listening on that port i.e.

man netstat

Perhaps run :

netstat -nap --inet

and look at the "local address" - anything on port 8010?

If you have a firewall enabled, this might interfere - see firewall rules via :

iptables -L -n

---

### Post by dolny on 2005-05-08
```
dolny@milkshake:~$ sudo netstat -nap --inet
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:8010            0.0.0.0:*               LISTEN     9226/psi

```

I can't this process it in the KDE System Guard. How can I kill it/fix this state?
Maybe Psi was set to start with the system and because I can't see it in the taskbar normally it 'hides' somewhere ;) ? I don't know, anyway I don't even know how to kill it.

---

### Post by dolny on 2005-05-08
Sorry I made a mistake, I now see the processes in the System Guard but it looks like this:

> dolny@milkshake:~$ sudo netstat -nap --inet
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN     7180/cupsd
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     7429/master
tcp        0      0 213.156.96.26:33050     66.249.85.99:80         ESTABLISHED8487/firefox-bin
udp        0      0 0.0.0.0:68              0.0.0.0:*                          7166/dhclient3
udp        0      0 0.0.0.0:631             0.0.0.0:*                          7180/cupsd
dolny@milkshake:~$

So the port is free but the communicator won't work. Jabber and the second one (Kadu). :( The port was blocked by another instance of Psi but when I killed it it still doesn't work :( Re-install of Psi didn't work :(

** It seems that the applications work but I can't see'em ... neither by alt-tab or on the taskbar... I don't know what to do :( :( :( **

---

### Post by dolny on 2005-05-08
Re-installing after deleting all config files helped. WEIRD.

---

