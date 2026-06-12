---
title: "[SOLVED] Apache httpd: limiting simultaneous connections"
date: 2008-10-05
forum: General Help
---

### Post by x1a4 on 2008-10-05
Hi,
I need to limit simultaneous connections to Apache httpd to 100, and ensure that any connection attempt above that is queued instead of denied access. How do I do that?  

Thank you.

---

### Post by Bluebell392 on 2008-10-05
Assuming the configuration files are in /etc/apache2, you would edit the apache2.conf file, and look for prefork MPM. There you should find a block of text similar to this: 
```
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>
```

"StartServers: number of server processes to start
MinSpareServers: minimum number of server processes which are kept spare
MaxSpareServers: maximum number of server processes which are kept spare
MaxClients: maximum number of server processes allowed to start
MaxRequestsPerChild: maximum number of requests a server process serves
"

You would probably want to tune MaxClients, MaxRequestsPerChild, and StartServers. Set them to whatever you like (within capabilities of the hardware, of course.)

---

