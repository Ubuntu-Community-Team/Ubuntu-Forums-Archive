---
title: "Wrong time after some time of inactivation"
date: 2008-11-16
forum: General Help
---

### Post by mgol on 2008-11-16
When I leave my computer (ASUS A6B00U notebook) turned on and go somewhere for a couple for hours, after going back, time is delayed. For example, I left the computer today at 3:20 and went back to it at 13:30, and I saw 7:40 as a system time, which is wrong. I had to synchronize it again by:
```
sudo ntpdate ntp.certum.pl
```

What can I do wrong? What should I do to solve it?

I'd like to use ntp synchronization and I turned in on in "Time & Date" menu, but sometimes I have a feeling it doesn't always work... Usually, to perform ntpdate, I should stop a deamon /etc/init.d/ntp. Totay, when I did it before ntdate'ing, I got:
```
$ sudo /etc/init.d/ntp stop
 * Stopping NTP server ntpd                                                                                                                 start-stop-daemon: warning: failed to kill 6051: No such process

```

---

