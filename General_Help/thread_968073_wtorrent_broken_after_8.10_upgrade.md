---
title: "wtorrent broken after 8.10 upgrade"
date: 2008-11-02
forum: General Help
---

### Post by orion2087 on 2008-11-02
After upgrading Ubuntu 8.04 server to 8.10, I'm getting a 403 on my wtorrent page. Any ideas?

[EDIT] It looks like all PHP is doing this, even a blank index.php.

---

### Post by orion2087 on 2008-11-02
Fixed by adding the following to /etc/lighttpd/lighttpd.conf

```
fastcgi.server = ( ".php" => ((
                     "bin-path" => "/usr/bin/php-cgi",
                     "socket" => "/tmp/php.socket",
                     "max-procs" => 2,
                     "bin-environment" => (
                       "PHP_FCGI_CHILDREN" => "16",
                       "PHP_FCGI_MAX_REQUESTS" => "10000"
                     ),
                     "bin-copy-environment" => (
                       "PATH", "SHELL", "USER"
                     ),
                     "broken-scriptfilename" => "enable"
                 )))
```

also added mod_fastcgi under server.modules

---

