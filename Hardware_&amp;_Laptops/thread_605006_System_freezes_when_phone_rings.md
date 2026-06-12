---
title: "System freezes when phone rings"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by xt-lee on 2007-11-06
Hello,

I'm trying to setup a server using the desktop edition of ubuntu 7.10. The same box was running Windows before. So far I have been able to get everything running. One of the last parts of my setup is to have a Caller ID server running. I had one running before and I liked it.

The box is a:

ASUS P4C800-E Deluxe Mainboard
Intel Pentium 4  3.2 Ghz
2 GB RAM
20 & 80 GIG HDDs
256MB Nvidia FX5500 Video
Adaptec SCSI card
Onboard LAN & Sound
Creative DI5655 56k Modem
DVD-Rom
Floppy Drive

With the help of scanModem tool, I installed the drivers from: [http://tx.technion.ac.il/~raindel/ess_2.6-v0.3.tar.gz](http://tx.technion.ac.il/~raindel/ess_2.6-v0.3.tar.gz) 

I was planning on using the NcID software from here: [http://ncid.sourceforge.net/](http://ncid.sourceforge.net/)

My problem is that whenever the phone rings, the system crashes and I see the NUM Lock and SCROLL Lock lights flashing.

NcID output give me this:

Started: 11/06/2007 16:40
Server: ncidd 0.69
ncidd logfile: /var/log/ncidd.log
Processed config file: /etc/ncid/ncidd.conf
Configured to send 'cidlog' to clients.
Configured to send 'cidinfo' to clients.
Processed alias file: /etc/ncid/ncidd.alias
Verbose level: 3
CID logfile: /var/log/cidcall.log
CID logfile maximum size: 110000 bytes
Data logfile: /var/log/ciddata.log
TTY port opened: /dev/modem
TTY port speed: 19200
TTY lock file: /var/lock/LCK..modem
TTY port control signals enabled
AT Z S0=0 E1 V1 Q0
OK
Try 1 to init modem: return = 0.
Modem initialized.
AT+VCID=1
OK
Modem set for CallerID.
Network Port: 3333
Fatal: /var/run/ncidd.pid already exists
Terminated:  11/06/2007 16:40

This is from the /var/log/messages.log
kernel: [   63.227325] ess(232): ESS initialization. Country code is 0.
kernel: [   63.227328] 
kernel: [   63.227335] ess_hw(461): setting up iobase=dfe0, irq=16
kernel: [   63.227337] 
kernel: [   64.423211] ess_hw(123): ESS info:  Card is 10, RealID is 12, CardID is b, HSP_Flag is 0, No_LCS is 0, FunctionID is 4
kernel: [   64.459189] ess_hw(465): initialization sequence complete

Can someone help me out?

---

### Post by xt-lee on 2007-11-06
Just to add, I narrowed the problem to NCID. When I remove it, the system doesn't crash when the phone rings. I used the .deb package for the installation.

---

### Post by xt-lee on 2007-11-08
bumpidy bump bump!

Anybody have an idea? I'm still stuck on this.

---

### Post by jlc46 on 2008-01-15
Hi xt-lee,

I just came across your problem with NCID.  Hopefully you still monitor this thread.

The ncidd output you posted shows that another instance of ncidd was running.  When that happens, the server terminates.  This is shown by the fatal line.  You need to kill off the running version using the pid in the ncidd.pid file if you want to restart the server.

I believe the crash is due to the modem driver you are using.  Modem drivers are part of the kernel and can cause the system to crash if there is a bug in it.

A way to verify this is to use minicom to connect to the modem.  When it connects, you will get "OK" is it initializes properly.  You should then send "AT+VCID=1" to set it up for Caller ID.  Call yourself and you will either see the caller id displayed or the system will crash.  If it crashes, it is a modem driver problem.  If it does not crash, them it could be a NCID problem.

---

### Post by xt-lee on 2008-02-02
Thanks for the reply. I'll have a look at it this weekend following your instructions. I'll post back my findings as soon as I get a chance.

Thanks for answering my post, I was about to give up completely.

---

### Post by xt-lee on 2008-02-02
Alright, I tried the minicom and when a call comes in, the system crashes. From your post you say that the driver is probably causing this. There was only 1 driver available for the Creative DI5655 56k Modem. I guess I'll just change the modem for a U.S. Robotics since that was the only available driver.

Thanks for your help, if you have any other ideas let me know!

---

