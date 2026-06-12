---
title: "3ware error"
date: 2010-06-16
forum: Hardware
---

### Post by stefi on 2010-06-16
Hello,
I have installed Ubuntu server 10.04, on 3ware raid 1 (2 x 1Tb WD Green Caviar, brand new hard drives)
Everything fine, didn't run on any problems. Installation was with no graphical stuff, only command line. 3ware card is 9650SE-2LP, Ubuntu has embedded drivers for it.

Now, doing dmesg, I see this error:
3w-9xxx: ERROR: Invalid command opcode=0x85

Usually this error is for hard drives going bad, but it is not the case, they are brand new (not that I haven't seen bad hard drives immediately after buying them from the hardware store :))

Now, I have contacted 3ware support, they think is only a codeset issue, and they ask me to have the latest firmware and drivers..
Now, my question is, how do I find out what is my system using, in terms of drivers?
I have tried lspci, dmidecode, dmesg, /var/log/boot.log , but I did not find any relevant information.
I am interested about the 3ware raid drivers, to check the version I am running against the latest version on 3ware site..

Thanks very much.

Stef

---

### Post by dabl on 2010-06-16
I would advise running a hard drive test on each drive, individually.  The fact that they are new does not mean one of them doesn't have a problem.

---

### Post by arnuschky on 2011-07-15
I found out that this error can safely be ignored:
[http://kb.lsi.com/Print16532.aspx](http://kb.lsi.com/Print16532.aspx)

Or see here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/618542?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/618542?comments=all)

---

