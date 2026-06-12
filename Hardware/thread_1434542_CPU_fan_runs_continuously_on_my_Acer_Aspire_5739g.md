---
title: "CPU fan runs continuously on my Acer Aspire 5739g"
date: 2010-03-20
forum: Hardware
---

### Post by pal.bjartan on 2010-03-20
After searching through several forums, it seems that the CPU keeps running continuously is a quite common problem when running Ubuntu on a computer. There are several suggestions to how to fix this issue, but none have worked on my laptop, an Acer Aspire 5739g, so far.

The best suggestion for a fix have I found, is propably this [**_thread_**]("http://www.robotsystematic.com/2009/ubuntu/howto-fan-control-in-ubuntu/"). However, when I tried to run pwmconfig, I got this error message:

> File /var/run/fancontrol.pid exists. This typically means that the
fancontrol deamon is running. You should stop it before running pwmconfig.
If you are certain that fancontrol is not running, then you can delete
/var/run/fancontrol.pid manually.

I checked my system monitor and I found no process called fancontrol running, so I deleted fancontrol.pid and ran pwmconfig again. Then I got the error message: 

> /usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

Can anyone help me with this issue?

---

