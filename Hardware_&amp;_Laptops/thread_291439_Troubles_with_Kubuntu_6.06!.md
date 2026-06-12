---
title: "Troubles with Kubuntu 6.06!"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by theJanitor on 2006-11-02
Hi Ubuntu people!

I'm always having this strange message in my shell:

*[(7 digits number).(6 dig. num.)] hdb: error code: 0x70 sense_key:0x02 asc:0x30 ascq:0x00*

Any idea?

I saw that this is not the first thread in which this problem is mentioned.
Maybe we have found the worst problem of the century because finding a good a nswer to this question seems to be impossible :-k 

shall our guru heros be able to resolve this puzzle? :mrgreen: 

Perhaps this is too difficult even for them....:rolleyes: 

Bye bye 

    Dani

---

### Post by deepwave on 2006-11-02
hdb: hd? Refers to a IDE device, and the b is the second device.

It looks like whatever your second IDE (or ATAPI CD ROM) is doing, is causing the kernel send a message to your shell.

Run dmesg, and see what that gives you.

Also run to figure out what the device is:
cat /proc/ide/hdb/model

"Nothing's too hard when you use your head" - Midgel from 321 Penguins

---

