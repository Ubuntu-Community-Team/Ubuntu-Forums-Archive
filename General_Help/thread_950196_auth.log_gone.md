---
title: "auth.log gone"
date: 2008-10-16
forum: General Help
---

### Post by Shwick2 on 2008-10-16
Running ubuntu 8.04

I wanted to separate the cron logs from the auth logs, so in /etc/syslog.conf I uncommented the line "cron.*        /var/log/cron.log".

I also wanted to cleanse the auth logs, so I deleted all of them.

I then restarted and tried to login via ssh, but there were no auth logs- a new auth.log wasn't created.  The cron jobs were now logged to cron.log though.

I tried creating an auth.log and restarting but that didn't work, I think it was because I had to create it with sudo, so it was owned by "root" instead of "adm", like syslog.

How do I get my auth.log back?

---

### Post by unutbu on 2008-10-16
Make sure you have this in /etc/syslog.conf:
```

auth,authpriv.*			/var/log/auth.log

```
Make sure the permissions and ownership are like this for /var/log/auth.log:
```

  -rw-r-----  1 syslog adm  108086 2008-10-16 22:39 auth.log
```

Have you rebooted the machine?
I don't know for sure, but it is possible that cron, sshd and gdm open /var/log/auth.log when they are first launched. If you subsequently delete the file, these daemons may have a file handle pointing to nowhere, and so when they try to write to /var/log/auth.log it fails even if you create a new /var/log/auth.log. If this is the case -- and it is only a guess -- you may have to restart each of these daemons, or just reboot.

If you want to test the theory without rebooting, do
```

sudo /etc/init.d/ssh restart
```

This will restart the sshd daemon. Then try logging in via ssh and see if it successfully writes to /var/log/auth.log.

---

### Post by Shwick2 on 2008-10-17
I created auth.log with "sudo touch auth.log" and changed it's permissions with "sudo chown syslog auth.log", "sudo chgrp adm auth.log" and "sudo chmod 640" to make it the same as syslog.

I tried restarting sshd but that didn't work, I had to restart the machine.  sshd then started logging to auth.log properly.

I'm a little concerned with the first few log messages though, entered right after restart:

```
Oct 17 10:21:01 desktop sshd[4832]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Oct 17 10:21:03 desktop sshd[4832]: Received SIGHUP; restarting.
Oct 17 10:21:03 desktop sshd[5538]: Server listening on :: port 22.
Oct 17 10:21:03 desktop sshd[5538]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Oct 17 10:22:46 desktop sshd[5807]: Accepted password for [my username] from [an ip] port 62485 ssh2
```

Why would sshd not be able to bind to port 22 but also be able to accept incoming connections, as I was still able to login?

---

### Post by unutbu on 2008-10-17
I think it is a harmless error message
caused by sshd trying to bind to port 22 on all ipv6 addresses, and then trying to bind to port 22 on all ipv4 addresses. If the first works, the second fails.

Nevertheless, if you would like to get rid of the error message, see: 
[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/129789](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/129789)

---

### Post by iponeverything on 2008-10-17
doing a:

```

sudo /etc/init.d/sysklogd restart

```
will get your logs going again..

> Why would sshd not be able to bind to port 22 but also be able to accept incoming connections, as I was still able to login?

sshd was already running on port 22

---

### Post by Shwick2 on 2008-10-17
I don't really care about fixing that minor bug then, I'll let it appear in the logs, as long as logging is working, which it is.

 Also thanks for telling me how to restart the logging daemon.

---

