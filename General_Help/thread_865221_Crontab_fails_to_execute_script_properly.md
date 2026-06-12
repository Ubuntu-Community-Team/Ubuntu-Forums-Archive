---
title: "Crontab fails to execute script properly"
date: 2008-07-20
forum: General Help
---

### Post by fiatguy85 on 2008-07-20
I have made a script to restart my wireless connection every hour.  When executed manually, it seems to work perfectly.  When I run it from the root users crontab, it fails to restart the connection completely, but the script appears to run to completion since the echo line is executed.  I have tried adding sleep and wait commands in it as well as using ifup/ifdown and /etc/init.d/networking restart as alternative methods of restarting the connection.  Here is the script:

```
:~$ cat /home/user/bin/networking
#!/bin/sh

dhclient -r ra0
ifconfig ra0 down
sleep 0
ifconfig ra0 up
dhclient ra0
echo "Networking Restarted: $(date)" >> /home/user/tmp/networking.log

```

This is the root crontab:

```
:~$ sudo crontab -l
PATH=/usr/sbin:/usr/bin:/sbin:/bin

# m h  dom mon dow   command
04 * * * * sh /home/user/bin/networking

```

This is the result in /var/log/syslog when cron runs the script:

```
Jul 20 13:04:01 bob /usr/sbin/cron[6689]: (root) RELOAD (crontabs/root)
Jul 20 13:04:01 bob /USR/SBIN/CRON[17325]: (root) CMD (sh /home/user/bin/networking)
Jul 20 13:04:01 bob dhclient: There is already a pid file /var/run/dhclient.pid with pid 16709
Jul 20 13:04:01 bob dhclient: killed old client process, removed PID file
Jul 20 13:04:01 bob dhclient: Internet Systems Consortium DHCP Client V3.0.6
Jul 20 13:04:01 bob dhclient: Copyright 2004-2007 Internet Systems Consortium.
Jul 20 13:04:01 bob dhclient: All rights reserved.
Jul 20 13:04:01 bob dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jul 20 13:04:01 bob dhclient: 
Jul 20 13:04:01 bob dhclient: Listening on LPF/ra0/00:12:17:86:0e:aa
Jul 20 13:04:01 bob dhclient: Sending on   LPF/ra0/00:12:17:86:0e:aa
Jul 20 13:04:01 bob dhclient: Sending on   Socket/fallback
Jul 20 13:04:01 bob dhclient: DHCPRELEASE on ra0 to 192.168.1.1 port 67
Jul 20 13:04:01 bob avahi-daemon[5944]: Withdrawing address record for 192.168.1.112 on ra0.
Jul 20 13:04:01 bob avahi-daemon[5944]: Leaving mDNS multicast group on interface ra0.IPv4 with address 192.168.1.112.
Jul 20 13:04:01 bob avahi-daemon[5944]: Interface ra0.IPv4 no longer relevant for mDNS.
Jul 20 13:04:01 bob avahi-daemon[5944]: Withdrawing address record for fe80::212:17ff:fe86:eaa on ra0.
Jul 20 13:04:01 bob dhclient: receive_packet failed on ra0: Network is down
Jul 20 13:04:01 bob dhclient: There is already a pid file /var/run/dhclient.pid with pid 134519072
Jul 20 13:04:01 bob dhclient: Internet Systems Consortium DHCP Client V3.0.6
Jul 20 13:04:01 bob dhclient: Copyright 2004-2007 Internet Systems Consortium.
Jul 20 13:04:01 bob dhclient: All rights reserved.
Jul 20 13:04:01 bob dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jul 20 13:04:01 bob dhclient: 
Jul 20 13:04:02 bob dhclient: Listening on LPF/ra0/00:12:17:86:0e:aa
Jul 20 13:04:02 bob dhclient: Sending on   LPF/ra0/00:12:17:86:0e:aa
Jul 20 13:04:02 bob dhclient: Sending on   Socket/fallback
Jul 20 13:04:02 bob avahi-daemon[5944]: Registering new address record for fe80::212:17ff:fe86:eaa on ra0.*.
Jul 20 13:04:05 bob dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
Jul 20 13:04:09 bob ntpd[22197]: sendto(91.189.94.4) (fd=21): Invalid argument
Jul 20 13:04:11 bob kernel: [319506.763069] ra0: no IPv6 routers present
Jul 20 13:04:26 bob kernel: [319521.132405]  CIFS VFS: server not responding
Jul 20 13:04:26 bob kernel: [319521.132417]  CIFS VFS: No response for cmd 50 mid 26128
```

This is the result in /var/log/syslog when i execute the script manually (sudo /home/user/bin/networking): 

