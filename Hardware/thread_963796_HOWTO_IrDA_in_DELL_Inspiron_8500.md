---
title: "HOWTO: IrDA in DELL Inspiron 8500"
date: 2008-10-30
forum: Hardware
---

### Post by tosszyx on 2008-10-30
I tried to enable infrared in my laptop before and was swamped with little programs/scripts/applets etc, so I resigned myself to not have it in linux. Now I'm giving it a try once again with a little more experience and the result were satisfactory. I hope to make myself clear, and be able to answer questions if any (I'm not very experienced still, so I'll do my best).

This HOWTO is based in this two tutorials:
[http://research.nianet.org/~shenjw/webpage/howto_T23_Infrared_Debian.txt]("http://research.nianet.org/~shenjw/webpage/howto_T23_Infrared_Debian.txt")
[https://help.ubuntu.com/community/IrdaHowto]("https://help.ubuntu.com/community/IrdaHowto")

So let's start:

1.- Make sure that IrDA support in the BIOS is enabled (true by default as COM2).

2.- Install irda-utils and openobex-apps from the repositories:
```

apt-get install irda-utils openobex-apps

```

What do they do:
**irda-utils** > Userspace utilities to manage and handle infrared devices. (irattach, findchip, irdadump, irdaping and irpsion5)
**openobex-apps**> The Object Exchange protocol can best be described as binary HTTP. OBEX is optimised for ad-hoc wireless links and can be used to exchange all kind of objects like files, pictures, calendar entries (vCal) and business cards (vCard).

3.- Configure the irda-utils for our IrDA port.
In my case the port is /dev/ttyS1

3a.- Edit /etc/default/irda-utils
```
sudo pico /etc/default/irda-utils
```

Change the line reading **DEVICE="/dev/ttyS1"** to **DEVICE="irda0"**
Change the line reading **SETSERIAL=""** to **SETSERIAL="/dev/ttyS1"**
Save the file and exit pico.

3b.- Edit the file /etc/modprobe.d/irda-utils.
```
sudo pico /etc/modprobe.d/irda-utils
```

Add the following two lines to the end of the file:

```
alias irda0 nsc-ircc
options nsc-ircc dongle_id=0x09
```
Save the file and exit pico.

3c.- Edit the file /etc/modules:
```
sudo pico /etc/modules
```

Add the following line to the end of the file: **ircomm-tty**
Save and exit.

4.- Restart the IrDA deamon:

```
sudo /etc/init.d/irda-utils stop
sudo /etc/init.d/irda-utils start
```

5.- Now we should bind the Linux-IrDA stack to a IrDA port:
```
sudo irattach /dev/ttyS1 -s
```

6.- Test the port by running **irdadump**:
```
sudo irdadump
```

The result should look like this, notice that you can see when I put my phone near the computer
```
$ sudo irdadump
14:58:08.720440 xid:cmd 45182b60 > ffffffff S=6 s=0 (14)
14:58:08.808339 xid:cmd 45182b60 > ffffffff S=6 s=1 (14)
14:58:08.896328 xid:cmd 45182b60 > ffffffff S=6 s=2 (14)
14:58:08.984354 xid:cmd 45182b60 > ffffffff S=6 s=3 (14)
14:58:09.072318 xid:cmd 45182b60 > ffffffff S=6 s=4 (14)
14:58:09.160322 xid:cmd 45182b60 > ffffffff S=6 s=5 (14)
14:58:09.248360 xid:cmd 45182b60 > ffffffff S=6 s=* Coatl hint=0400 [ Computer ] (21)
14:58:11.720341 xid:cmd 45182b60 > ffffffff S=6 s=0 (14)
14:58:11.808338 xid:cmd 45182b60 > ffffffff S=6 s=1 (14)
**14:58:11.892321 xid:rsp 45182b60 < 0000efe0 S=6 s=1 Nokia 6070 hint=b125 [ PnP Modem Fax Telephony IrCOMM IrOBEX ] (27)**
14:58:11.896325 xid:cmd 45182b60 > ffffffff S=6 s=2 (14)
14:58:11.984320 xid:cmd 45182b60 > ffffffff S=6 s=3 (14)
14:58:12.072346 xid:cmd 45182b60 > ffffffff S=6 s=4 (14)
14:58:12.160324 xid:cmd 45182b60 > ffffffff S=6 s=5 (14)
14:58:12.248325 xid:cmd 45182b60 > ffffffff S=6 s=* Coatl hint=0400 [ Computer ] (21)

```

7.- Now that we have IrDA enabled, we should be able to exchange pictures/videos/etc. with the device (cellphone in my case).

To receive a file from the device, we use **irxfer** or **ircp**.

```

$irxfer
Waiting for files

Unknown event!
...........................HEADER_LENGTH = 27308
put_done() Skipped header 42
put_done() Skipped header 44
Filename = Image000.jpg
Wrote Image000.jpg (27308 bytes)

```

```

$ ircp -r /home/user/Desktop/
Waiting for incoming connection
Incoming connection
Receiving Image000.jpg...done
Disconnecting

```

8.- Congratulate yourself and drink a beer!!! 

I hope you find this useful and easy to follow.

---

### Post by bat12 on 2008-12-26
That was really helpful.Thanks a lot. However when I use ircp sais: ```
Connecting...failed
```. 
(With rxfer everythings ok)

ok, Ijust reinstall ircp-tray and works perfect

---

### Post by bat12 on 2009-01-03
New problem. As I switched to 8.10, irda stoped working. I tried the HOW TO above again I have: ```
sudo irdadump
15:10:53.671549 xid:cmd e089689d > ffffffff S=6 s=0 (14) 
15:10:53.759488 xid:cmd e089689d > ffffffff S=6 s=1 (14) 
15:10:53.847487 xid:cmd e089689d > ffffffff S=6 s=2 (14) 
15:10:53.935486 xid:cmd e089689d > ffffffff S=6 s=3 (14) 
15:10:54.023486 xid:cmd e089689d > ffffffff S=6 s=4 (14) 
15:10:54.111487 xid:cmd e089689d > ffffffff S=6 s=5 (14) 
15:10:54.199487 xid:cmd e089689d > ffffffff S=6 s=* ben-laptop hint=0400 [ Computer ] (27)
``` 
and when I put my phone near nothing changes.

Also: ```
cat /proc/net/irda/discovery
IrLMP: Discovery log:           
```

Any idea?:confused:

---

### Post by rambaldi on 2009-01-10
> **bat12 said:**
> New problem. As I switched to 8.10, irda stoped working. I tried the HOW TO above again I have: ```
sudo irdadump
15:10:53.671549 xid:cmd e089689d > ffffffff S=6 s=0 (14) 
15:10:53.759488 xid:cmd e089689d > ffffffff S=6 s=1 (14) 
15:10:53.847487 xid:cmd e089689d > ffffffff S=6 s=2 (14) 
15:10:53.935486 xid:cmd e089689d > ffffffff S=6 s=3 (14) 
15:10:54.023486 xid:cmd e089689d > ffffffff S=6 s=4 (14) 
15:10:54.111487 xid:cmd e089689d > ffffffff S=6 s=5 (14) 
15:10:54.199487 xid:cmd e089689d > ffffffff S=6 s=* ben-laptop hint=0400 [ Computer ] (27)
``` 
and when I put my phone near nothing changes.

Also: ```
cat /proc/net/irda/discovery
IrLMP: Discovery log:           
```

Any idea?:confused:


I have the same problem as *bat12*. I don't know what I can do.

---

### Post by tosszyx on 2009-02-03
Can you repeat the **irdadump**, but putting your phone near the computer (as in the edited step 6)? We can narrow the possible problems like this. 

Sorry, I'm not using 8.10. But I'll try to help

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.2
Release:        8.04
Codename:       hardy

```
```
$ uname -a
Linux Coatl 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux

```

---

### Post by wijit on 2009-03-10
Great article.
Thank you very much for your great knowledge.
I use ECS G733 labtop running Hua-Hin (Gutsy derivative) and the ir is now working.
Again, thanks.:D

---

