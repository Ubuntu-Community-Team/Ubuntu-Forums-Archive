---
title: "Upgrade apache2: local hosted website not working."
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by greenshirt11 on 2009-08-26
kubuntu 9.04

Upgraded apache2 to 2.2.11-2ubuntu2.3 via synaptic the normal way.

Now i can't access my local hosted website(s) anymore.
I used to type in 'websiteXYZ' and it would find /var/www/websiteXYZ/index.html ok.
Now it asks if i want to download a PHTML file.
In the /var/www/websiteXYZ directory is a .htaccess file containing:

```
AddType application/x-httpd-php .php .htm .html
```

Everything was setup properly for working with name based virtual hosts and using php (the index.html contains php code).

If i open a testphp.php file containing a call to phpinfo(), proper results are returned. What seems strange is the setting for "Virtual Directory Support". That says it is disabled. Could that indicate a problem? Howto get it to enabled then?

Is it a problem related to not handling php correctly anymore or to something with virtual hosts (directories)?

Thanks.

---

### Post by greenshirt11 on 2009-08-27
OK that was very simple too solve. Silly me.

---

