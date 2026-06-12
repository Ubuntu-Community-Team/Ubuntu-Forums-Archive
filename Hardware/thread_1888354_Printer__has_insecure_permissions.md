---
title: "Printer  has insecure permissions"
date: 2011-11-29
forum: Hardware
---

### Post by afrodeity on 2011-11-29
Status message

The printers state message is Directory /usr/local/lexmark/lxxk08/bin/printerdriver has insecure permissions (040775/uid=0/gid=2)

warnings are
cups-insecure-filter

```

chown root:root /usr/local/lexmark/lxxk08/bin/printerdriver

```

doesn't work, I've also tried

chmod 777

No success

I have also tried setting /usr/sbin/cupsd to complain mode

```

 sudo aa-complain cupsd

```

Also, restarting cups

```

sudo /etc/init.d/cups restart

```
no luck, doesn't appear to be an apparmour problem or is it?

---

