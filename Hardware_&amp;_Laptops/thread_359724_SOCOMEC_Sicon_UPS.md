---
title: "SOCOMEC Sicon UPS"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by AkumA on 2007-02-12
[Ubuntu 6.06.1 LTS Server for 64Bit on a Dual Core - Intel E6300 Core 2 Duo with a Asus/Via Motherboard p5Vd2-mx / p5v-vm dh]
Hi!
I've got a file for the UPS shutdown.
I have to created ```
/etc/upsmon/
``` and put in there this file like i red on the document that is included with the file.
This is
It's a only script called kinmon.
I have the synthax that is
```
./kinmon /dev/ttyS0 300 60
``` for shutting down the PC when UPS has low charge.
This is the document:
```
Readme of KINMON FOR LINUX

kinmon  PM1   PM2  PM3 
1.kinmon has 3 parameters, PM1&#12289;PM2 and PM3 
2.PM1: COMPORT => ttyS0 (COM1 of UNIX) or ttyS1 (COM2 of UNIX)  
It must include the path when you appoint the parameter PM1 (Ex: /dev/ttyS0)
Please be noted that PM1 must be appointed.
3.PM2: It is for setting the breakout delay time default: 60 sec. If PM2 don&#8217;t be appointed, the breakout delay time will be 60 seconds. 
4.PM3: It is for setting the UPS shutdown delay time default: 60 sec. If PM3 don&#8217;t be appointed, the UPS shutdown delay time will be 60 seconds.
./kinmon /dev/ttyS0 300 60
Note: The Caps is considered different with Low case in UNIX.

Installation step must use root LOGIN:
5.Create a directory: Please create a directory upsmon under /etc
6.Change directory to /etc/upsmon
7.Copy these 1 file (kinmon) to /etc/upsmon
8.Test &#8220;kinmon&#8221; and COM port:  
Use commend ./kinmon /dev/ttyS0 300 60  ( &#8220;./kinmon&#8221; must be included when you use this commend)
Means: ./kinmon COM1 300 seconds AC fail count and 60 seconds UPS shutdown delay. 
You will see UPS CONNECT OR NO CONNECT UPS in tty1 (ctrl_alt_F1)
If it didn&#8217;t connect UPS, you can use the commend &#8220;kill PID&#8221; to delete the process of UPSMON
Then, use commend ./kinmon /dev/ttyS1 300 60 (&#8220;./kinmon&#8221; must be included when you use this commend)
Means: ./kinmon COM2 300 seconds AC fail count and 60 seconds UPS shutdown delay. 
If it still doesn&#8217;t connect, please check the CABLE&#12289; PC and UPS are all be connected correctly.

9.After the connection confirmed, please edit the system setup file rc.local under /etc/rc.d/rc.local and add the following commend to edit rc.local:

  /etc/upsmon/kinmon /dev/ttyS0 300 60
  or
  /etc/upsmon/kinmon /dev/ttyS1 300 60
  The system will execute kinmon after restart the computer.

```

It's quite simple but i can't make it work. I've tried few thing i've found on the internet about setserial, but i think i can see the ttyS0 but i can't make the script work: it just tells me that  it can't connect to UPS.

I've also tried to substitute my serial cable..

Can someone help me? Could i make it work easily if i try with a USB cable?
Thanks

---

