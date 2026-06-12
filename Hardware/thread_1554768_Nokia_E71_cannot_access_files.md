---
title: "Nokia E71 cannot access files"
date: 2010-08-17
forum: Hardware
---

### Post by noworldorder on 2010-08-17
Ubunto 10.04

I have Nokia 10.04 cell phone.  I have read that people are able to connect to it via USB on Kinux and transmit files both ways.

I can't.  When I connect it in Mass Storage mode it shows up under places>computer but I cannot open it.

Any ideas?  I have pictures of my 3 year old I want to get off there.

thanks

---

### Post by Fafler on 2010-08-17
Disconnect the phone

tail -f /var/log/messages

reconnect and watch what happens. I've many Nokia N and E phones with Linux and never experienced anthing like that.

---

### Post by noworldorder on 2010-08-17
thanks - these are the results:

[http://pastebin.com/vEhqhv7Z](http://pastebin.com/vEhqhv7Z)

---

### Post by Fafler on 2010-08-17
So, the phone identifies itself as /dev/sdb, but doesn't say anything about size or partitions. I can't verify against my own phone, because i can't seem to find my datacable just now, but try mounting it with

sudo mount /dev/sdb /mnt

and see what happens. Have you tried reproducing it on another computer? Rebooting the phone? Are you able to access the memory card from the phone?

---

### Post by noworldorder on 2010-08-17
chris@chris-laptop:~$ sudo mount /dev/sdb /mnt
mount: /dev/sdb: unknown device
chris@chris-laptop:~$

---

### Post by noworldorder on 2010-08-21
So no one can figure out why I can' access my Nokia E71 :(

I am relying on you guys... I am an absolute beginner..

---

### Post by Fafler on 2010-08-22
You could start by answering the questions i asked in my last post: Have you tried reproducing it on another computer? Rebooting the phone? Are you able to access the memory card from the phone?

---

### Post by noworldorder on 2010-08-22
> You could start by answering the questions i asked in my last post: Have  you tried reproducing it on another computer? Rebooting the phone? Are  you able to access the memory card from the phone?

Sorry Fafler my bad.

I tried this on windows 7 and it didn't work in mass storage - nothing showed up in explorer.  Also I set it to PC Suite and opened up the Nokia software and it said unrecognized usb format

Rebooting had no effect

I have no memory card

The help is much appreciated

---

### Post by PaulReaver on 2010-08-22
the only way I've been able to access the all the files on my nokia (not just the minisd) is by using bluetooth..

---

### Post by noworldorder on 2010-08-22
I don't have bluetooth....

If I got a memory card could I revmove the card and put it in my laptop to get the files off??

---

### Post by Fafler on 2010-08-23
The USB Mass Storage mode only works with a memory card. You cannot access the internal phone memory that way. Are you sure there wasn't one included with your phone? Either get one or a bluetooth adapter.

If you get a card for your phone, i'm almost sure it will work with the data cable in mass storage mode.

---

### Post by noworldorder on 2010-09-01
So I got a memory card and all is well.  Thanks for the help.

---

