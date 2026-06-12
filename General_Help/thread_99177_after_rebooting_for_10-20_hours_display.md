---
title: "after rebooting for 10-20 hours display"
date: 2005-12-05
forum: General Help
---

### Post by GGINIS on 2005-12-05
I have download:
ubuntu-server-5.10-install-i386.iso
after rebooting for 10-20 hours display:
[4238618.435126]hub 1-0:1.0 over-current change on port 2
....
....
.....
[4248618.565432]hub 1-0:1.0 over-current change on port 2

why?

---

### Post by Arktis on 2005-12-05
Huh?  Could you be a bit more clear?  I can't tell what you mean, and I suspect that's why you haven't gotten a reply yet.

---

### Post by GGINIS on 2005-12-05
I have download:
ubuntu-server-5.10-install-i386.iso
after install and rebooting for 10-20 hours(continuously) display:
 
[4238618.435126]hub 1-0:1.0 over-current change on port 2
 
[4238618.435126]hub 1-0:1.0 over-current change on port 2
....
....
.....
[4248618.565432]hub 1-0:1.0 over-current change on port 2
 
why?
 
 
 
what I need it is...
1) I want make compjle with cc or gcc.
2) I want have SSH, Telnet, rlogjn, nfs server.
3) I have D-link wireless usb adapter (DWL-122) I want a software or
drivers, exist? there are?
 
 
thanks a lot...

---

### Post by Arktis on 2005-12-05
Well, I hope you can understand these instructions.  What language do you speak?  Maybe you can get someone who speaks the same language as you to translate it for you.

Okay, you need build utilities to compile and install stuff?  You also need ndiswrapper to get your wireless usb adapter working?

Insert the Ubuntu CD into your computer, then open a terminal and type:
```
sudo apt-get install build-essential
```
This will install all the things you need to compile (gcc, make, etc.) from the CD.
Then type:
```
sudo apt-get install ndiswrapper-utils
```
This will install ndiswrapper from the cd.  You can use ndiswrapper to get your wireless card working.

Now you should have everything you need to get started, assuming you already have the windows driver for your wireless card.  ***If you don't have the windows driver for your wireless usb adapter, get it, because you need it.***

Then to get your usb wireless working, follow the instructions here:
[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

After you install the windows driver into linux with ndiswrapper, you may or may not need to associate the usb port that the wireless adapter is connected to with the driver.  You can do that by first using
```
lsusb
```
Then from the list, see which I.D. that your usb wireless card is on.
Then do
```
ndiswrapper -d devid driver
```
For example, if my wireless usb card is listed as 
"Bus 001 Device 004: ID 045e:0039"
and uses the broadcom driver (bcmwl5.inf), then I would do:
```
ndiswrapper -d 045e:0039 bcmwl5
```

Once again, I hope this is understandable.  Maybe someone who speaks the same language as you can help better.

[quote=GGINIS]fter install and rebooting for 10-20 hours(continuously) display:

[4238618.435126]hub 1-0:1.0 over-current change on port 2

[4238618.435126]hub 1-0:1.0 over-current change on port 2
....
....
.....
[4248618.565432]hub 1-0:1.0 over-current change on port 2

why?[/quote]

I have no idea what that means, sorry...

---

