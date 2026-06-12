---
title: "Upgrade Dapper--&gt;Hardy: now Apache2 will not start"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by wgw on 2009-08-17
I can't start Apache2 now that I have upgraded to Hardy:

> Failed to start apache :

 * Starting web server apache2
[Mon Aug 17 15:21:18 2009] [warn] NameVirtualHost *:0 has no VirtualHosts
(98 )Address already in use: make_sock: could not bind to address xxx.xx.xxx.xxx:8000
no listening sockets available, shutting down
Unable to open logs
   ...fail! (xxx etc is the ip)

What bothers me most is that I don't have any error logs!

I suppose I will have to remove and reinstall, but I am still hoping that there is a quick fix (could this be a permissions problem?).

here is what is running:
> 
$ sudo netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:mysql         *:*                     LISTEN     
tcp        0      0 *:webmin                *:*                     LISTEN     
tcp        0      0 xxx.xxx.xxx:497  *:*                     LISTEN     
tcp        0      0 localhost:497           *:*                     LISTEN     
tcp        0      0 *:ftp                   *:*                     LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
udp        0      0 *:10000                 *:*                                
udp        0      0 *:497                   *:*                                
udp        0      0 xxx.xxx.xxx:ntp  *:*                                
udp        0      0 localhost:ntp           *:*                                
udp        0      0 *:ntp                   *:*                                
udp6       0      0 fe80::20c:29ff:fed5:ntp [::]:*                             
udp6       0      0 ip6-localhost:ntp       [::]:*                             
udp6       0      0 [::]:ntp                [::]:*                             
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     11209    /var/run/mysqld/mysqld.sock

Any suggestions?

---

