---
title: "Enable Remote Logging"
date: 2008-11-29
forum: General Help
---

### Post by mattrock on 2008-11-29
If you would like to use your Ubuntu 8.10 system as a log collector for other devices on your network, the steps are really easy.

```
sudo nano /etc/default/syslogd
```

Add "-R" to between the SYSLOGD="" config so that it looks like;
```
SYSLOGD="-r"
```

Punch your firewall if you require to let in UDP packets on port 514.  Next, restart your syslog server with this command:
```
sudo /etc/init.d/sysklogd restart
```

This sets your system up to receive logs from other devices on your net.

To have another network device send logs to your now ready to accept remote log server, check to see if the device has a config option for "remote logging."  It will likely ask for a server (or IP) and a port.  Common devices which may have remote logging are NAS boxes and firewall routers.  
If you would like to forward logs from a linux system, typically all that is needed is to add the following line to the /etc/syslog.conf file;
```
*  @logserver
``` Where "logserver" is the name or IP of the logging server you just set up.

---

