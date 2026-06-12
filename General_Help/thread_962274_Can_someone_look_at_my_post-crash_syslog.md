---
title: "Can someone look at my post-crash syslog?"
date: 2008-10-29
forum: General Help
---

### Post by moofang on 2008-10-29
Hi. I've been experiencing sudden hard shutdowns/reboots (as in it just goes off, poof) on my Laptop running Ubuntu for awhile now, and have not yet been able to pin down the problem. Can someone give me a hand and take a look at a snippet of my syslog contents (below)? This was taken right after one such hard shutdown.

Please let me know if there are any clues about the problem therein. Thanks :)

```

Oct 29 15:00:32 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:00:32 lim-laptop dhclient: DHCPACK from 137.132.155.236
Oct 29 15:00:32 lim-laptop NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Oct 29 15:00:32 lim-laptop dhclient: bound to 172.19.163.224 -- renewal in 787 seconds.
Oct 29 15:03:32 lim-laptop avahi-daemon[5203]: Invalid response packet.
Oct 29 15:03:34 lim-laptop last message repeated 3 times
Oct 29 15:07:29 lim-laptop nmbd[5736]: [2008/10/29 15:07:29, 0] nmbd/nmbd_incomingdgrams.c:process_local_master_announce(309) 
Oct 29 15:07:29 lim-laptop nmbd[5736]:   process_local_master_announce: Server U0707716 at IP 172.19.167.173 is announcing itself as a local master browser for workgroup NUSSTU and we think we are master. Forcing election. 
Oct 29 15:07:29 lim-laptop nmbd[5736]: [2008/10/29 15:07:29, 0] nmbd/nmbd_become_lmb.c:unbecome_local_master_success(149) 
Oct 29 15:07:29 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:07:29 lim-laptop nmbd[5736]:    
Oct 29 15:07:29 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP has stopped being a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:07:29 lim-laptop nmbd[5736]:    
Oct 29 15:07:29 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:07:45 lim-laptop nmbd[5736]: [2008/10/29 15:07:45, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Oct 29 15:07:45 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:07:45 lim-laptop nmbd[5736]:    
Oct 29 15:07:45 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP is now a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:07:45 lim-laptop nmbd[5736]:    
Oct 29 15:07:45 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:08:39 lim-laptop avahi-daemon[5203]: Invalid response packet.
Oct 29 15:08:41 lim-laptop last message repeated 3 times
Oct 29 15:09:01 lim-laptop /USR/SBIN/CRON[15586]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
Oct 29 15:09:01 lim-laptop /USR/SBIN/CRON[15585]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct 29 15:10:02 lim-laptop /USR/SBIN/CRON[15653]: (lim) CMD (/usr/bin/python /home/lim/ranwp.py)
Oct 29 15:10:22 lim-laptop nmbd[5736]: [2008/10/29 15:10:22, 0] nmbd/nmbd_incomingdgrams.c:process_local_master_announce(309) 
Oct 29 15:10:22 lim-laptop nmbd[5736]:   process_local_master_announce: Server BLACKNIGHT at IP 172.19.167.83 is announcing itself as a local master browser for workgroup NUSSTU and we think we are master. Forcing election. 
Oct 29 15:10:22 lim-laptop nmbd[5736]: [2008/10/29 15:10:22, 0] nmbd/nmbd_become_lmb.c:unbecome_local_master_success(149) 
Oct 29 15:10:22 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:10:22 lim-laptop nmbd[5736]:    
Oct 29 15:10:22 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP has stopped being a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:10:22 lim-laptop nmbd[5736]:    
Oct 29 15:10:22 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:10:39 lim-laptop nmbd[5736]: [2008/10/29 15:10:39, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Oct 29 15:10:39 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:10:39 lim-laptop nmbd[5736]:    
Oct 29 15:10:39 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP is now a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:10:39 lim-laptop nmbd[5736]:    
Oct 29 15:10:39 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:11:44 lim-laptop nmbd[5736]: [2008/10/29 15:11:44, 0] nmbd/nmbd_incomingdgrams.c:process_local_master_announce(309) 
Oct 29 15:11:44 lim-laptop nmbd[5736]:   process_local_master_announce: Server BLACKNIGHT at IP 172.19.167.83 is announcing itself as a local master browser for workgroup NUSSTU and we think we are master. Forcing election. 
Oct 29 15:11:44 lim-laptop nmbd[5736]: [2008/10/29 15:11:44, 0] nmbd/nmbd_become_lmb.c:unbecome_local_master_success(149) 
Oct 29 15:11:44 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:11:44 lim-laptop nmbd[5736]:    
Oct 29 15:11:44 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP has stopped being a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:11:44 lim-laptop nmbd[5736]:    
Oct 29 15:11:44 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:12:01 lim-laptop nmbd[5736]: [2008/10/29 15:12:01, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Oct 29 15:12:01 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:12:01 lim-laptop nmbd[5736]:    
Oct 29 15:12:01 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP is now a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:12:01 lim-laptop nmbd[5736]:    
Oct 29 15:12:01 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:13:39 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:13:39 lim-laptop dhclient: DHCPACK from 137.132.155.236
Oct 29 15:13:39 lim-laptop dhclient: bound to 172.19.163.224 -- renewal in 720 seconds.
Oct 29 15:13:39 lim-laptop NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Oct 29 15:13:46 lim-laptop avahi-daemon[5203]: Invalid response packet.
Oct 29 15:13:48 lim-laptop last message repeated 3 times
Oct 29 15:17:01 lim-laptop /USR/SBIN/CRON[16089]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 29 15:18:53 lim-laptop avahi-daemon[5203]: Invalid response packet.
Oct 29 15:18:55 lim-laptop last message repeated 3 times
Oct 29 15:19:14 lim-laptop nmbd[5736]: [2008/10/29 15:19:14, 0] nmbd/nmbd_incomingdgrams.c:process_local_master_announce(309) 
Oct 29 15:19:14 lim-laptop nmbd[5736]:   process_local_master_announce: Server BLACKNIGHT at IP 172.19.167.83 is announcing itself as a local master browser for workgroup NUSSTU and we think we are master. Forcing election. 
Oct 29 15:19:14 lim-laptop nmbd[5736]: [2008/10/29 15:19:14, 0] nmbd/nmbd_become_lmb.c:unbecome_local_master_success(149) 
Oct 29 15:19:14 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:19:14 lim-laptop nmbd[5736]:    
Oct 29 15:19:14 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP has stopped being a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:19:14 lim-laptop nmbd[5736]:    
Oct 29 15:19:14 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:19:31 lim-laptop nmbd[5736]: [2008/10/29 15:19:31, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Oct 29 15:19:31 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:19:31 lim-laptop nmbd[5736]:    
Oct 29 15:19:31 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP is now a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:19:31 lim-laptop nmbd[5736]:    
Oct 29 15:19:31 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:24:00 lim-laptop avahi-daemon[5203]: Invalid response packet.
Oct 29 15:24:02 lim-laptop last message repeated 3 times
Oct 29 15:25:39 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:26:09 lim-laptop last message repeated 3 times
Oct 29 15:27:13 lim-laptop last message repeated 5 times
Oct 29 15:27:26 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:27:27 lim-laptop nmbd[5736]: [2008/10/29 15:27:27, 0] nmbd/nmbd_incomingdgrams.c:process_local_master_announce(309) 
Oct 29 15:27:27 lim-laptop nmbd[5736]:   process_local_master_announce: Server BLACKNIGHT at IP 172.19.167.83 is announcing itself as a local master browser for workgroup NUSSTU and we think we are master. Forcing election. 
Oct 29 15:27:27 lim-laptop nmbd[5736]: [2008/10/29 15:27:27, 0] nmbd/nmbd_become_lmb.c:unbecome_local_master_success(149) 
Oct 29 15:27:27 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:27:27 lim-laptop nmbd[5736]:    
Oct 29 15:27:27 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP has stopped being a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:27:27 lim-laptop nmbd[5736]:    
Oct 29 15:27:27 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:27:40 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:27:45 lim-laptop nmbd[5736]: [2008/10/29 15:27:45, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Oct 29 15:27:45 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:27:45 lim-laptop nmbd[5736]:    
Oct 29 15:27:45 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP is now a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:27:45 lim-laptop nmbd[5736]:    
Oct 29 15:27:45 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:27:48 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:28:14 lim-laptop last message repeated 2 times
Oct 29 15:28:30 lim-laptop nmbd[5736]: [2008/10/29 15:28:30, 0] nmbd/nmbd_incomingdgrams.c:process_local_master_announce(309) 
Oct 29 15:28:30 lim-laptop nmbd[5736]:   process_local_master_announce: Server BLACKNIGHT at IP 172.19.167.83 is announcing itself as a local master browser for workgroup NUSSTU and we think we are master. Forcing election. 
Oct 29 15:28:30 lim-laptop nmbd[5736]: [2008/10/29 15:28:30, 0] nmbd/nmbd_become_lmb.c:unbecome_local_master_success(149) 
Oct 29 15:28:30 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:28:30 lim-laptop nmbd[5736]:    
Oct 29 15:28:30 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP has stopped being a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:28:30 lim-laptop nmbd[5736]:    
Oct 29 15:28:30 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:28:33 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:28:42 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:28:47 lim-laptop nmbd[5736]: [2008/10/29 15:28:47, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Oct 29 15:28:47 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:28:47 lim-laptop nmbd[5736]:    
Oct 29 15:28:47 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP is now a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:28:47 lim-laptop nmbd[5736]:    
Oct 29 15:28:47 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:28:56 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:29:07 lim-laptop avahi-daemon[5203]: Invalid response packet.
Oct 29 15:29:09 lim-laptop last message repeated 3 times
Oct 29 15:29:11 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:29:32 lim-laptop last message repeated 2 times
Oct 29 15:30:40 lim-laptop last message repeated 4 times
Oct 29 15:31:34 lim-laptop last message repeated 5 times
Oct 29 15:32:39 lim-laptop last message repeated 4 times
Oct 29 15:33:41 lim-laptop last message repeated 5 times
Oct 29 15:34:13 lim-laptop last message repeated 3 times
Oct 29 15:34:13 lim-laptop nmbd[5736]: [2008/10/29 15:34:13, 0] nmbd/nmbd_incomingdgrams.c:process_local_master_announce(309) 
Oct 29 15:34:13 lim-laptop nmbd[5736]:   process_local_master_announce: Server BLACKNIGHT at IP 172.19.167.83 is announcing itself as a local master browser for workgroup NUSSTU and we think we are master. Forcing election. 
Oct 29 15:34:13 lim-laptop nmbd[5736]: [2008/10/29 15:34:13, 0] nmbd/nmbd_become_lmb.c:unbecome_local_master_success(149) 
Oct 29 15:34:13 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:34:13 lim-laptop nmbd[5736]:    
Oct 29 15:34:13 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP has stopped being a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:34:13 lim-laptop nmbd[5736]:    
Oct 29 15:34:13 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:34:14 lim-laptop avahi-daemon[5203]: Invalid response packet.
Oct 29 15:34:16 lim-laptop last message repeated 3 times
Oct 29 15:34:22 lim-laptop nmbd[5736]: [2008/10/29 15:34:22, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Oct 29 15:34:22 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:34:22 lim-laptop nmbd[5736]:    
Oct 29 15:34:22 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP is now a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:34:22 lim-laptop nmbd[5736]:    
Oct 29 15:34:22 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:34:33 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:34:56 lim-laptop last message repeated 2 times
Oct 29 15:36:05 lim-laptop last message repeated 5 times
Oct 29 15:37:13 lim-laptop last message repeated 5 times
Oct 29 15:38:11 lim-laptop last message repeated 5 times
Oct 29 15:38:15 lim-laptop nmbd[5736]: [2008/10/29 15:38:15, 0] nmbd/nmbd_incomingdgrams.c:process_local_master_announce(309) 
Oct 29 15:38:15 lim-laptop nmbd[5736]:   process_local_master_announce: Server BLACKNIGHT at IP 172.19.167.83 is announcing itself as a local master browser for workgroup NUSSTU and we think we are master. Forcing election. 
Oct 29 15:38:15 lim-laptop nmbd[5736]: [2008/10/29 15:38:15, 0] nmbd/nmbd_become_lmb.c:unbecome_local_master_success(149) 
Oct 29 15:38:15 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:38:15 lim-laptop nmbd[5736]:    
Oct 29 15:38:15 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP has stopped being a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:38:15 lim-laptop nmbd[5736]:    
Oct 29 15:38:15 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:38:20 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:38:30 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:38:32 lim-laptop nmbd[5736]: [2008/10/29 15:38:32, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Oct 29 15:38:32 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:38:32 lim-laptop nmbd[5736]:    
Oct 29 15:38:32 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP is now a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:38:32 lim-laptop nmbd[5736]:    
Oct 29 15:38:32 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:38:42 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:38:57 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:39:01 lim-laptop /USR/SBIN/CRON[17410]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct 29 15:39:01 lim-laptop /USR/SBIN/CRON[17412]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
Oct 29 15:39:04 lim-laptop nmbd[5736]: [2008/10/29 15:39:04, 0] nmbd/nmbd_incomingdgrams.c:process_local_master_announce(309) 
Oct 29 15:39:04 lim-laptop nmbd[5736]:   process_local_master_announce: Server BLACKNIGHT at IP 172.19.167.83 is announcing itself as a local master browser for workgroup NUSSTU and we think we are master. Forcing election. 
Oct 29 15:39:04 lim-laptop nmbd[5736]: [2008/10/29 15:39:04, 0] nmbd/nmbd_become_lmb.c:unbecome_local_master_success(149) 
Oct 29 15:39:04 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:39:04 lim-laptop nmbd[5736]:    
Oct 29 15:39:04 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP has stopped being a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:39:04 lim-laptop nmbd[5736]:    
Oct 29 15:39:04 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:39:17 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:39:21 lim-laptop avahi-daemon[5203]: Invalid response packet.
Oct 29 15:39:22 lim-laptop avahi-daemon[5203]: Invalid response packet.
Oct 29 15:39:22 lim-laptop nmbd[5736]: [2008/10/29 15:39:22, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Oct 29 15:39:22 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:39:22 lim-laptop nmbd[5736]:    
Oct 29 15:39:22 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP is now a local master browser for workgroup NUSSTU on subnet 172.19.163.224 
Oct 29 15:39:22 lim-laptop nmbd[5736]:    
Oct 29 15:39:22 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:39:22 lim-laptop avahi-daemon[5203]: Invalid response packet.
Oct 29 15:39:23 lim-laptop avahi-daemon[5203]: Invalid response packet.
Oct 29 15:39:30 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.155.236 port 67
Oct 29 15:39:51 lim-laptop last message repeated 2 times
Oct 29 15:40:00 lim-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct 29 15:40:35 lim-laptop last message repeated 3 times
Oct 29 15:41:42 lim-laptop last message repeated 5 times
Oct 29 15:42:29 lim-laptop last message repeated 3 times
Oct 29 15:43:39 lim-laptop last message repeated 5 times
Oct 29 15:43:40 lim-laptop avahi-daemon[5203]: Withdrawing address record for 172.19.163.224 on eth0.
Oct 29 15:43:40 lim-laptop avahi-daemon[5203]: Leaving mDNS multicast group on interface eth0.IPv4 with address 172.19.163.224.
Oct 29 15:43:40 lim-laptop avahi-daemon[5203]: Interface eth0.IPv4 no longer relevant for mDNS.
Oct 29 15:43:40 lim-laptop avahi-autoipd(eth0)[17717]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Oct 29 15:43:40 lim-laptop avahi-autoipd(eth0)[17717]: Successfully called chroot().
Oct 29 15:43:40 lim-laptop avahi-autoipd(eth0)[17717]: Successfully dropped root privileges.
Oct 29 15:43:40 lim-laptop avahi-autoipd(eth0)[17717]: fopen() failed: Permission denied
Oct 29 15:43:40 lim-laptop avahi-autoipd(eth0)[17717]: Starting with address 169.254.8.84
Oct 29 15:43:45 lim-laptop avahi-autoipd(eth0)[17717]: Callout BIND, address 169.254.8.84 on interface eth0
Oct 29 15:43:45 lim-laptop avahi-daemon[5203]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.84.
Oct 29 15:43:45 lim-laptop avahi-daemon[5203]: New relevant interface eth0.IPv4 for mDNS.
Oct 29 15:43:45 lim-laptop avahi-daemon[5203]: Registering new address record for 169.254.8.84 on eth0.IPv4.
Oct 29 15:43:49 lim-laptop avahi-autoipd(eth0)[17717]: Successfully claimed IP address 169.254.8.84
Oct 29 15:43:49 lim-laptop avahi-autoipd(eth0)[17717]: fopen() failed: Permission denied
Oct 29 15:43:49 lim-laptop NetworkManager: <information>^IDHCP daemon state is now 10 (unknown) for interface eth0 
Oct 29 15:43:49 lim-laptop avahi-autoipd(eth0)[17717]: Got SIGTERM, quitting.
Oct 29 15:43:49 lim-laptop avahi-autoipd(eth0)[17717]: Callout STOP, address 169.254.8.84 on interface eth0
Oct 29 15:43:49 lim-laptop avahi-daemon[5203]: Withdrawing address record for 169.254.8.84 on eth0.
Oct 29 15:43:49 lim-laptop avahi-daemon[5203]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.8.84.
Oct 29 15:43:49 lim-laptop avahi-daemon[5203]: Interface eth0.IPv4 no longer relevant for mDNS.
Oct 29 15:43:49 lim-laptop avahi-autoipd(eth0)[17718]: client: RTNETLINK answers: No such process
Oct 29 15:43:50 lim-laptop NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Oct 29 15:43:50 lim-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Oct 29 15:43:58 lim-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Oct 29 15:44:13 lim-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Oct 29 15:44:15 lim-laptop dhclient: DHCPOFFER from 172.19.160.2
Oct 29 15:44:15 lim-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct 29 15:44:19 lim-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct 29 15:44:21 lim-laptop dhclient: DHCPACK from 172.19.160.2
Oct 29 15:44:21 lim-laptop avahi-daemon[5203]: Joining mDNS multicast group on interface eth0.IPv4 with address 172.19.168.14.
Oct 29 15:44:21 lim-laptop avahi-daemon[5203]: New relevant interface eth0.IPv4 for mDNS.
Oct 29 15:44:21 lim-laptop avahi-daemon[5203]: Registering new address record for 172.19.168.14 on eth0.IPv4.
Oct 29 15:44:21 lim-laptop avahi-daemon[5203]: Withdrawing address record for 172.19.168.14 on eth0.
Oct 29 15:44:21 lim-laptop avahi-daemon[5203]: Leaving mDNS multicast group on interface eth0.IPv4 with address 172.19.168.14.
Oct 29 15:44:21 lim-laptop avahi-daemon[5203]: Interface eth0.IPv4 no longer relevant for mDNS.
Oct 29 15:44:21 lim-laptop avahi-daemon[5203]: Joining mDNS multicast group on interface eth0.IPv4 with address 172.19.168.14.
Oct 29 15:44:21 lim-laptop avahi-daemon[5203]: New relevant interface eth0.IPv4 for mDNS.
Oct 29 15:44:21 lim-laptop avahi-daemon[5203]: Registering new address record for 172.19.168.14 on eth0.IPv4.
Oct 29 15:44:21 lim-laptop NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Oct 29 15:44:21 lim-laptop dhclient: bound to 172.19.168.14 -- renewal in 752 seconds.
Oct 29 15:44:28 lim-laptop avahi-daemon[5203]: Invalid response packet.
Oct 29 15:44:30 lim-laptop last message repeated 3 times
Oct 29 15:46:49 lim-laptop nmbd[5736]: [2008/10/29 15:46:49, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Oct 29 15:46:49 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:46:49 lim-laptop nmbd[5736]:    
Oct 29 15:46:49 lim-laptop nmbd[5736]:   Samba name server LIM-LAPTOP is now a local master browser for workgroup NUSSTU on subnet 172.19.168.14 
Oct 29 15:46:49 lim-laptop nmbd[5736]:    
Oct 29 15:46:49 lim-laptop nmbd[5736]:   ***** 
Oct 29 15:49:35 lim-laptop avahi-daemon[5203]: Invalid response packet.
Oct 29 15:49:37 lim-laptop last message repeated 3 times
Oct 29 15:54:42 lim-laptop avahi-daemon[5203]: Invalid response packet.
Oct 29 15:54:44 lim-laptop last message repeated 3 times
Oct 29 15:56:53 lim-laptop dhclient: DHCPREQUEST on eth0 to 137.132.5.246 port 67
Oct 29 15:56:55 lim-laptop dhclient: DHCPACK from 137.132.5.246
Oct 29 15:56:55 lim-laptop dhclient: bound to 172.19.168.14 -- renewal in 779 seconds.
Oct 29 15:56:55 lim-laptop NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Oct 29 15:59:49 lim-laptop avahi-daemon[5203]: Invalid response packet.
Oct 29 15:59:51 lim-laptop last message repeated 3 times
Oct 29 16:04:56 lim-laptop avahi-daemon[5203]: Invalid response packet.
Oct 29 16:04:58 lim-laptop last message repeated 3 times
Oct 29 16:08:12 lim-laptop syslogd 1.4.1#20ubuntu4: restart.
Oct 29 16:08:12 lim-laptop kernel: Inspecting /boot/System.map-2.6.20-17-generic
Oct 29 16:08:12 lim-laptop kernel: Loaded 24981 symbols from /boot/System.map-2.6.20-17-generic.
Oct 29 16:08:12 lim-laptop kernel: Symbols match kernel version 2.6.20.
Oct 29 16:08:12 lim-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] Linux version 2.6.20-17-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed Aug 20 16:47:34 UTC 2008 (Ubuntu 2.6.20-17.39-generic)
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] sanitize start
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] sanitize end
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003f5d3400 end: 000000003f6d3400 type: 1
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] copy_e820_map() type is E820_RAM
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] copy_e820_map() start: 000000003f6d3400 size: 000000000092cc00 end: 0000000040000000 type: 2
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] copy_e820_map() start: 00000000f0000000 size: 0000000004007000 end: 00000000f4007000 type: 2
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] copy_e820_map() start: 00000000f4008000 size: 0000000000004000 end: 00000000f400c000 type: 2
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] copy_e820_map() start: 00000000fed20000 size: 0000000000080000 end: 00000000feda0000 type: 2
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000010000 end: 00000000fee10000 type: 2
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6d3400 (usable)
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]  BIOS-e820: 000000003f6d3400 - 0000000040000000 (reserved)
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] 118MB HIGHMEM available.
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] 896MB LOWMEM available.
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 259795) 0 entries of 256 used
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] Zone PFN ranges:
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]   DMA             0 ->     4096
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]   HighMem    229376 ->   259795
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]     0:        0 ->   259795
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] On node 0 totalpages: 259795
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]   HighMem zone: 237 pages used for memmap
Oct 29 16:08:12 lim-laptop kernel: [    0.000000]   HighMem zone: 30182 pages, LIFO batch:7
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] DMI 2.4 present.
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fc1d0
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: RSDT (v001 DELL    M07     0x27d70205 ASL  0x00000061) @ 0x3f6d3a0f
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: FADT (v001 DELL    M07     0x27d70205 ASL  0x00000061) @ 0x3f6d4800
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: HPET (v001 DELL    M07     0x00000001 ASL  0x00000061) @ 0x3f6d4f00
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: MADT (v001 DELL    M07     0x27d70205 ASL  0x00000047) @ 0x3f6d5000
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: MCFG (v016 DELL    M07     0x27d70205 ASL  0x00000061) @ 0x3f6d4fc0
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: SLIC (v001 DELL    M07     0x27d70205 ASL  0x00000061) @ 0x3f6d509c
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: BOOT (v001 DELL    M07     0x27d70205 ASL  0x00000061) @ 0x3f6d4bc0
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x3f6d3a4f
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 INTL 0x20050624) @ 0x00000000
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] Processor #0 6:15 APIC version 20
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] Processor #1 6:15 APIC version 20
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
Oct 29 16:08:12 lim-laptop kernel: [    0.000000] Detected 1662.658 MHz processor.
Oct 29 16:08:12 lim-laptop kernel: [   41.247012] Built 1 zonelists.  Total pages: 257766
Oct 29 16:08:12 lim-laptop kernel: [   41.247015] Kernel command line: root=UUID=cd272330-334c-4d93-9ba2-4bdc092e7254 ro splash vga=791 acpi_osi=!Linux
Oct 29 16:08:12 lim-laptop kernel: [   41.247062] ACPI: _OSI additional string ignored -- !Linux
Oct 29 16:08:12 lim-laptop kernel: [   41.247181] mapped APIC to ffffd000 (fee00000)
Oct 29 16:08:12 lim-laptop kernel: [   41.247183] mapped IOAPIC to ffffc000 (fec00000)
Oct 29 16:08:12 lim-laptop kernel: [   41.247186] Enabling fast FPU save and restore... done.
Oct 29 16:08:12 lim-laptop kernel: [   41.247189] Enabling unmasked SIMD FPU exception support... done.
Oct 29 16:08:12 lim-laptop kernel: [   41.247196] Initializing CPU#0
Oct 29 16:08:12 lim-laptop kernel: [   41.247260] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 29 16:08:12 lim-laptop kernel: [   41.247300] Console: colour dummy device 80x25
Oct 29 16:08:12 lim-laptop kernel: [   41.247653] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 29 16:08:12 lim-laptop kernel: [   41.247952] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 29 16:08:12 lim-laptop kernel: [   41.268474] Memory: 1018984k/1039180k available (1993k kernel code, 19424k reserved, 900k data, 328k init, 121676k highmem)
Oct 29 16:08:12 lim-laptop kernel: [   41.268487] virtual kernel memory layout:
Oct 29 16:08:12 lim-laptop kernel: [   41.268488]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
Oct 29 16:08:12 lim-laptop kernel: [   41.268490]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 29 16:08:12 lim-laptop kernel: [   41.268491]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Oct 29 16:08:12 lim-laptop kernel: [   41.268492]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Oct 29 16:08:12 lim-laptop kernel: [   41.268493]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
Oct 29 16:08:12 lim-laptop kernel: [   41.268494]       .data : 0xc02f2699 - 0xc03d36d4   ( 900 kB)
Oct 29 16:08:12 lim-laptop kernel: [   41.268495]       .text : 0xc0100000 - 0xc02f2699   (1993 kB)
Oct 29 16:08:12 lim-laptop kernel: [   41.268508] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 29 16:08:12 lim-laptop kernel: [   41.268657] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Oct 29 16:08:12 lim-laptop kernel: [   41.268665] hpet0: 3 64-bit timers, 14318180 Hz
Oct 29 16:08:12 lim-laptop kernel: [   41.269670] Using HPET for base-timer
Oct 29 16:08:12 lim-laptop kernel: [   41.348540] Calibrating delay using timer specific routine.. 3328.70 BogoMIPS (lpj=6657414)
Oct 29 16:08:12 lim-laptop kernel: [   41.348579] Security Framework v1.0.0 initialized
Oct 29 16:08:12 lim-laptop kernel: [   41.348585] SELinux:  Disabled at boot.
Oct 29 16:08:12 lim-laptop kernel: [   41.348599] Mount-cache hash table entries: 512
Oct 29 16:08:12 lim-laptop kernel: [   41.348718] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
Oct 29 16:08:12 lim-laptop kernel: [   41.348726] monitor/mwait feature present.
Oct 29 16:08:12 lim-laptop kernel: [   41.348730] using mwait in idle threads.
Oct 29 16:08:12 lim-laptop kernel: [   41.348735] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 29 16:08:12 lim-laptop kernel: [   41.348738] CPU: L2 cache: 2048K
Oct 29 16:08:12 lim-laptop kernel: [   41.348742] CPU: Physical Processor ID: 0
Oct 29 16:08:12 lim-laptop kernel: [   41.348745] CPU: Processor Core ID: 0
Oct 29 16:08:12 lim-laptop kernel: [   41.348747] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
Oct 29 16:08:12 lim-laptop kernel: [   41.348756] Compat vDSO mapped to ffffe000.
Oct 29 16:08:12 lim-laptop kernel: [   41.348760] Remapping vsyscall page to ffffe000
Oct 29 16:08:12 lim-laptop kernel: [   41.348772] Checking 'hlt' instruction... OK.
Oct 29 16:08:12 lim-laptop kernel: [   41.364604] SMP alternatives: switching to UP code
Oct 29 16:08:12 lim-laptop kernel: [   41.364918] Early unpacking initramfs... done
Oct 29 16:08:12 lim-laptop kernel: [   41.679006] ACPI: Core revision 20060707
Oct 29 16:08:12 lim-laptop kernel: [   41.695454] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Oct 29 16:08:12 lim-laptop kernel: [   41.697995] CPU0: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 02
Oct 29 16:08:12 lim-laptop kernel: [   41.698016] SMP alternatives: switching to SMP code
Oct 29 16:08:12 lim-laptop kernel: [   41.698093] Booting processor 1/1 eip 3000
Oct 29 16:08:12 lim-laptop kernel: [   43.578750] Initializing CPU#1
Oct 29 16:08:12 lim-laptop kernel: [   43.659512] Calibrating delay using timer specific routine.. 3325.10 BogoMIPS (lpj=6650202)
Oct 29 16:08:12 lim-laptop kernel: [   43.659518] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
Oct 29 16:08:12 lim-laptop kernel: [   43.659523] monitor/mwait feature present.
Oct 29 16:08:12 lim-laptop kernel: [   43.659526] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 29 16:08:12 lim-laptop kernel: [   43.659528] CPU: L2 cache: 2048K
Oct 29 16:08:12 lim-laptop kernel: [   43.659530] CPU: Physical Processor ID: 0
Oct 29 16:08:12 lim-laptop kernel: [   43.659531] CPU: Processor Core ID: 1
Oct 29 16:08:12 lim-laptop kernel: [   43.659533] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
Oct 29 16:08:12 lim-laptop kernel: [   41.792395] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 02
Oct 29 16:08:12 lim-laptop kernel: [   41.792428] Total of 2 processors activated (6653.80 BogoMIPS).
Oct 29 16:08:12 lim-laptop kernel: [   41.792628] ENABLING IO-APIC IRQs
Oct 29 16:08:12 lim-laptop kernel: [   41.792824] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 29 16:08:12 lim-laptop kernel: [   41.939639] checking TSC synchronization across 2 CPUs: 
Oct 29 16:08:12 lim-laptop kernel: [    0.000002] CPU#0 had -935532 usecs TSC skew, fixed it up.
Oct 29 16:08:12 lim-laptop kernel: [    0.000006] CPU#1 had 935532 usecs TSC skew, fixed it up.
Oct 29 16:08:12 lim-laptop kernel: [    0.003992] Brought up 2 CPUs
Oct 29 16:08:12 lim-laptop kernel: [    0.162266] migration_cost=67
Oct 29 16:08:12 lim-laptop kernel: [    0.162533] Booting paravirtualized kernel on bare hardware
Oct 29 16:08:12 lim-laptop kernel: [    0.162623] Time: 16:07:42  Date: 09/29/108
Oct 29 16:08:12 lim-laptop kernel: [    0.162652] NET: Registered protocol family 16
Oct 29 16:08:12 lim-laptop kernel: [    0.162733] EISA bus registered
Oct 29 16:08:12 lim-laptop kernel: [    0.162738] ACPI: bus type pci registered
Oct 29 16:08:12 lim-laptop kernel: [    0.191381] PCI: PCI BIOS revision 2.10 entry at 0xfb336, last bus=14
Oct 29 16:08:12 lim-laptop kernel: [    0.191384] PCI: Using configuration type 1
Oct 29 16:08:12 lim-laptop kernel: [    0.191387] Setting up standard PCI resources
Oct 29 16:08:12 lim-laptop kernel: [    0.218613] ACPI: Interpreter enabled
Oct 29 16:08:12 lim-laptop kernel: [    0.218617] ACPI: Using IOAPIC for interrupt routing
Oct 29 16:08:12 lim-laptop kernel: [    0.219526] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 29 16:08:12 lim-laptop kernel: [    0.219537] PCI: Probing PCI hardware (bus 00)
Oct 29 16:08:12 lim-laptop kernel: [    0.219735] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Oct 29 16:08:12 lim-laptop kernel: [    0.232794] Boot video device is 0000:00:02.0
Oct 29 16:08:12 lim-laptop kernel: [    0.233473] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Oct 29 16:08:12 lim-laptop kernel: [    0.233480] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Oct 29 16:08:12 lim-laptop kernel: [    0.234712] PCI: Transparent bridge - 0000:00:1e.0
Oct 29 16:08:12 lim-laptop kernel: [    0.234793] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 29 16:08:12 lim-laptop kernel: [    0.256181] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Oct 29 16:08:12 lim-laptop kernel: [    0.256438] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
Oct 29 16:08:12 lim-laptop kernel: [    0.256691] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Oct 29 16:08:12 lim-laptop kernel: [    0.256949] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
Oct 29 16:08:12 lim-laptop kernel: [    0.257212] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Oct 29 16:08:12 lim-laptop kernel: [    0.257470] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Oct 29 16:08:12 lim-laptop kernel: [    0.257731] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Oct 29 16:08:12 lim-laptop kernel: [    0.257992] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Oct 29 16:08:12 lim-laptop kernel: [    0.258777] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Oct 29 16:08:12 lim-laptop kernel: [    0.259034] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Oct 29 16:08:12 lim-laptop kernel: [    0.259274] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Oct 29 16:08:12 lim-laptop kernel: [    0.259601] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Oct 29 16:08:12 lim-laptop kernel: [    0.260023] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 29 16:08:12 lim-laptop kernel: [    0.260035] pnp: PnP ACPI init
Oct 29 16:08:12 lim-laptop kernel: [    0.292282] pnp: PnP ACPI: found 12 devices
Oct 29 16:08:12 lim-laptop kernel: [    0.292287] PnPBIOS: Disabled by ACPI PNP
Oct 29 16:08:12 lim-laptop kernel: [    0.292331] PCI: Using ACPI for IRQ routing
Oct 29 16:08:12 lim-laptop kernel: [    0.292335] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 29 16:08:12 lim-laptop kernel: [    0.344648] NET: Registered protocol family 8
Oct 29 16:08:12 lim-laptop kernel: [    0.344652] NET: Registered protocol family 20
Oct 29 16:08:12 lim-laptop kernel: [    0.362862] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
Oct 29 16:08:12 lim-laptop kernel: [    0.362868] pnp: 00:02: ioport range 0x1000-0x1005 could not be reserved
Oct 29 16:08:12 lim-laptop kernel: [    0.362873] pnp: 00:02: ioport range 0x1008-0x100f could not be reserved
Oct 29 16:08:12 lim-laptop kernel: [    0.362880] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
Oct 29 16:08:12 lim-laptop kernel: [    0.362884] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
Oct 29 16:08:12 lim-laptop kernel: [    0.362888] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
Oct 29 16:08:12 lim-laptop kernel: [    0.362892] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
Oct 29 16:08:12 lim-laptop kernel: [    0.362896] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
Oct 29 16:08:12 lim-laptop kernel: [    0.362900] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
Oct 29 16:08:12 lim-laptop kernel: [    0.362909] pnp: 00:08: ioport range 0xc80-0xcff could not be reserved
Oct 29 16:08:12 lim-laptop kernel: [    0.362912] pnp: 00:08: ioport range 0x910-0x91f has been reserved
Oct 29 16:08:12 lim-laptop kernel: [    0.362916] pnp: 00:08: ioport range 0x920-0x92f has been reserved
Oct 29 16:08:12 lim-laptop kernel: [    0.362920] pnp: 00:08: ioport range 0xcb0-0xcbf has been reserved
Oct 29 16:08:12 lim-laptop kernel: [    0.362924] pnp: 00:08: ioport range 0x930-0x97f has been reserved
Oct 29 16:08:12 lim-laptop kernel: [    0.363219] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
Oct 29 16:08:12 lim-laptop kernel: [    0.363225] PCI: Bridge: 0000:00:1c.0
Oct 29 16:08:12 lim-laptop kernel: [    0.363227]   IO window: disabled.
Oct 29 16:08:12 lim-laptop kernel: [    0.363234]   MEM window: disabled.
Oct 29 16:08:12 lim-laptop kernel: [    0.363239]   PREFETCH window: disabled.
Oct 29 16:08:12 lim-laptop kernel: [    0.363246] PCI: Bridge: 0000:00:1c.1
Oct 29 16:08:12 lim-laptop kernel: [    0.363249]   IO window: disabled.
Oct 29 16:08:12 lim-laptop kernel: [    0.363256]   MEM window: efd00000-efdfffff
Oct 29 16:08:12 lim-laptop kernel: [    0.363262]   PREFETCH window: disabled.
Oct 29 16:08:12 lim-laptop kernel: [    0.363269] PCI: Bridge: 0000:00:1c.3
Oct 29 16:08:12 lim-laptop kernel: [    0.363273]   IO window: d000-dfff
Oct 29 16:08:12 lim-laptop kernel: [    0.363280]   MEM window: efa00000-efcfffff
Oct 29 16:08:12 lim-laptop kernel: [    0.363287]   PREFETCH window: e0000000-e01fffff
Oct 29 16:08:12 lim-laptop kernel: [    0.363294] PCI: Bridge: 0000:00:1e.0
Oct 29 16:08:12 lim-laptop kernel: [    0.363296]   IO window: disabled.
Oct 29 16:08:12 lim-laptop kernel: [    0.363303]   MEM window: ef900000-ef9fffff
Oct 29 16:08:12 lim-laptop kernel: [    0.363309]   PREFETCH window: disabled.
Oct 29 16:08:12 lim-laptop kernel: [    0.363341] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 29 16:08:12 lim-laptop kernel: [    0.363350] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Oct 29 16:08:12 lim-laptop kernel: [    0.363375] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Oct 29 16:08:12 lim-laptop kernel: [    0.363384] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Oct 29 16:08:12 lim-laptop kernel: [    0.363408] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
Oct 29 16:08:12 lim-laptop kernel: [    0.363417] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Oct 29 16:08:12 lim-laptop kernel: [    0.363438] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Oct 29 16:08:12 lim-laptop kernel: [    0.363463] NET: Registered protocol family 2
Oct 29 16:08:12 lim-laptop kernel: [    0.403418] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 29 16:08:12 lim-laptop kernel: [    0.403520] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 29 16:08:12 lim-laptop kernel: [    0.403994] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 29 16:08:12 lim-laptop kernel: [    0.404247] TCP: Hash tables configured (established 131072 bind 65536)
Oct 29 16:08:12 lim-laptop kernel: [    0.404251] TCP reno registered
Oct 29 16:08:12 lim-laptop kernel: [    0.419470] checking if image is initramfs... it is
Oct 29 16:08:12 lim-laptop kernel: [    1.039464] Freeing initrd memory: 6761k freed
Oct 29 16:08:12 lim-laptop kernel: [    1.039646] Simple Boot Flag at 0x79 set to 0x1
Oct 29 16:08:12 lim-laptop kernel: [    1.040106] audit: initializing netlink socket (disabled)
Oct 29 16:08:12 lim-laptop kernel: [    1.040125] audit(1225296462.796:1): initialized
Oct 29 16:08:12 lim-laptop kernel: [    1.040226] highmem bounce pool size: 64 pages
Oct 29 16:08:12 lim-laptop kernel: [    1.040315] VFS: Disk quotas dquot_6.5.1
Oct 29 16:08:12 lim-laptop kernel: [    1.040336] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 29 16:08:12 lim-laptop kernel: [    1.040387] io scheduler noop registered
Oct 29 16:08:12 lim-laptop kernel: [    1.040391] io scheduler anticipatory registered
Oct 29 16:08:12 lim-laptop kernel: [    1.040394] io scheduler deadline registered
Oct 29 16:08:12 lim-laptop kernel: [    1.040407] io scheduler cfq registered (default)
Oct 29 16:08:12 lim-laptop kernel: [    1.040663] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Oct 29 16:08:12 lim-laptop kernel: [    1.040724] assign_interrupt_mode Found MSI capability
Oct 29 16:08:12 lim-laptop kernel: [    1.040729] Allocate Port Service[0000:00:1c.0:pcie00]
Oct 29 16:08:12 lim-laptop kernel: [    1.040762] Allocate Port Service[0000:00:1c.0:pcie02]
Oct 29 16:08:12 lim-laptop kernel: [    1.040892] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Oct 29 16:08:12 lim-laptop kernel: [    1.040952] assign_interrupt_mode Found MSI capability
Oct 29 16:08:12 lim-laptop kernel: [    1.040956] Allocate Port Service[0000:00:1c.1:pcie00]
Oct 29 16:08:12 lim-laptop kernel: [    1.040988] Allocate Port Service[0000:00:1c.1:pcie02]
Oct 29 16:08:12 lim-laptop kernel: [    1.041115] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Oct 29 16:08:12 lim-laptop kernel: [    1.041175] assign_interrupt_mode Found MSI capability
Oct 29 16:08:12 lim-laptop kernel: [    1.041179] Allocate Port Service[0000:00:1c.3:pcie00]
Oct 29 16:08:12 lim-laptop kernel: [    1.041211] Allocate Port Service[0000:00:1c.3:pcie02]
Oct 29 16:08:12 lim-laptop kernel: [    1.041397] isapnp: Scanning for PnP cards...
Oct 29 16:08:12 lim-laptop kernel: [    1.394890] isapnp: No Plug & Play device found
Oct 29 16:08:12 lim-laptop kernel: [    1.415484] Real Time Clock Driver v1.12ac
Oct 29 16:08:12 lim-laptop kernel: [    1.415549] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 29 16:08:12 lim-laptop kernel: [    1.416139] mice: PS/2 mouse device common for all mice
Oct 29 16:08:12 lim-laptop kernel: [    1.416693] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 29 16:08:12 lim-laptop kernel: [    1.416914] input: Macintosh mouse button emulation as /class/input/input0
Oct 29 16:08:12 lim-laptop kernel: [    1.416950] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Oct 29 16:08:12 lim-laptop kernel: [    1.416955] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Oct 29 16:08:12 lim-laptop kernel: [    1.417205] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 29 16:08:12 lim-laptop kernel: [    1.420023] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 29 16:08:12 lim-laptop kernel: [    1.420028] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 29 16:08:12 lim-laptop kernel: [    1.420140] EISA: Probing bus 0 at eisa.0
Oct 29 16:08:12 lim-laptop kernel: [    1.420151] Cannot allocate resource for EISA slot 1
Oct 29 16:08:12 lim-laptop kernel: [    1.420184] EISA: Detected 0 cards.
Oct 29 16:08:12 lim-laptop kernel: [    1.450314] TCP cubic registered
Oct 29 16:08:12 lim-laptop kernel: [    1.450325] NET: Registered protocol family 1
Oct 29 16:08:12 lim-laptop kernel: [    1.450351] Starting balanced_irq
Oct 29 16:08:12 lim-laptop kernel: [    1.450358] Using IPI No-Shortcut mode
Oct 29 16:08:12 lim-laptop kernel: [    1.450445] input: AT Translated Set 2 keyboard as /class/input/input1
Oct 29 16:08:12 lim-laptop kernel: [    1.450707] ACPI: (supports S0 S3 S4 S5)
Oct 29 16:08:12 lim-laptop kernel: [    1.450754]   Magic number: 12:964:136
Oct 29 16:08:12 lim-laptop kernel: [    1.451006] Freeing unused kernel memory: 328k freed
Oct 29 16:08:12 lim-laptop kernel: [    1.453781] Time: tsc clocksource has been installed.
Oct 29 16:08:12 lim-laptop kernel: [    1.536158] vesafb: framebuffer at 0xd0000000, mapped to 0xf8880000, using 3072k, total 7872k
Oct 29 16:08:12 lim-laptop kernel: [    1.536169] vesafb: mode is 1024x768x16, linelength=2048, pages=4
Oct 29 16:08:12 lim-laptop kernel: [    1.536172] vesafb: protected mode interface info at 00ff:44f0
Oct 29 16:08:12 lim-laptop kernel: [    1.536175] vesafb: scrolling: redraw
Oct 29 16:08:12 lim-laptop kernel: [    1.536179] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
Oct 29 16:08:12 lim-laptop kernel: [    1.550884] Console: switching to colour frame buffer device 128x48
Oct 29 16:08:12 lim-laptop kernel: [    1.565638] fb0: VESA VGA frame buffer device
Oct 29 16:08:12 lim-laptop kernel: [    2.705974] Capability LSM initialized
Oct 29 16:08:12 lim-laptop kernel: [    2.747000] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
Oct 29 16:08:12 lim-laptop kernel: [    2.747177] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
Oct 29 16:08:12 lim-laptop kernel: [    2.747380] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Oct 29 16:08:12 lim-laptop kernel: [    2.747386] ACPI: Processor [CPU0] (supports 8 throttling states)
Oct 29 16:08:12 lim-laptop kernel: [    2.747833] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
Oct 29 16:08:12 lim-laptop kernel: [    2.747997] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
Oct 29 16:08:12 lim-laptop kernel: [    2.748241] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Oct 29 16:08:12 lim-laptop kernel: [    2.748246] ACPI: Processor [CPU1] (supports 8 throttling states)
Oct 29 16:08:12 lim-laptop kernel: [    3.328000] ACPI: Thermal Zone [THM] (57 C)
Oct 29 16:08:12 lim-laptop kernel: [    3.332000] Time: hpet clocksource has been installed.
Oct 29 16:08:12 lim-laptop kernel: [    3.708000] usbcore: registered new interface driver usbfs
Oct 29 16:08:12 lim-laptop kernel: [    3.708000] usbcore: registered new interface driver hub
Oct 29 16:08:12 lim-laptop kernel: [    3.708000] usbcore: registered new device driver usb
Oct 29 16:08:12 lim-laptop kernel: [    3.708000] USB Universal Host Controller Interface driver v3.0
Oct 29 16:08:12 lim-laptop kernel: [    3.708000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
Oct 29 16:08:12 lim-laptop kernel: [    3.708000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Oct 29 16:08:12 lim-laptop kernel: [    3.708000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 29 16:08:12 lim-laptop kernel: [    3.708000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Oct 29 16:08:12 lim-laptop kernel: [    3.708000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000bf80
Oct 29 16:08:12 lim-laptop kernel: [    3.708000] usb usb1: configuration #1 chosen from 1 choice
Oct 29 16:08:12 lim-laptop kernel: [    3.708000] hub 1-0:1.0: USB hub found
Oct 29 16:08:12 lim-laptop kernel: [    3.708000] hub 1-0:1.0: 2 ports detected
Oct 29 16:08:12 lim-laptop kernel: [    3.748000] SCSI subsystem initialized
Oct 29 16:08:12 lim-laptop kernel: [    3.752000] libata version 2.20 loaded.
Oct 29 16:08:12 lim-laptop kernel: [    3.804000] ieee1394: Initialized config rom entry `ip1394'
Oct 29 16:08:12 lim-laptop kernel: [    3.812000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
Oct 29 16:08:12 lim-laptop kernel: [    3.812000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Oct 29 16:08:12 lim-laptop kernel: [    3.812000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Oct 29 16:08:12 lim-laptop kernel: [    3.812000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Oct 29 16:08:12 lim-laptop kernel: [    3.812000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000bf60
Oct 29 16:08:12 lim-laptop kernel: [    3.812000] usb usb2: configuration #1 chosen from 1 choice
Oct 29 16:08:12 lim-laptop kernel: [    3.812000] hub 2-0:1.0: USB hub found
Oct 29 16:08:12 lim-laptop kernel: [    3.812000] hub 2-0:1.0: 2 ports detected
Oct 29 16:08:12 lim-laptop kernel: [    3.916000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
Oct 29 16:08:12 lim-laptop kernel: [    3.916000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Oct 29 16:08:12 lim-laptop kernel: [    3.916000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Oct 29 16:08:12 lim-laptop kernel: [    3.916000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Oct 29 16:08:12 lim-laptop kernel: [    3.916000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000bf40
Oct 29 16:08:12 lim-laptop kernel: [    3.916000] usb usb3: configuration #1 chosen from 1 choice
Oct 29 16:08:12 lim-laptop kernel: [    3.916000] hub 3-0:1.0: USB hub found
Oct 29 16:08:12 lim-laptop kernel: [    3.916000] hub 3-0:1.0: 2 ports detected
Oct 29 16:08:12 lim-laptop kernel: [    4.020000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 22
Oct 29 16:08:12 lim-laptop kernel: [    4.020000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Oct 29 16:08:12 lim-laptop kernel: [    4.020000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Oct 29 16:08:12 lim-laptop kernel: [    4.020000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Oct 29 16:08:12 lim-laptop kernel: [    4.020000] uhci_hcd 0000:00:1d.3: irq 22, io base 0x0000bf20
Oct 29 16:08:12 lim-laptop kernel: [    4.020000] usb usb4: configuration #1 chosen from 1 choice
Oct 29 16:08:12 lim-laptop kernel: [    4.020000] hub 4-0:1.0: USB hub found
Oct 29 16:08:12 lim-laptop kernel: [    4.020000] hub 4-0:1.0: 2 ports detected
Oct 29 16:08:12 lim-laptop kernel: [    4.124000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
Oct 29 16:08:12 lim-laptop kernel: [    4.124000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Oct 29 16:08:12 lim-laptop kernel: [    4.124000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 29 16:08:12 lim-laptop kernel: [    4.124000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Oct 29 16:08:12 lim-laptop kernel: [    4.124000] ehci_hcd 0000:00:1d.7: debug port 1
Oct 29 16:08:12 lim-laptop kernel: [    4.124000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Oct 29 16:08:12 lim-laptop kernel: [    4.124000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa80000
Oct 29 16:08:12 lim-laptop kernel: [    4.128000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 29 16:08:12 lim-laptop kernel: [    4.128000] usb usb5: configuration #1 chosen from 1 choice
Oct 29 16:08:12 lim-laptop kernel: [    4.128000] hub 5-0:1.0: USB hub found
Oct 29 16:08:12 lim-laptop kernel: [    4.128000] hub 5-0:1.0: 8 ports detected
Oct 29 16:08:12 lim-laptop kernel: [    4.156000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Oct 29 16:08:12 lim-laptop kernel: [    4.232000] b44.c:v1.01 (Jun 16, 2006)
Oct 29 16:08:12 lim-laptop kernel: [    4.232000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Oct 29 16:08:12 lim-laptop kernel: [    4.232000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:15:c5:78:1d:f8
Oct 29 16:08:12 lim-laptop kernel: [    4.236000] ata_piix 0000:00:1f.2: version 2.10ac1
Oct 29 16:08:12 lim-laptop kernel: [    4.236000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Oct 29 16:08:12 lim-laptop kernel: [    4.236000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
Oct 29 16:08:12 lim-laptop kernel: [    4.236000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Oct 29 16:08:12 lim-laptop kernel: [    4.236000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Oct 29 16:08:12 lim-laptop kernel: [    4.236000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Oct 29 16:08:12 lim-laptop kernel: [    4.236000] scsi0 : ata_piix
Oct 29 16:08:12 lim-laptop kernel: [    4.400000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Oct 29 16:08:12 lim-laptop kernel: [    4.400000] ata1.00: ATA-8: FUJITSU MHW2080BH, 00850012, max UDMA/100
Oct 29 16:08:12 lim-laptop kernel: [    4.400000] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
Oct 29 16:08:12 lim-laptop kernel: [    4.408000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Oct 29 16:08:12 lim-laptop kernel: [    4.408000] ata1.00: configured for UDMA/100
Oct 29 16:08:12 lim-laptop kernel: [    4.408000] scsi1 : ata_piix
Oct 29 16:08:12 lim-laptop kernel: [    4.728000] ata2.00: ATAPI, max UDMA/33
Oct 29 16:08:12 lim-laptop kernel: [    4.892000] ata2.00: configured for UDMA/33
Oct 29 16:08:12 lim-laptop kernel: [    4.892000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHW2080B 0085 PQ: 0 ANSI: 5
Oct 29 16:08:12 lim-laptop kernel: [    4.896000] scsi 1:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-5540A 102C PQ: 0 ANSI: 5
Oct 29 16:08:12 lim-laptop kernel: [    4.896000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 19 (level, low) -> IRQ 18
Oct 29 16:08:12 lim-laptop kernel: [    4.952000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Oct 29 16:08:12 lim-laptop kernel: [    4.968000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Oct 29 16:08:12 lim-laptop kernel: [    4.968000] sda: Write Protect is off
Oct 29 16:08:12 lim-laptop kernel: [    4.968000] sda: Mode Sense: 00 3a 00 00
Oct 29 16:08:12 lim-laptop kernel: [    4.968000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 29 16:08:12 lim-laptop kernel: [    4.968000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Oct 29 16:08:12 lim-laptop kernel: [    4.968000] sda: Write Protect is off
Oct 29 16:08:12 lim-laptop kernel: [    4.968000] sda: Mode Sense: 00 3a 00 00
Oct 29 16:08:12 lim-laptop kernel: [    4.968000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 29 16:08:12 lim-laptop kernel: [    4.968000]  sda: sda1 sda2 sda3 < sda5sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Oct 29 16:08:12 lim-laptop kernel: [    4.996000] Uniform CD-ROM driver Revision: 3.20
Oct 29 16:08:12 lim-laptop kernel: [    4.996000] sr 1:0:0:0: Attached scsi CD-ROM sr0
Oct 29 16:08:12 lim-laptop kernel: [    5.000000]  sda6 > sda4
Oct 29 16:08:12 lim-laptop kernel: [    5.000000] sd 0:0:0:0: Attached scsi disk sda
Oct 29 16:08:12 lim-laptop kernel: [    5.000000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 29 16:08:12 lim-laptop kernel: [    5.000000] sr 1:0:0:0: Attached scsi generic sg1 type 5
Oct 29 16:08:12 lim-laptop kernel: [    5.124000] usb 2-1: new full speed USB device using uhci_hcd and address 3
Oct 29 16:08:12 lim-laptop kernel: [    5.300000] usb 2-1: configuration #1 chosen from 1 choice
Oct 29 16:08:12 lim-laptop kernel: [    5.300000] hub 2-1:1.0: USB hub found
Oct 29 16:08:12 lim-laptop kernel: [    5.304000] hub 2-1:1.0: 3 ports detected
Oct 29 16:08:12 lim-laptop kernel: [    5.416000] EXT3-fs: INFO: recovery required on readonly filesystem.
Oct 29 16:08:12 lim-laptop kernel: [    5.416000] EXT3-fs: write access will be enabled during recovery.
Oct 29 16:08:12 lim-laptop kernel: [    5.652000] usb 3-1: new low speed USB device using uhci_hcd and address 2
Oct 29 16:08:12 lim-laptop kernel: [    5.824000] usb 3-1: configuration #1 chosen from 1 choice
Oct 29 16:08:12 lim-laptop kernel: [    6.032000] usb 2-1.1: new full speed USB device using uhci_hcd and address 4
Oct 29 16:08:12 lim-laptop kernel: [    6.160000] usb 2-1.1: configuration #1 chosen from 1 choice
Oct 29 16:08:12 lim-laptop kernel: [    6.228000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[434fc0002a1ed038]
Oct 29 16:08:12 lim-laptop kernel: [    6.368000] usb 2-1.2: new full speed USB device using uhci_hcd and address 5
Oct 29 16:08:12 lim-laptop kernel: [    6.500000] usb 2-1.2: configuration #1 chosen from 1 choice
Oct 29 16:08:12 lim-laptop kernel: [    6.708000] usb 2-1.3: new full speed USB device using uhci_hcd and address 6
Oct 29 16:08:12 lim-laptop kernel: [    6.840000] usb 2-1.3: configuration #1 chosen from 1 choice
Oct 29 16:08:12 lim-laptop kernel: [    6.844000] usbcore: registered new interface driver hiddev
Oct 29 16:08:12 lim-laptop kernel: [    6.856000] input: Genius NetScroll + Traveler as /class/input/input2
Oct 29 16:08:12 lim-laptop kernel: [    6.856000] input: USB HID v1.10 Mouse [Genius NetScroll + Traveler] on usb-0000:00:1d.2-1
Oct 29 16:08:12 lim-laptop kernel: [    6.860000] input: Broadcom Corp as /class/input/input3
Oct 29 16:08:12 lim-laptop kernel: [    6.860000] input: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.1-1.2
Oct 29 16:08:12 lim-laptop kernel: [    6.864000] input: Broadcom Corp as /class/input/input4
Oct 29 16:08:12 lim-laptop kernel: [    6.864000] input: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.1-1.3
Oct 29 16:08:12 lim-laptop kernel: [    6.864000] usbcore: registered new interface driver usbhid
Oct 29 16:08:12 lim-laptop kernel: [    6.864000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Oct 29 16:08:12 lim-laptop kernel: [   11.260000] kjournald starting.  Commit interval 5 seconds
Oct 29 16:08:12 lim-laptop kernel: [   11.260000] EXT3-fs: sda5: orphan cleanup on readonly fs
Oct 29 16:08:12 lim-laptop kernel: [   11.260000] ext3_orphan_cleanup: deleting unreferenced inode 2458942
Oct 29 16:08:12 lim-laptop kernel: [   11.260000] ext3_orphan_cleanup: deleting unreferenced inode 3830012
Oct 29 16:08:12 lim-laptop kernel: [   11.260000] ext3_orphan_cleanup: deleting unreferenced inode 517805
Oct 29 16:08:12 lim-laptop kernel: [   11.260000] ext3_orphan_cleanup: deleting unreferenced inode 517804
Oct 29 16:08:12 lim-laptop kernel: [   11.796000] ext3_orphan_cleanup: deleting unreferenced inode 517696
Oct 29 16:08:12 lim-laptop kernel: [   11.796000] ext3_orphan_cleanup: deleting unreferenced inode 517370
Oct 29 16:08:12 lim-laptop kernel: [   11.796000] ext3_orphan_cleanup: deleting unreferenced inode 517124
Oct 29 16:08:12 lim-laptop kernel: [   11.796000] EXT3-fs: sda5: 7 orphan inodes deleted
Oct 29 16:08:12 lim-laptop kernel: [   11.796000] EXT3-fs: recovery complete.
Oct 29 16:08:12 lim-laptop kernel: [   11.812000] EXT3-fs: mounted filesystem with ordered data mode.
Oct 29 16:08:12 lim-laptop kernel: [   22.904000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 29 16:08:12 lim-laptop kernel: [   22.908000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 29 16:08:12 lim-laptop kernel: [   23.148000] Linux agpgart interface v0.102 (c) Dave Jones
Oct 29 16:08:12 lim-laptop kernel: [   23.288000] agpgart: Detected an Intel 945GM Chipset.
Oct 29 16:08:12 lim-laptop kernel: [   23.288000] agpgart: Detected 7932K stolen memory.
Oct 29 16:08:12 lim-laptop kernel: [   23.304000] agpgart: AGP aperture is 256M @ 0xd0000000
Oct 29 16:08:12 lim-laptop kernel: [   23.472000] input: PC Speaker as /class/input/input5
Oct 29 16:08:12 lim-laptop kernel: [   23.740000] ieee80211_crypt: registered algorithm 'NULL'
Oct 29 16:08:12 lim-laptop kernel: [   23.928000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
Oct 29 16:08:12 lim-laptop kernel: [   23.940000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Oct 29 16:08:12 lim-laptop kernel: [   23.940000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Oct 29 16:08:12 lim-laptop kernel: [   23.968000] input: SynPS/2 Synaptics TouchPad as /class/input/input6
Oct 29 16:08:12 lim-laptop kernel: [   24.060000] intel_rng: FWH not detected
Oct 29 16:08:12 lim-laptop kernel: [   24.080000] Bluetooth: Core ver 2.11
Oct 29 16:08:12 lim-laptop kernel: [   24.080000] NET: Registered protocol family 31
Oct 29 16:08:12 lim-laptop kernel: [   24.080000] Bluetooth: HCI device and connection manager initialized
Oct 29 16:08:12 lim-laptop kernel: [   24.080000] Bluetooth: HCI socket layer initialized
Oct 29 16:08:12 lim-laptop kernel: [   24.152000] sdhci: Secure Digital Host Controller Interface driver
Oct 29 16:08:12 lim-laptop kernel: [   24.152000] sdhci: Copyright(c) Pierre Ossman
Oct 29 16:08:12 lim-laptop kernel: [   24.152000] sdhci: SDHCI controller found at 0000:02:01.1 [1180:0822] (rev 19)
Oct 29 16:08:12 lim-laptop kernel: [   24.152000] ACPI: PCI Interrupt 0000:02:01.1[B] -> GSI 18 (level, low) -> IRQ 23
Oct 29 16:08:12 lim-laptop kernel: [   24.152000] mmc0: SDHCI at 0xef9fd400 irq 23 DMA
Oct 29 16:08:12 lim-laptop kernel: [   24.220000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
Oct 29 16:08:12 lim-laptop kernel: [   24.220000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Oct 29 16:08:12 lim-laptop kernel: [   24.220000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Oct 29 16:08:12 lim-laptop kernel: [   24.220000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
Oct 29 16:08:12 lim-laptop kernel: [   24.220000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Oct 29 16:08:12 lim-laptop kernel: [   24.288000] Bluetooth: HCI USB driver ver 2.9
Oct 29 16:08:12 lim-laptop kernel: [   24.340000] usbcore: registered new interface driver hci_usb
Oct 29 16:08:12 lim-laptop kernel: [   24.400000] iTCO_vendor_support: vendor-support=0
Oct 29 16:08:12 lim-laptop kernel: [   24.400000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
Oct 29 16:08:12 lim-laptop kernel: [   24.400000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Oct 29 16:08:12 lim-laptop kernel: [   24.400000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Oct 29 16:08:12 lim-laptop kernel: [   24.608000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
Oct 29 16:08:12 lim-laptop kernel: [   24.608000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Oct 29 16:08:12 lim-laptop kernel: [   25.120000] fuse init (API version 7.8)
Oct 29 16:08:12 lim-laptop kernel: [   25.200000] lp: driver loaded but no devices found
Oct 29 16:08:12 lim-laptop kernel: [   25.240000] i8k: not running on a supported Dell system.
Oct 29 16:08:12 lim-laptop kernel: [   25.240000] i8k: vendor=Dell Inc., model=MXC061                          , version=A09
Oct 29 16:08:12 lim-laptop kernel: [   25.240000] i8k: unable to get SMM BIOS version
Oct 29 16:08:12 lim-laptop kernel: [   25.240000] Dell laptop SMM driver v1.14 21/02/2005 Massimo Dal Zotto (dz@debian.org)
Oct 29 16:08:12 lim-laptop kernel: [   25.304000] Adding 514040k swap on /dev/disk/by-uuid/81807514-eb54-4263-8d64-552d4fa2c4db.  Priority:-1 extents:1 across:514040k
Oct 29 16:08:12 lim-laptop kernel: [   25.392000] EXT3 FS on sda5, internal journal
Oct 29 16:08:12 lim-laptop kernel: [   26.224000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Oct 29 16:08:12 lim-laptop kernel: [   27.272000] NET: Registered protocol family 17
Oct 29 16:08:12 lim-laptop kernel: [   30.288000] ACPI: AC Adapter [AC] (on-line)
Oct 29 16:08:12 lim-laptop kernel: [   30.292000] No dock devices found.
Oct 29 16:08:12 lim-laptop kernel: [   30.300000] input: Lid Switch as /class/input/input7
Oct 29 16:08:12 lim-laptop kernel: [   30.300000] ACPI: Lid Switch [LID]
Oct 29 16:08:12 lim-laptop kernel: [   30.300000] input: Power Button (CM) as /class/input/input8
Oct 29 16:08:12 lim-laptop kernel: [   30.300000] ACPI: Power Button (CM) [PBTN]
Oct 29 16:08:12 lim-laptop kernel: [   30.300000] input: Sleep Button (CM) as /class/input/input9
Oct 29 16:08:12 lim-laptop kernel: [   30.300000] ACPI: Sleep Button (CM) [SBTN]
Oct 29 16:08:12 lim-laptop kernel: [   30.340000] ibm_acpi: ec object not found
Oct 29 16:08:12 lim-laptop kernel: [   30.424000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Oct 29 16:08:12 lim-laptop kernel: [   30.424000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Oct 29 16:08:12 lim-laptop kernel: [   30.464000] ACPI: Battery Slot [BAT0] (battery present)
Oct 29 16:08:12 lim-laptop kernel: [   30.672000] Using specific hotkey driver
Oct 29 16:08:12 lim-laptop kernel: [   30.744000] pcc_acpi: loading...
Oct 29 16:08:13 lim-laptop dhcdbd: Started up.
Oct 29 16:08:13 lim-laptop NetworkManager: <information>^Istarting... 
Oct 29 16:08:13 lim-laptop NetworkManager: <information>^Ieth1: Device is fully-supported using driver 'ipw3945'. 
Oct 29 16:08:13 lim-laptop NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Oct 29 16:08:13 lim-laptop NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Oct 29 16:08:13 lim-laptop NetworkManager: <information>^INow managing wireless (802.11) device 'eth1'. 
Oct 29 16:08:13 lim-laptop NetworkManager: <information>^IDeactivating device eth1. 
Oct 29 16:08:13 lim-laptop avahi-daemon[5202]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Oct 29 16:08:13 lim-laptop avahi-daemon[5202]: Successfully dropped root privileges.
Oct 29 16:08:13 lim-laptop avahi-daemon[5202]: avahi-daemon 0.6.17 starting up.
Oct 29 16:08:13 lim-laptop avahi-daemon[5202]: Successfully called chroot().
Oct 29 16:08:13 lim-laptop avahi-daemon[5202]: Successfully dropped remaining capabilities.
Oct 29 16:08:13 lim-laptop avahi-daemon[5202]: No service found in /etc/avahi/services.
Oct 29 16:08:13 lim-laptop avahi-daemon[5202]: Network interface enumeration completed.
Oct 29 16:08:13 lim-laptop avahi-daemon[5202]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 29 16:08:13 lim-laptop avahi-daemon[5202]: Server startup complete. Host name is lim-laptop.local. Local service cookie is 1801343434.
Oct 29 16:08:13 lim-laptop NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'b44'. 
Oct 29 16:08:13 lim-laptop NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Oct 29 16:08:13 lim-laptop NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Oct 29 16:08:13 lim-laptop NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Oct 29 16:08:13 lim-laptop NetworkManager: <information>^IDeactivating device eth0. 
Oct 29 16:08:16 lim-laptop ovpn-socvpn[5308]: OpenVPN 2.0.9 i486-pc-linux-gnu [SSL] [LZO] [EPOLL] built on Jun 11 2008
Oct 29 16:08:16 lim-laptop ovpn-socvpn[5308]: ERROR: could not read Auth username from stdin
Oct 29 16:08:16 lim-laptop ovpn-socvpn[5308]: Exiting
Oct 29 16:08:16 lim-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 29 16:08:16 lim-laptop NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link. 
Oct 29 16:08:16 lim-laptop NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Oct 29 16:08:16 lim-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 29 16:08:16 lim-laptop NetworkManager: <information>^IWill activate connection 'eth0'. 
Oct 29 16:08:16 lim-laptop NetworkManager: <information>^IDevice eth0 activation scheduled... 
Oct 29 16:08:16 lim-laptop NetworkManager: <information>^IActivation (eth0) started... 
Oct 29 16:08:16 lim-laptop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 29 16:08:16 lim-laptop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 29 16:08:16 lim-laptop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 29 16:08:16 lim-laptop NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 29 16:08:16 lim-laptop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 29 16:08:16 lim-laptop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct 29 16:08:16 lim-laptop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 29 16:08:16 lim-laptop NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 29 16:08:16 lim-laptop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct 29 16:08:16 lim-laptop kernel: [   35.444000] b44: eth0: Link is up at 100 Mbps, full duplex.
Oct 29 16:08:16 lim-laptop kernel: [   35.444000] b44: eth0: Flow control is off for TX and off for RX.
Oct 29 16:08:16 lim-laptop kernel: [   35.520000] ppdev: user-space parallel port driver
Oct 29 16:08:17 lim-laptop kernel: [   35.808000] NET: Registered protocol family 10
Oct 29 16:08:17 lim-laptop kernel: [   35.808000] lo: Disabled Privacy Extensions
Oct 29 16:08:17 lim-laptop kernel: [   35.812000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Oct 29 16:08:17 lim-laptop kernel: [   36.188000] [drm] Initialized drm 1.1.0 20060810
Oct 29 16:08:17 lim-laptop kernel: [   36.232000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 29 16:08:17 lim-laptop kernel: [   36.232000] [drm] Initialized i915 1.6.0 20060119 on minor 0
Oct 29 16:08:17 lim-laptop hpiod: 1.7.3 accepting connections at 2208... 
Oct 29 16:08:17 lim-laptop NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Oct 29 16:08:17 lim-laptop NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 29 16:08:17 lim-laptop NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Oct 29 16:08:18 lim-laptop avahi-daemon[5202]: Registering new address record for fe80::215:c5ff:fe78:1df8 on eth0.*.
Oct 29 16:08:19 lim-laptop NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Oct 29 16:08:19 lim-laptop mysqld_safe[5545]: started
Oct 29 16:08:19 lim-laptop mysqld[5548]: 081029 16:08:19  InnoDB: Database was not shut down normally!
Oct 29 16:08:19 lim-laptop mysqld[5548]: InnoDB: Starting crash recovery.
Oct 29 16:08:19 lim-laptop mysqld[5548]: InnoDB: Reading tablespace information from the .ibd files...
Oct 29 16:08:20 lim-laptop mysqld[5548]: InnoDB: Restoring possible half-written data pages from the doublewrite
Oct 29 16:08:20 lim-laptop mysqld[5548]: InnoDB: buffer...
Oct 29 16:08:20 lim-laptop mysqld[5548]: 081029 16:08:20  InnoDB: Starting log scan based on checkpoint at
Oct 29 16:08:20 lim-laptop mysqld[5548]: InnoDB: log sequence number 0 33435173.
Oct 29 16:08:20 lim-laptop mysqld[5548]: InnoDB: Doing recovery: scanned up to log sequence number 0 33435173
Oct 29 16:08:20 lim-laptop mysqld[5548]: InnoDB: Last MySQL binlog file position 0 39690, file name /var/log/mysql/mysql-bin.002325
Oct 29 16:08:20 lim-laptop mysqld[5548]: 081029 16:08:20  InnoDB: Started; log sequence number 0 33435173
Oct 29 16:08:20 lim-laptop mysqld[5548]: 081029 16:08:20 [Note] Recovering after a crash using /var/log/mysql/mysql-bin
Oct 29 16:08:20 lim-laptop mysqld[5548]: 081029 16:08:20 [Note] Starting crash recovery...
Oct 29 16:08:20 lim-laptop mysqld[5548]: 081029 16:08:20 [Note] Crash recovery finished.
Oct 29 16:08:20 lim-laptop mysqld[5548]: 081029 16:08:20 [Note] /usr/sbin/mysqld: ready for connections.
Oct 29 16:08:20 lim-laptop mysqld[5548]: Version: '5.0.38-Ubuntu_0ubuntu1.4-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  Ubuntu 7.04 distribution
Oct 29 16:08:21 lim-laptop /etc/mysql/debian-start[5603]: Upgrading MySQL tables if necessary.
Oct 29 16:08:22 lim-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct 29 16:08:22 lim-laptop /etc/init.d/mysql[5628]: Root password is blank.  To change it use '/etc/rc2.d/S19mysql reset-password'
Oct 29 16:08:23 lim-laptop kernel: [   41.660000] apm: BIOS not found.
Oct 29 16:08:24 lim-laptop nmbd[5710]: [2008/10/29 16:08:24, 0] nmbd/nmbd_subnetdb.c:create_subnets(190) 
Oct 29 16:08:24 lim-laptop nmbd[5710]:   create_subnets: No local interfaces ! 
Oct 29 16:08:24 lim-laptop nmbd[5710]: [2008/10/29 16:08:24, 0] nmbd/nmbd_subnetdb.c:create_subnets(191) 
Oct 29 16:08:24 lim-laptop nmbd[5710]:   create_subnets: Waiting for an interface to appear ... 
Oct 29 16:08:24 lim-laptop /etc/mysql/debian-start[5723]: Checking for crashed MySQL tables.
Oct 29 16:08:25 lim-laptop hcid[5797]: Bluetooth HCI daemon
Oct 29 16:08:25 lim-laptop hcid[5797]: HCI dev 0 registered
Oct 29 16:08:25 lim-laptop hcid[5797]: Starting SDP server
Oct 29 16:08:26 lim-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct 29 16:08:26 lim-laptop winbindd[5745]: [2008/10/29 16:08:26, 0] nsswitch/winbindd_util.c:init_domain_list(518) 
Oct 29 16:08:26 lim-laptop winbindd[5745]:   Could not fetch our SID - did we join? 
Oct 29 16:08:26 lim-laptop winbindd[5745]: [2008/10/29 16:08:26, 0] nsswitch/winbindd.c:main(1051) 
Oct 29 16:08:26 lim-laptop winbindd[5745]:   unable to initalize domain list 
Oct 29 16:08:26 lim-laptop kernel: [   44.768000] Bluetooth: L2CAP ver 2.8
Oct 29 16:08:26 lim-laptop kernel: [   44.768000] Bluetooth: L2CAP socket layer initialized
Oct 29 16:08:26 lim-laptop hcid[5797]: HCI dev 0 up
Oct 29 16:08:26 lim-laptop hcid[5797]: Device hci0 has been added
Oct 29 16:08:26 lim-laptop kernel: [   44.916000] Bluetooth: RFCOMM socket layer initialized
Oct 29 16:08:26 lim-laptop kernel: [   44.916000] Bluetooth: RFCOMM TTY layer initialized
Oct 29 16:08:26 lim-laptop kernel: [   44.916000] Bluetooth: RFCOMM ver 1.8
Oct 29 16:08:26 lim-laptop hcid[5797]: Starting security manager 0
Oct 29 16:08:26 lim-laptop hcid[5797]: Device hci0 has been activated
Oct 29 16:08:26 lim-laptop anacron[5836]: Anacron 2.3 started on 2008-10-29
Oct 29 16:08:26 lim-laptop anacron[5836]: Normal exit (0 jobs run)
Oct 29 16:08:26 lim-laptop /usr/sbin/cron[5867]: (CRON) INFO (pidfile fd = 3)
Oct 29 16:08:26 lim-laptop /usr/sbin/cron[5868]: (CRON) STARTUP (fork ok)
Oct 29 16:08:26 lim-laptop /usr/sbin/cron[5868]: (CRON) INFO (Running @reboot jobs)
Oct 29 16:08:30 lim-laptop gconfd (lim-6027): starting (version 2.18.0.1), pid 6027 user 'lim'
Oct 29 16:08:31 lim-laptop gconfd (lim-6027): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Oct 29 16:08:31 lim-laptop gconfd (lim-6027): Resolved address "xml:readwrite:/home/lim/.gconf" to a writable configuration source at position 1
Oct 29 16:08:31 lim-laptop gconfd (lim-6027): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Oct 29 16:08:31 lim-laptop gconfd (lim-6027): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Oct 29 16:08:31 lim-laptop gconfd (lim-6027): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Oct 29 16:08:34 lim-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Oct 29 16:08:34 lim-laptop NetworkManager: <information>^IOld device 'eth0' activating, won't change. 
Oct 29 16:08:34 lim-laptop dhclient: DHCPOFFER from 172.19.160.2
Oct 29 16:08:34 lim-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct 29 16:08:34 lim-laptop dhclient: DHCPACK from 172.19.160.2
Oct 29 16:08:34 lim-laptop avahi-daemon[5202]: Joining mDNS multicast group on interface eth0.IPv4 with address 172.19.165.6.
Oct 29 16:08:34 lim-laptop avahi-daemon[5202]: New relevant interface eth0.IPv4 for mDNS.
Oct 29 16:08:34 lim-laptop avahi-daemon[5202]: Registering new address record for 172.19.165.6 on eth0.IPv4.
Oct 29 16:08:34 lim-laptop avahi-daemon[5202]: Withdrawing address record for 172.19.165.6 on eth0.
Oct 29 16:08:34 lim-laptop avahi-daemon[5202]: Leaving mDNS multicast group on interface eth0.IPv4 with address 172.19.165.6.
Oct 29 16:08:34 lim-laptop avahi-daemon[5202]: Interface eth0.IPv4 no longer relevant for mDNS.
Oct 29 16:08:34 lim-laptop avahi-daemon[5202]: Joining mDNS multicast group on interface eth0.IPv4 with address 172.19.165.6.
Oct 29 16:08:34 lim-laptop avahi-daemon[5202]: New relevant interface eth0.IPv4 for mDNS.
Oct 29 16:08:34 lim-laptop avahi-daemon[5202]: Registering new address record for 172.19.165.6 on eth0.IPv4.
Oct 29 16:08:35 lim-laptop NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Oct 29 16:08:35 lim-laptop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 29 16:08:35 lim-laptop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Oct 29 16:08:35 lim-laptop dhclient: bound to 172.19.165.6 -- renewal in 729 seconds.
Oct 29 16:08:35 lim-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 29 16:08:35 lim-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 29 16:08:35 lim-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 29 16:08:35 lim-laptop NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Oct 29 16:08:35 lim-laptop NetworkManager: <information>^I  address 172.19.165.6 
Oct 29 16:08:35 lim-laptop NetworkManager: <information>^I  netmask 255.255.240.0 
Oct 29 16:08:35 lim-laptop NetworkManager: <information>^I  broadcast 172.19.175.255 
Oct 29 16:08:35 lim-laptop NetworkManager: <information>^I  gateway 172.19.160.1 
Oct 29 16:08:35 lim-laptop NetworkManager: <information>^I  nameserver 137.132.0.254 
Oct 29 16:08:35 lim-laptop NetworkManager: <information>^I  nameserver 137.132.0.252 
Oct 29 16:08:35 lim-laptop NetworkManager: <information>^I  domain name 'nus.edu.sg' 
Oct 29 16:08:35 lim-laptop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 29 16:08:35 lim-laptop NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Oct 29 16:08:35 lim-laptop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Oct 29 16:08:35 lim-laptop avahi-daemon[5202]: Withdrawing address record for 172.19.165.6 on eth0.
Oct 29 16:08:35 lim-laptop avahi-daemon[5202]: Leaving mDNS multicast group on interface eth0.IPv4 with address 172.19.165.6.
Oct 29 16:08:35 lim-laptop avahi-daemon[5202]: Interface eth0.IPv4 no longer relevant for mDNS.
Oct 29 16:08:35 lim-laptop avahi-daemon[5202]: Withdrawing address record for fe80::215:c5ff:fe78:1df8 on eth0.
Oct 29 16:08:35 lim-laptop avahi-daemon[5202]: Joining mDNS multicast group on interface eth0.IPv4 with address 172.19.165.6.
Oct 29 16:08:35 lim-laptop avahi-daemon[5202]: New relevant interface eth0.IPv4 for mDNS.
Oct 29 16:08:35 lim-laptop avahi-daemon[5202]: Registering new address record for 172.19.165.6 on eth0.IPv4.
Oct 29 16:08:36 lim-laptop NetworkManager: <information>^IClearing nscd hosts cache. 
Oct 29 16:08:36 lim-laptop NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 29 16:08:36 lim-laptop NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Oct 29 16:08:36 lim-laptop NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Oct 29 16:08:36 lim-laptop NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 29 16:08:37 lim-laptop avahi-daemon[5202]: Registering new address record for fe80::215:c5ff:fe78:1df8 on eth0.*.
Oct 29 16:08:38 lim-laptop ntpdate[6086]: step time server 91.189.94.4 offset 0.839114 sec
Oct 29 16:08:39 lim-laptop hcid[5797]: Default passkey agent (:1.14, /org/bluez/applet) registered
Oct 29 16:08:40 lim-laptop gconfd (lim-6027): Resolved address "xml:readwrite:/home/lim/.gconf" to a writable configuration source at position 0
Oct 29 16:08:48 lim-laptop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Oct 29 16:09:04 lim-laptop /USR/SBIN/CRON[6470]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
Oct 29 16:09:04 lim-laptop /USR/SBIN/CRON[6471]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct 29 16:10:01 lim-laptop /USR/SBIN/CRON[6584]: (lim) CMD (/usr/bin/python /home/lim/ranwp.py)
Oct 29 16:10:03 lim-laptop avahi-daemon[5202]: Invalid response packet.
Oct 29 16:10:05 lim-laptop last message repeated 3 times
Oct 29 16:10:16 lim-laptop nmbd[5710]: [2008/10/29 16:10:16, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Oct 29 16:10:16 lim-laptop nmbd[5710]:   ***** 
Oct 29 16:10:16 lim-laptop nmbd[5710]:    
Oct 29 16:10:16 lim-laptop nmbd[5710]:   Samba name server LIM-LAPTOP is now a local master browser for workgroup NUSSTU on subnet 172.19.165.6 
Oct 29 16:10:16 lim-laptop nmbd[5710]:    
Oct 29 16:10:16 lim-laptop nmbd[5710]:   ***** 
Oct 29 16:10:34 lim-laptop nmbd[5710]: [2008/10/29 16:10:34, 0] nmbd/nmbd_incomingdgrams.c:process_local_master_announce(309) 
Oct 29 16:10:34 lim-laptop nmbd[5710]:   process_local_master_announce: Server U0707716 at IP 172.19.167.173 is announcing itself as a local master browser for workgroup NUSSTU and we think we are master. Forcing election. 
Oct 29 16:10:34 lim-laptop nmbd[5710]: [2008/10/29 16:10:34, 0] nmbd/nmbd_become_lmb.c:unbecome_local_master_success(149) 
Oct 29 16:10:34 lim-laptop nmbd[5710]:   ***** 
Oct 29 16:10:34 lim-laptop nmbd[5710]:    
Oct 29 16:10:34 lim-laptop nmbd[5710]:   Samba name server LIM-LAPTOP has stopped being a local master browser for workgroup NUSSTU on subnet 172.19.165.6 
Oct 29 16:10:34 lim-laptop nmbd[5710]:    
Oct 29 16:10:34 lim-laptop nmbd[5710]:   ***** 
Oct 29 16:10:52 lim-laptop nmbd[5710]: [2008/10/29 16:10:52, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396) 
Oct 29 16:10:52 lim-laptop nmbd[5710]:   ***** 
Oct 29 16:10:52 lim-laptop nmbd[5710]:    
Oct 29 16:10:52 lim-laptop nmbd[5710]:   Samba name server LIM-LAPTOP is now a local master browser for workgroup NUSSTU on subnet 172.19.165.6 
Oct 29 16:10:52 lim-laptop nmbd[5710]:    
Oct 29 16:10:52 lim-laptop nmbd[5710]:   ***** 
```

---

### Post by moofang on 2008-10-30
bump

---

### Post by debiant on 2008-12-08
Same problem-not even a shutdown, the system just seems to stop dead, as if I just pulled the plug out. Seems to happen when I'm online just after the updates available red arrow appears?
Anyone any ideas? It started for me a few days ago.:confused:

---

