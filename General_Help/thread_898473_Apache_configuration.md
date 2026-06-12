---
title: "Apache configuration"
date: 2008-08-23
forum: General Help
---

### Post by liquorvicar on 2008-08-23
I can't seem to get apache up and running.
It starts OK:
andy@andy-desktop:/etc/apache2$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                                                                             apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
andy@andy-desktop:/etc/apache2$ sudo netstat -plant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      10106/apache2
          
However whenever I try and access anything through my browser I get this error:
Bad Request

Your browser sent a request that this server could not understand.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch Server at localhost Port 80

I'm on Kubuntu Hardy Heron. Any ideas?

---

### Post by RealPSL on 2008-08-23
Well let us start from the first error although this is not what is causing your Apache to fail. In your /etc/hosts add the fully qualified name to the IP address for 127.0.1.1. E.g.

It currently looks something like this:
> 127.0.1.1       my-desktop

Make it look like this
```
127.0.1.1       my-desktop        my-desktop.example.com
```

To fix the other problem where it is not responding properly to the web browser we need to see the log files located in /var/log/apache2. If you can please attach the error.log file. The access.log will help as well.

---

### Post by Iowan on 2008-08-23
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")
Another option under "Troubleshooting Apache"

---

### Post by liquorvicar on 2008-08-23
I managed to get rid of the FQDN error (although I don't think that one really mattered). I'm still getting "400 bad Request" when I try a view a page:
andy@andy-desktop:/etc/apache2/conf.d$ tail /var/log/apache2/error.log
[Sat Aug 23 14:39:36 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 23 14:39:46 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 23 15:37:20 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 23 15:37:23 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 23 19:07:08 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 23 19:07:12 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 23 19:30:47 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 23 19:30:48 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 23 19:31:49 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 23 19:31:52 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations

andy@andy-desktop:/etc/apache2/conf.d$ tail /var/log/apache2/access.log
127.0.0.1 - - [23/Aug/2008:19:30:47 +0100] "OPTIONS * HTTP/1.0" 400 340 "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [23/Aug/2008:19:30:47 +0100] "OPTIONS * HTTP/1.0" 400 340 "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [23/Aug/2008:19:30:47 +0100] "OPTIONS * HTTP/1.0" 400 340 "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [23/Aug/2008:19:31:49 +0100] "OPTIONS * HTTP/1.0" 400 340 "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [23/Aug/2008:19:31:49 +0100] "OPTIONS * HTTP/1.0" 400 340 "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [23/Aug/2008:19:31:49 +0100] "OPTIONS * HTTP/1.0" 400 340 "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [23/Aug/2008:19:31:49 +0100] "OPTIONS * HTTP/1.0" 400 340 "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [23/Aug/2008:19:31:49 +0100] "OPTIONS * HTTP/1.0" 400 340 "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [23/Aug/2008:19:31:57 +0100] "GET / HTTP/1.1" 400 340 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"
127.0.0.1 - - [23/Aug/2008:19:31:58 +0100] "GET / HTTP/1.1" 400 340 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1"

---

### Post by RealPSL on 2008-08-23
The FQDN error was really irrelevant but I just wanted to get it out the way. It is pretty clear from the logs that you Apache is crashing though. Are you hitting just an html page when it happens our a page with php codes?

---

### Post by liquorvicar on 2008-08-24
> **RealPSL said:**
> The FQDN error was really irrelevant but I just wanted to get it out the way.
Fair enough.

> **RealPSL said:**
>  It is pretty clear from the logs that you Apache is crashing though.
Are you sure? All I'm seeing in the error log is apache restarting.

> **RealPSL said:**
>  Are you hitting just an html page when it happens our a page with php codes?
Just plain 'ole HTML.

---

### Post by liquorvicar on 2008-08-31
Tried uninstalling and reinstalling Apache. Uninstalled the packages from Adept and removed the /etc/apache2 directory. When I reinstalled the apache packages, the sub-directories of /etc/apache2 were all empty. Did I miss something? Is there a package that installs the default config files?

---

### Post by RealPSL on 2008-09-03
Most of the files should have come back when you installed apache2.2-common package.

---

### Post by liquorvicar on 2008-09-04
I had that installed and there's still no config files there. I've tried uninstalling it and reinstalling it and nothing.

The mods are there under /usr/lib/apache2
When I look at the installed files in the package detail in adept I can see all the config files but they're all listed as 0 bytes.

---

