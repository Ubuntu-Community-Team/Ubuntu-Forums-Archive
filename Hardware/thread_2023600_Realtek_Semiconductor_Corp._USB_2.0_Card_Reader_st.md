---
title: "Realtek Semiconductor Corp. USB 2.0 Card Reader stopped working"
date: 2012-07-12
forum: Hardware
---

### Post by duhfactor on 2012-07-12
Greetings,

I am very new at linux, and need help figuring out what happened with my card reader. I currently use Ubuntu 10.04 LTS Lucid Lynx, and have a Realtek Semiconductor Corp. USB 2.0 Card Reader that has worked flawlessly until just recently. I'm not aware of a specific update that may have changed things, but I always install all of the updates as I'm prompted to. I tried to search the Net for answers, but admittedly I don't understand some of the terms used, and haven't compiled anything significant, so don't have much confidence unless someone walks me through the process. I do have this information to share if it's of any help;

"damon@damon-upstairs:~$ lsusb -v | grep ID
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
Bus 001 Device 002: ID 0bda:0103 Realtek Semiconductor Corp. USB 2.0 Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
damon@damon-upstairs:~$"

Can someone give me some direction? Thanks in advance!

Damon

---

### Post by duhfactor on 2012-07-14
Any ideas please?

---

### Post by duhfactor on 2012-07-14
bump.....

---

### Post by mik01aj on 2012-07-25
I have the same problem. I have a Lenovo x100e laptop and my builtin "Realtek Semiconductor Corp. USB 2.0 multicard reader" just stopped working.

I upgraded a lot of packages yesterday, so I think that it might be a problem with one of them. Here's the list of them: [http://textbox.m01.pl/?WSga](http://textbox.m01.pl/?WSga)

When I insert a card there, I get the following in syslog, repeated all the time until I remove the card:

```
Jul 25 09:18:26 lappy kernel: [ 2696.066538] sd 1:0:0:0: [sdb] Unhandled sense code
Jul 25 09:18:26 lappy kernel: [ 2696.066550] sd 1:0:0:0: [sdb]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
Jul 25 09:18:26 lappy kernel: [ 2696.066562] sd 1:0:0:0: [sdb]  Sense Key : Hardware Error [current] 
Jul 25 09:18:26 lappy kernel: [ 2696.066574] sd 1:0:0:0: [sdb]  Add. Sense: No additional sense information
Jul 25 09:18:26 lappy kernel: [ 2696.066586] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Jul 25 09:18:26 lappy kernel: [ 2696.066606] end_request: I/O error, dev sdb, sector 0
Jul 25 09:18:26 lappy kernel: [ 2696.066618] quiet_error: 1 callbacks suppressed
Jul 25 09:18:26 lappy kernel: [ 2696.066625] Buffer I/O error on device sdb, logical block 0

```

Btw, @duhfactor: to get useful output from [FONT="Monospace"]lsusb -v | grep ID[/FONT], you have to run it with sudo.

---

### Post by mik01aj on 2012-07-30
Bump.

In the meantime, I used the same card on the same computer with a different card reader, and it worked normally.

---

