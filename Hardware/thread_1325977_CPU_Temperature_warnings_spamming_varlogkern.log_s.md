---
title: "CPU Temperature warnings spamming /var/log/kern.log since upgrade to Karmic"
date: 2009-11-14
forum: Hardware
---

### Post by mbobak on 2009-11-14
Hi all,

I'm hitting bug [#463276]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/463276") and it's killing my system performance.

Does anyone have a workaround?  How can I stop those messages being logged?

Thanks,

-Mark

---

### Post by nixscripter on 2009-11-18
You can change that in **/etc/syslog.conf**. Comment out the line:

```

kern.*                          -/var/log/kern.log
```

It'll suppress all kernel messages. You can add another rule to perhaps add back all the levels if you don't want that.

Hope this helps.

---

### Post by abiheiri on 2010-03-03
[LIST=1]
[*][SIZE=3]edit /etc/rsyslog.d/50-default.conf[/SIZE]
[*][SIZE=3]comment out (eg. "#kern.*     -/var/log/kern.log")[/SIZE]
[*][SIZE=3]restart rsyslog (eg. "sudo restart rsyslog")[/SIZE]
[/LIST]

---

