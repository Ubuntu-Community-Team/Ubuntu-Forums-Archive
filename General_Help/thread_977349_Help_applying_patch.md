---
title: "Help applying patch"
date: 2008-11-10
forum: General Help
---

### Post by eludlow on 2008-11-10
I'm getting the following message though CRON every day:

> Subject: Cron <root@wilfred> test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
/etc/cron.daily/apt:
No value set for `/system/http_proxy/use_http_proxy'
No value set for `/system/http_proxy/host'
No value set for `/system/http_proxy/port'

A quick google reveals this [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/223502](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/223502) which has the following diff file:

```
--- apt.orig    2008-04-28 08:56:53.000000000 +0200
+++ apt 2008-04-28 08:57:29.000000000 +0200
@@ -201,9 +201,9 @@
 # set the proxy based on the admin users gconf settings
 admin_user=$(getent group admin|cut -d: -f4|cut -d, -f1)
 if [ -n "$admin_user" ] && [ -x /usr/bin/sudo ] && [ -z "$http_proxy" ] && [ -x /usr/bin/gconftool ]; then
-       use=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/use_http_proxy)
-       host=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/host)
-       port=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/port)
+       use=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/use_http_proxy 2>/dev/null);
+       host=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/host 2>/dev/null);
+       port=$(sudo -u "$admin_user" gconftool --get /system/http_proxy/port 2>/dev/null)
        if [ "$use" = "true" ] && [ -n "$host" ] && [ -n "$port" ]; then
                export http_proxy="http://$host:$port/"
        fi

```

But I have no idea how to apply this - any help would be appreciated.

Thanks,
Ed Ludlow

---

### Post by geirha on 2008-11-10
```

cp /etc/cron.daily/apt $HOME/apt.backup   # Make a backup copy to be safe
sudo patch /etc/cron.daily/apt < cron_daily_apt.diff

```

---

### Post by eludlow on 2008-11-10
Thanks.  Getting:

```
patching file /etc/cron.daily/apt
Hunk #1 FAILED at 201.
1 out of 1 hunk FAILED -- saving rejects to file /etc/cron.daily/apt.rej

```

Any ideas?

---

### Post by geirha on 2008-11-10
Possibly a mismatch of spaces. Try ```
sudo patch -l /etc/cron.daily/apt < cron_daily_apt.diff
``` That's a lowecase L.

---

### Post by eludlow on 2008-11-10
Brilliant, thank you :)

---

