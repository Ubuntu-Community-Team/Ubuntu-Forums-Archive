---
title: "Problem with Ubuntu powered crane"
date: 2008-12-27
forum: Hardware
---

### Post by stefangr1 on 2008-12-27
As I never know what to do with all the time off during the christmas break, I decided make a meccano crane that can be remote controlled through the internet, using the Velleman k8055 usb interface card, a webcam and an old laptop with Ubuntu on it. So I build an almost 2m high crane, installed the neccesary software (apache2, php5, webcam-server), made a simple website using some php scripts and a java-applet for the webcam, and everything is (almost) working now.

Exept... the webcam almost always crashes when a command is passed to the velleman card. This happens for all software packages I tried (webcam-server, webcam, CamE, camera). Some programs give a strange error that sais it could be due to a driver issue, others just keep the webcam on while the images on the server are no longer refreshed. This is off cause a great bummer.

I have tried some php scripts that DON'T help (not even when I pause the script for say 100ms before executing the last command), like:
exec("pkill -signal Stop webcam-server");
exec("k8055 -d:1");
exec("pkill -signal Cont webcam-server");

The only thing that works (sort of) is killing the webcam-server entirely, and then restart it after a command has been passed to the Velleman card. This, however, has two cons:
1) every time a command is executed there's a 5 seconds gap in the webcam stream
2) the php script doesn't automatically close since the process it started hasn't terminated.

Does anyone have ideas for a more workable workaround or how to fix this?

---

### Post by sdennie on 2008-12-27
First, you get at least 2^10 nerd creds for this project.  I've never built an Ubuntu powered crane but, if I had done so, I would look in /var/log/syslog to help figure out your problem.  Also, sometimes for even very old hardware, a kernel update can fix things like this.  I have a 5 year old TV tuner card for my machine that only got support for Argentine TV with kernel 2.6.27.

---

### Post by stefangr1 on 2008-12-27
> **vor said:**
> First, you get at least 2^10 nerd creds for this project.  I've never built an Ubuntu powered crane but, if I had done so, I would look in /var/log/syslog to help figure out your problem.  Also, sometimes for even very old hardware, a kernel update can fix things like this.  I have a 5 year old TV tuner card for my machine that only got support for Argentine TV with kernel 2.6.27.

Thanks for the tip. However my /var/log/syslog doesn't show anything about the failure. In the mean time I managed to change my php scripts such that they do close while the process that was started continues to run, and it appears that the reloading time for "webcam-server" is much lower than that of "webcam" (<2 vs. >5 seconds), which is workable (but definately not optimal).

Any suggestions on how two usb-devices on one computer can make onother crash are, however, still welcome. 

PS.: The laptop is btw. a 1000Mhz. PIII with 256mb RAM. It has Ubuntu 7.04 from a fresh install.

---

