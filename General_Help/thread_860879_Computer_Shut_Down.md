---
title: "Computer Shut Down"
date: 2008-07-16
forum: General Help
---

### Post by andrecamp on 2008-07-16
Hi,

Every now and them my computer just randomly shuts down completely. I am not sure if it is the power supply acting up because of aging or if it because of Ubuntu or some malfunction or virus. 

When I had Windows, which was about a month ago, this never happened. :S

---

### Post by lisati on 2008-07-16
Most likely: mixed up settings or possibly power supply problems
Least likely: virus

---

### Post by iaculallad on 2008-07-16
> **andrecamp said:**
> Hi,

Every now and them my computer just randomly shuts down completely. I am not sure if it is the power supply acting up because of aging or if it because of Ubuntu or some malfunction or virus. 

When I had Windows, which was about a month ago, this never happened. :S

You could try looking for the system log files for any generated error:

> 
/var/log/syslog
/var/log/messages
/var/log/debug

Or you could try the dmesg command if it shows any irregularities:

```
dmesg
```

---

### Post by andrecamp on 2008-07-16
> /var/log/syslog
/var/log/messages
/var/log/debug 

All of those are zipped up and there are many of them. Like syslog.01, up to about syslog.03 and the same with all the others.

Also, I used that "dmesg" and I didn't see anything that looked  irregular and it loaded very fast. I know usually when there is an error, it might have loaded slow. :S

Also, when I say shut off, I don't mean going through the shut down process. I mean shut off, like I wonder if the electricity went out. But i know the electricity didn't go out because my speakers and my external hard drive are still on.

---

