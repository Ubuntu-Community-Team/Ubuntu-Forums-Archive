---
title: "irda not working properly using irtty-sir"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by icebite on 2006-03-20
Hello,

I have a Toshiba Tecra 9100 Laptop with an built-in ir device. I am trying to get it working in SIR mode, because that seems to be more simple than FIR setup.
I get some feedback from irdadump after **irattach /dev/ttyS1 -s**
but the info doesn´t change after putting my phone in front of the ir-port. (ir is activated on phone)

I use the irtty-sir driver & I have irda-utils installed.

/etc/modutils/irda-utils:

[B]alias tty-ldisc-11 irtty-sir
alias char-major-161 ircomm-tty
alias char-major-10-187 irnet[/B]

#----------------------------------

irdadump:

[B]10:58:27.014119 xid:cmd 172664ac > ffffffff S=6 s=0 (14)
10:58:27.104095 xid:cmd 172664ac > ffffffff S=6 s=1 (14)
10:58:27.194075 xid:cmd 172664ac > ffffffff S=6 s=2 (14)
10:58:27.284074 xid:cmd 172664ac > ffffffff S=6 s=3 (14)
10:58:27.374050 xid:cmd 172664ac > ffffffff S=6 s=4 (14)
10:58:27.464036 xid:cmd 172664ac > ffffffff S=6 s=5 (14)
10:58:27.554036 xid:cmd 172664ac > ffffffff S=6 s=* toshiba hint=0400 [ Computer ] (23)[/B]

---

