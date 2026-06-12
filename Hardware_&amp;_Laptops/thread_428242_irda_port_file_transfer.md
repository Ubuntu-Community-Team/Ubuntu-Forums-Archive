---
title: "irda port file transfer"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by pininy on 2007-04-30
Hi,

Currently using 7.04 on a X60, how do i enable file transfer via infrared port? I've installed irda-ulits, but ircp didn't work. Am trying to transfer some files from my mobile phone to  my laptop.

able to get interaction 
here's my irdadump

58:55.841539 xid:rsp 08a3eff3 < 7ef1cfda S=6 s=2 Nokia 6600 hint=9225 [ PDA/Palmtop Modem Telephony IrCOMM IrOBEX ] (27) 
08:58:55.849956 xid:cmd 08a3eff3 > ffffffff S=6 s=3 (14) 
08:58:55.937936 xid:cmd 08a3eff3 > ffffffff S=6 s=4 (14) 
08:58:56.025962 xid:cmd 08a3eff3 > ffffffff S=6 s=5 (14) 
08:58:56.113971 xid:cmd 08a3eff3 > ffffffff S=6 s=* thomas-laptop hint=0400 [ Computer ] (29) 
q
08:58:58.586038 xid:cmd 08a3eff3 > ffffffff S=6 s=0 (14) 
08:58:58.674037 xid:cmd 08a3eff3 > ffffffff S=6 s=1 (14) 
08:58:58.753693 xid:rsp 08a3eff3 < 7ef1cfda S=6 s=1 Nokia 6600 hint=9225 [ PDA/Palmtop Modem Telephony IrCOMM IrOBEX ] (27) 
08:58:58.762027 xid:cmd 08a3eff3 > ffffffff S=6 s=2 (14) 
08:58:58.850045 xid:cmd 08a3eff3 > ffffffff S=6 s=3 (14) 
08:58:58.938063 xid:cmd 08a3eff3 > ffffffff S=6 s=4 (14) 
08:58:59.026070 xid:cmd 08a3eff3 > ffffffff S=6 s=5 (14) 
08:58:59.114054 xid:cmd 08a3eff3 > ffffffff S=6 s=* thomas-laptop hint=0400 [ Computer ] (29) 



many thanks!

---

### Post by pininy on 2007-04-30
hi guys,

i did a sudo synaptic and install most of the obex, and now it works..

many thanks!

---

### Post by semgok on 2007-06-01
Hi.I am using Ubuntu 6.06 and Sony Ericsson K510i.I installed irda-utils and openobex-apps to my machine.

I have successfully recieved files from my mobile phone but i cant send any file to my mobile phone.

when i use irxfer,i have received file succesfully but when i use

irxfer deneme.X(jpg,mp3,etc...)

i cant send file to mobile phone.The fallowing message is printed:

-------------------

# irxfer bennyhill_0.mp3
Send files to and receive files from win95

name=bennyhill_0.mp3, size=134524936
PUT failed: No such file or directory

PUT successful

---------------

What can i do for solve this problem ?

Thanks all.

---

