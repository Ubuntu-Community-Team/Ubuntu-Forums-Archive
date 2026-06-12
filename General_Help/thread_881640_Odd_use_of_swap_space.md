---
title: "Odd use of swap space"
date: 2008-08-06
forum: General Help
---

### Post by Jimmey on 2008-08-06
Any ideas why my system would use swap over normal RAM space like this?
[[IMG]http://img180.imageshack.us/img180/1456/screenshothw5.th.png[/IMG]](http://img180.imageshack.us/my.php?image=screenshothw5.png)

I was running a render with Yafray at the time.

Thanks

---

### Post by TenPlus1 on 2008-08-06
Try editing your /etc/sysctl.conf file and adding these line to the end:

# Virtual memory control (0 to 100 - 0=use physical, 60=default, 100=use virtual)
vm.swappiness=0

---

### Post by Yannick Le Saint kyncani on 2008-08-06
Linux will swap out unused pages to get some cache memory, to increase performance.

You can see how memory is used with "free -m".

---

