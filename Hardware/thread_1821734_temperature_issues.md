---
title: "temperature issues"
date: 2011-08-09
forum: Hardware
---

### Post by l3ecl on 2011-08-09
I noticed my laptop idle temperature has increased to to an average of 44 degrees Celsius from a previous 37 degrees Cecilius. Yet, physically, it does not feel any hotter.

Also when I run dmesg I get spammed with this message:
```

[27283.736911] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[27288.724143] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
[27293.711427] intel ips 0000:00:1f.6: MCP power or thermal limit exceeded

```

---

### Post by l3ecl on 2011-08-11
bump

---

### Post by wojox on 2011-08-11
Have you tried blacklisting it?

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

At the end of the file add the following line:

```
blacklist intel_ips
```

Save and restart. ;)

---

### Post by .... on 2011-08-12
Temperature will fluctuate. It's not causing your issue, though. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/636045](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/636045)
Blacklisting intel_ips will make the message go away, but you also lose that feature: [http://www.phoronix.com/scan.php?page=news_item&px=NzkzOQ](http://www.phoronix.com/scan.php?page=news_item&px=NzkzOQ)

---

