---
title: "ubuntu &quot;Read Error&quot;"
date: 2014-06-04
forum: Hardware
---

### Post by giorgigongadze on 2014-06-04
when my pc booting he shows Read Error, and how fix it?

---

### Post by tgalati4 on 2014-06-04
It could be a bad disk, which is difficult to fix.  Can you boot Ubuntu and open a command terminal?  If so, post the output:

```
sudo smartctl -a /dev/sda
```

or

```
grep -i read /var/log/syslog
grep -i read /var/log/syslog.1
```

---

### Post by giorgigongadze on 2014-06-04
when my pc booting he shows this error:

[B]error: attempt to read or write outside of disk 'hd0'. 
Entering rescue mode... 
grub rescue>


how to fix it??? :(
[/B]

---

### Post by papibe on 2014-06-04
Threads merged.

---

