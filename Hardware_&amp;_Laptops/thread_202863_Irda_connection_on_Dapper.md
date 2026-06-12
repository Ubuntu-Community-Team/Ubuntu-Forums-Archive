---
title: "Irda connection on Dapper"
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by leeyee on 2006-06-24
Hi guys,
I'm using Dapper on my ASUS M2 laptop, and I want to connect my mobile phone SonyEricsson k508c to ubuntu via Irda. However, I don't know how to, and I even didn't find any issues referring to IRDA connection on Dapper. Please you guys help me if you have any experience on this issue. Thank you in advance!

---

### Post by sandrejev on 2006-07-01
I also have a problem with irda on my laptop using Ubuntu 6.06. I have integrated irda on NAPA 8224 laptop, but it isn't listed in lshw, lsusb, lspci or any other list.

---

### Post by leeyee on 2006-07-03
Well, I'm glad to tell you that I've figured out this issue. Here are what I did:
First, install these packages with apt-get
```

sudo apt-get install ircp irda-utils openobex-apps

```
And add modules into the kernel
```

sudo modprobe irda irtty_sir sir_dev

```
If you want it add automatically when system booting, you can just write these 3 module into the /etc/modules. Here is mine:
```

[leeyee@myUbuntu:~]$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
sbp2
sr_mod
irda
irtty_sir
sir_dev

```
After these were done, you can test your irda module and will see some outputs:
```

[leeyee@myUbuntu:~]$ sudo irdadump
Password:
13:33:14.381579 xid:cmd f75971d2 > ffffffff S=6 s=0 (14)
13:33:14.471789 xid:cmd f75971d2 > ffffffff S=6 s=1 (14)
13:33:14.561776 xid:cmd f75971d2 > ffffffff S=6 s=2 (14)
13:33:14.651760 xid:cmd f75971d2 > ffffffff S=6 s=3 (14)
13:33:14.741746 xid:cmd f75971d2 > ffffffff S=6 s=4 (14)
13:33:14.831733 xid:cmd f75971d2 > ffffffff S=6 s=5 (14)
13:33:14.921881 xid:cmd f75971d2 > ffffffff S=6 s=* myUbuntu hint=0400 [ Computer ] (24)

```
These outputs indicate you that your Irda device is ready. To send files to the phone
```

irobex_palm3 /your/file/path

```
and receive from it with
```

irobex_palm3

```
Then you are there! Hope this helps!

---

### Post by Amon_Re on 2006-07-12
Hmm... i'm having a problem with irda too, my computer detects 2 serial ports at boot (ttyS0 & ttyS2) however, no matter how i try i can't attach to ttyS2 while that one should effectively be the irDA port.

I can connect to ttyS0 but there is no ir activity according to irdadump

The tty's are both detected at boot as 16550A's

---

### Post by Nightmare on 2006-09-18
For some months I installed Irda without problems but now the command "sudo apt-get install ircp irda-utils openobex-apps" makes problems. 

```
Reading package lists... Done
Building dependency tree... Done
Package ircp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ircp has no installation candidate

```

Which source I need? :confused:

---

### Post by tc10b on 2006-11-05
I'm having a problem that I never had before, I've done everything you said but everytime I try to send or recieve a file it says, "Sorry unable to connect" straight away

I dunno what to do.

---

### Post by esmerine on 2008-01-17
Maybe somebody would help me with a problem I'm having when trying to send a file from my sony ericsson through irobex. When I'm sending a file from a PC everything's fine, but vice versa phone says "no device found."

---

