---
title: "[SOLVED] MySQL and remote connections"
date: 2008-11-27
forum: General Help
---

### Post by ethernet on 2008-11-27
Pulling my hair out over this. Have searched the forum and read other threads but no luck.

I want to connect to the MySQL server running on my server over the Internet.

Running Ubuntu Server 8.04.1 (x64). Installed mysql (client and server) from the repos.

I have:

[LIST]
[*]commented out 'bind-address' in /etc/mysql/my.cnf
[*]restarted the mysqld several times (and even the server itself!)
[*]created a new user, granted this user all privileges from all hosts and reflushed privileges
[*]checked iptables: everything is 'accept'
[*]tried disabling fail2ban in desperation: no fix
[*]changed the default port to 1521 for both client and the daemon in my.cnf as my router won't allow me port forward to 3306 (which I have also set up)
[/LIST]

That's all I can think of now.

Can connect locally no problem with just:
```
mysql -u <user> -p
```

Have been using this on the remote machine:
```
mysql -h <my_server> -P 1521 -u <user> -p <pass>
```

I continue to get this error:
```
ERROR 2003 (HY000): Can't connect to MySQL server on '<my_server>' (111)
```

Open to suggestions. Could it have something to do with AppArmour?

---

### Post by geirha on 2008-11-27
Are you sure it is listening on the correct device? What is the bind-adress in my.cnf, and/or what's the output of ```
netstat -nap | grep mysql
```

---

### Post by ethernet on 2008-11-27
Thanks for replying.

I had bind-address commented out as it seemed to solve the problem in other threads. Tried setting it:
```
bind-address = 192.168.80
```

There are two NICs in the box but I'm only using one, eth1. Restarted MySQL and tried connecting remotely again. No luck.

Here's the output of netstat:
```
root@gecko:~# netstat -nap | grep mysql
tcp        0      0 192.168.0.80:1521       0.0.0.0:*               LISTEN      10580/mysqld    
unix  2      [ ACC ]     STREAM     LISTENING     24916    10580/mysqld        /var/run/mysqld/mysqld.sock
```

---

### Post by geirha on 2008-11-27
Try setting bind-address to 0.0.0.0 which should listen on all network devices, though your setup should work too. Try telnetting to that port localy ```
telnet 192.168.0.80 1521
``` then remotely ```
telnet <external ip> 1521
``` to see if the router is the show stopper or not. The result should be some random characters, and not 
```
Trying <ip address>...
telnet: Unable to connect to remote host: Connection refused

```

---

### Post by ethernet on 2008-11-28
I set the bind address to 0.0.0.0. Couldn't connect remotely.

Telnetting to the port locally on the server gives me the random characters as you've described.

The connection is refused when I do it remotely (same error message you posted). The odd thing is, all attempts I make at connecting to the MySQL server appear to be successful in my router's log:
```
Thu, 2008-11-27 19:17:46 - TCP Packet - Source:75.150.x.y,56931 Destination:86.45.x.y,1521 - [SQL-NET rule match]
```
but not telnet on the same port.

---

### Post by geirha on 2008-11-28
Well, seems it's the router that is the problem, but why, I don't know :/

---

### Post by ethernet on 2008-11-28
Thanks for all your help. Might try putting the server in a DMZ temporarily to see if it works. Think it's time to try another distro :(

---

### Post by ethernet on 2008-11-29
It would appear I was overlooking something quite obvious. Went through [this]("http://forge.mysql.com/wiki/Error2003-CantConnectToMySQLServer") detailed process of elimination.

The remote client was in a network (in a university) where outbound 3306 is being blocked. Didn't consider this and was trying to connect from two different machines. I am able to connect from machines on my LAN and from my web host's server no problem. Embarrassing! Hope this might help someone in future.

---

