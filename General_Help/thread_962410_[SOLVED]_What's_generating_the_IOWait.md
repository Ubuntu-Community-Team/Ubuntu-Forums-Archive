---
title: "[SOLVED] What's generating the IOWait?"
date: 2008-10-29
forum: General Help
---

### Post by siddartha on 2008-10-29
The system is quite fast. The RAM is more than enough (about 20% used). The external devices are all turned off. So it's only a SATA hard drive on. The swap shouldn't be even used in these conditions.

Yet, I have quite heavy IOwaits, that might render the system almost unusable for a few minutes. How can I locate the source?

---

### Post by sdennie on 2008-10-29
You could try the following:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

Then, tail the syslog to see what is doing I/O:

```

tail -f /var/log/syslog

```

To turn that functionality off again:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

---

### Post by siddartha on 2008-10-29
I just did that and nothing weird was going on in the logs during the problems. It seems that the cute visual toys are misleading. I based my problem on the panel applet which shows IOWait all the way to 100% CPU usage.

I switched monitoring with the good old "top" and actually the IOWait is 0% during the peaks. The 90% CPU usage comes from Software Interrupts. Now how can I deal with this one? The station should be ready for some intensive graphical work and these peaks make it unusable.

---

### Post by sdennie on 2008-10-29
You might be able to debug that with the powertop tool.  It's meant for laptops and power savings but, it may know how to get the information to correlate your problem with the driver/software that's causing it.

---

### Post by siddartha on 2008-10-29
Yes, powertop was the needed app. I totally forgot about it. And the trouble maker is the wireless USB dongle. It's correct as the trafic increases so does the CPU consumption. Yet, it is weird as this was not a problem a few days ago.

---

### Post by siddartha on 2008-10-29
In the meanwhile, I have changed the kernel, just in case the driver was broken somehow and the problem persisted.

The solution was another wireless device interfering with this connection. I shut down the second device and everything went back to normal. I'm amazed.

---

