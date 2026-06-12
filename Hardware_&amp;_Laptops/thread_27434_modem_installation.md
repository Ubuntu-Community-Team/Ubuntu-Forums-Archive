---
title: "modem installation"
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by simca on 2005-04-16
Hi eyeryone,

a few days ago I switched after several years with Debian Sid to Kubuntu (Hoary) and I must say I'm deeply impressed.
Now I convinced my father-in-law to install Kubuntu on his IBM Thinkpad R50e.
I'm impressed again...  :) 
Almost everything works just out-of-the-box. Almost...
The internal modem doesn't.

So here I am, not having installed a modem on a laptop before and not being the trial-and-error type of guy I'm a little bit lost, maybe someone can give a short summary of how to get that thing to work.

Here is what I found out:

lspci says:
```
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (I CH4 / I CH4-L / I CH4-M) AC'97 Modem Controller (rev01)
```

When I start kppp and try to setup a modem the program tries to connect to /dev/modem which doesn't exist.

Do I have to create /dev/modem by myself?
Do I have to install something magical to get the modem recognized?

As i said: I'm a little bit lost...  :smile: 

Maybe someone could help?

Regards

---

### Post by az on 2005-04-16
Download and install the sl-modem packages here. they should work.  They are for the stock Hoary kernel.

[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)

---

### Post by simca on 2005-04-16
[QUOTE=azz]Download and install the sl-modem packages here. they should work.  They are for the stock Hoary kernel.

[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)[/QUOTE]

Yep, just found them myself...  :) 

Installation works just fine, kppp detects a modem at /dev/modem but stops dialing with "NO DIALTONE".
(The cables are connected...  ;-) )

What am I doing wrong?

Regards

---

### Post by kaltertee on 2005-06-17
Please be carefull, 
(rev 1) ist not the same like (rev 3).
I guess for (rev 1) only the Linuxant driver is working, but you have to pay for or just use it with 14,4 k.
If someone has an other solution please post it!
Simon

---

### Post by az on 2005-06-17
[QUOTE=kaltertee]Please be carefull, 
(rev 1) ist not the same like (rev 3).
I guess for (rev 1) only the Linuxant driver is working, but you have to pay for or just use it with 14,4 k.
If someone has an other solution please post it!
Simon[/QUOTE]

The linuxant driver is for Conexant modems.  This is not the case.

---

### Post by kaltertee on 2005-06-27
That's not the case???
```
sl108@natan:~$ lspci | grep Modem 0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) sl108@natan:~$ lspci -n | grep 1f.6 0000:00:1f.6 0703: 8086:24c6 (rev 01) 
``` 
That's my modem and it ist supported from Linuxant!!!
[Linuxant supportet](http://www.linuxant.com/drivers/hsf/index.php) 
You should have read up on this beforehand.
Simon

---

### Post by az on 2005-06-27
Sorry.  Good luck with your modem driver.

---

### Post by towsonu2003 on 2006-05-08
let me be the bad guy who direct future readers to the wiki page (second link in my signature)...

sidenote: you never know what is what without scanmodem tool

---

