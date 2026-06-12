---
title: "Change hardware in my server"
date: 2015-01-27
forum: Hardware
---

### Post by guldberg72 on 2015-01-27
Hello guys/girls. i am getting aned mb today with an integrated cpu. i was wondering if it is possible just to change the hardware without needing to reinstall the whole system?
I am running a Ubuntu 14.04 LTS Headless server

---

### Post by sandyd on 2015-01-27
> **guldberg72 said:**
> Hello guys/girls. i am getting aned mb today with an integrated cpu. i was wondering if it is possible just to change the hardware without needing to reinstall the whole system?
I am running a Ubuntu 14.04 LTS Headless server

Generally, if the hardware is supported by Ubuntu, it can be changed. Attention must be made to hardware such as video cards if proprietary drivers are installed.

For example, if you install an ATI graphics card and move to Nvidia, you should remove the ATI proprietary driver beforehand if you have it installed. Other hardware such as RAM, and HDD can easily be added. If you are changing the HDD, you will have to make sure that the /etc/fstab file is updated with your new partitions.

---

### Post by guldberg72 on 2015-01-27
well i am only going to change the mb and the cpu there is integrated in the mb. and the server is running on a headless system so the video card shouldt be a problem :)
I am going to give it a try

---

### Post by guldberg72 on 2015-01-27
well everything worked as expected :D i just had to change the network interfaces file to another ethernet port.
is there a command to test if everything is working ?

---

### Post by tgalati4 on 2015-01-27
```
uptime
```

---

### Post by guldberg72 on 2015-01-28
i am just getting this output ? there is no errors or check marks?

```
daniel@techknight:~$ uptime
 20:20:39 up 8 min,  1 user,  load average: 0.13, 0.09, 0.05


```

---

### Post by SeijiSensei on 2015-01-28
You can look at /var/log/syslog to see if it reports any errors.  I suspect you're fine.

---

### Post by tgalati4 on 2015-01-29
Wait a year and run *uptime* again.  If *uptime* is near a year, then you are OK.

---