```
Jul 20 13:05:50 bob dhclient: There is already a pid file /var/run/dhclient.pid with pid 134519072
Jul 20 13:05:50 bob dhclient: Internet Systems Consortium DHCP Client V3.0.6
Jul 20 13:05:50 bob dhclient: Copyright 2004-2007 Internet Systems Consortium.
Jul 20 13:05:50 bob dhclient: All rights reserved.
Jul 20 13:05:50 bob dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jul 20 13:05:50 bob dhclient: 
Jul 20 13:05:50 bob dhclient: Listening on LPF/ra0/00:12:17:86:0e:aa
Jul 20 13:05:50 bob dhclient: Sending on   LPF/ra0/00:12:17:86:0e:aa
Jul 20 13:05:50 bob dhclient: Sending on   Socket/fallback
Jul 20 13:05:50 bob dhclient: DHCPRELEASE on ra0 to 192.168.1.1 port 67
Jul 20 13:05:50 bob dhclient: send_packet: Network is unreachable
Jul 20 13:05:50 bob dhclient: send_packet: please consult README file regarding broadcast address.
Jul 20 13:05:50 bob avahi-daemon[5944]: Withdrawing address record for fe80::212:17ff:fe86:eaa on ra0.
Jul 20 13:05:50 bob dhclient: receive_packet failed on ra0: Network is down
Jul 20 13:05:50 bob dhclient: There is already a pid file /var/run/dhclient.pid with pid 134519072
Jul 20 13:05:50 bob dhclient: Internet Systems Consortium DHCP Client V3.0.6
Jul 20 13:05:50 bob dhclient: Copyright 2004-2007 Internet Systems Consortium.
Jul 20 13:05:50 bob dhclient: All rights reserved.
Jul 20 13:05:50 bob dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jul 20 13:05:50 bob dhclient: 
Jul 20 13:05:51 bob dhclient: Listening on LPF/ra0/00:12:17:86:0e:aa
Jul 20 13:05:51 bob dhclient: Sending on   LPF/ra0/00:12:17:86:0e:aa
Jul 20 13:05:51 bob dhclient: Sending on   Socket/fallback
Jul 20 13:05:52 bob dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
Jul 20 13:05:52 bob avahi-daemon[5944]: Registering new address record for fe80::212:17ff:fe86:eaa on ra0.*.
Jul 20 13:06:00 bob dhclient: DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
Jul 20 13:06:00 bob dhclient: DHCPOFFER of 192.168.1.112 from 192.168.1.1
Jul 20 13:06:00 bob dhclient: DHCPREQUEST of 192.168.1.112 on ra0 to 255.255.255.255 port 67
Jul 20 13:06:00 bob dhclient: DHCPACK of 192.168.1.112 from 192.168.1.1
Jul 20 13:06:00 bob avahi-daemon[5944]: Joining mDNS multicast group on interface ra0.IPv4 with address 192.168.1.112.
Jul 20 13:06:00 bob avahi-daemon[5944]: New relevant interface ra0.IPv4 for mDNS.
Jul 20 13:06:00 bob avahi-daemon[5944]: Registering new address record for 192.168.1.112 on ra0.IPv4.
Jul 20 13:06:00 bob dhclient: bound to 192.168.1.112 -- renewal in 930910087 seconds.
Jul 20 13:06:01 bob kernel: [319616.295574] ra0: no IPv6 routers present
Jul 20 13:06:04 bob ntpd[22197]: no servers reachable
```

Thanks for the help.

---

### Post by Krupski on 2008-07-22
> **fiatguy85 said:**
> 
```
:~$ sudo crontab -l
PATH=/usr/sbin:/usr/bin:/sbin:/bin

# m h  dom mon dow   command
04 * * * * sh /home/user/bin/networking

```


You need to have the user specified in crontab.

Since you have 'sh" after the time specification, cron thinks you want the user 'sh' to run your script.

Edit the line to look like this (addition in bold):

```

# m h  dom mon dow   command
04 * * * * **root** sh /home/user/bin/networking

```

Should work now...

I like to add relevant pieces of man pages or other info into config files so that I don't have to look things up. For example, I *added* these comments to my 'crontab' file:

```

###############################################################
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the 'crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.
#
# TIME FIELDS:
#
#       * * * * * * command to execute && next command && ...
#       - - - - - -
#       | | | | | |
#       | | | | | +--- run command as 'user' (i.e. root)
#       | | | | +----- day of week (0-7) (Sunday=0 or 7)
#       | | | +------- month (1-12)
#       | | +--------- day of month (1-31)
#       | +----------- hour (0-23)
#       +------------- minute (0-59)
#
# SPECIAL STRINGS:
#
#       special string  meaning
#       --------------  -------
#
#       @reboot         Run once, at startup.
#       @yearly         Run once a year [0 0 1 1 *]
#       @annually       (same as @yearly)
#       @monthly        Run once a month [0 0 1 * *]
#       @weekly         Run once a week [0 0 * * 0]
#       @daily          Run once a day [0 0 * * *]
#       @midnight       (same as @daily)
#       @hourly         Run once an hour [0 * * * *]
#
###############################################################

```

-- Roger

---

### Post by fiatguy85 on 2008-07-22
Thanks, but sorry, I didn't realize I still had that in there.  That was just a variation of executing the command I tried.  I was trying to run this from my root user's crontab, which is what is displayed and requires no username to be specified.  I have also tried running it from /etc/crontab with the root user specified and had the same result as running it from the root user's crontab.

---

### Post by Potatoj316 on 2008-07-22
its kind of off topic but why do you run every hour at minute 04?

---

### Post by fiatguy85 on 2008-07-22
That's when I was testing it out.  I'd try whatever I thought might help or fix it and set it for the next minute or two to see if it succeeded.  I don't know of a better way to try it out.

---

### Post by fiatguy85 on 2008-07-23
Still looking for some help.  Can anyone figure out why it doesn't execute the same with crontab running the script?

---

### Post by kylea on 2009-05-17
try this 

[http://www.estamos.de/blog/2009/05/08/running-syncevolution-as-cron-job/](http://www.estamos.de/blog/2009/05/08/running-syncevolution-as-cron-job/)

---

