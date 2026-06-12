---
title: "starting tftpd-hpa  (hardy)"
date: 2008-07-14
forum: General Help
---

### Post by calicoAngelina on 2008-07-14
Hi,
I have a Hardy server that I want to use for tftp behind my inside firewall.
I poked around, found [COLOR="Blue"]/etc/default/tftpd-hpa[/COLOR] with  
> [COLOR="Green"]RUN_DAEMON="no"[/COLOR]
Also found [COLOR="Blue"]/etc/init.d/tftpd-hpa[/COLOR], with 
> [COLOR="Green"]test "$RUN_DAEMON" = "yes" || exit 0[/COLOR]
So, I changed 
>RUN_DAEMON="**no**"   to
>RUN_DAEMON="**yes**"  then did:
user@friesian:~$ sudo /etc/init.d/tftpd-hpa start
[sudo] password for user:

Response is:
Starting HPA's tftpd: in.tftpduser@friesian:~$

(there's no lf/cr, leaving the command prompt on the same line as the status message - probably not significant, but included here just in case...)

However, netstat does not show port 69 open.  Also, attempts to send a file by tftp from a machine on the same subnet fail.

Likely something simple, but I can't I don't know where to go seeing as how it's actually telling me that tftpd-hpa is starting...

Anyone?
Thx...

---

### Post by tybalt on 2008-10-03
check your /etc/inetd.config file.
you should have something like:
tftp		dgram	udp	wait	tftpd	/usr/sbin/tcpd	/usr/sbin/in.tftpd /srv/tftp

so you have your tftp server started at system startup.

regards,

---

