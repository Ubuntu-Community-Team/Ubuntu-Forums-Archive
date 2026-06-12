---
title: "HP printer prints more than one copy randomly"
date: 2013-02-12
forum: Hardware
---

### Post by yurykom777 on 2013-02-12
If a print job was sent remotely to HP printer, it prints more than one copy randomly

Please need help! Tired of wasting time and paper )

---

### Post by tgalati4 on 2013-02-12
That is strange.  Open a terminal, post the output from:

```
lpstat -a -r -l
```

Perhaps you have a shared printer with the same name such that a single job gets multiplied to two printers, but they are really the same physical printer.

If this is not the case, it's not difficult to delete the printer and recreate it.

Sometimes cups needs a restart or a reboot helps.  Describe randomly--does it happen once every 10 print jobs? Or every other print job?

What is the model of the printer?  HP printers have generally poor build quality, so it's possible that the printer processor is asking for resubmit because of data errors.  Check the cabling--reseat connections.

---

### Post by yurykom777 on 2013-02-13
Thanks for the interest.
tgalati4, I think that the problem has nothing to do with your assumption.

Unfortunately recreation or cups restarting doesn't help...

Randomly means that it prints nearly every job twice or even three times, the other time it might print properly or with rare job duplication...
Can't find the reason why it happens so.

Printer is HP - 1020

My guess now that it might be because of low internet speed. When I send a job to a printer via Internet PC doesn't receive the information that job has already printed and resends the same job. 

If this is so, how to fix this?
 If it can't be the reason, then what is the reason?? Please, need help

---

### Post by tgalati4 on 2013-02-13
If you plug the printer into your machine directly using a USB cable, do you get double prints?

I would try upgrading the firmware of the printer.  Again, my experience with HP printers is there is a lot of crap out there.  The linux drivers are generally pretty good, rarely do you read about poor print quality, or lack of print options under linux.  But you do see a lot of posts and reviews about random problems that are isolated to poor hardware.

By low internet speed, I assume you mean low Ethernet/TCP/IP speed, since I assume you are printing locally on a LAN--local area network.  Are you hooked up with 10Mb or 100Mb routers?

---

### Post by yurykom777 on 2013-02-14
Probably It's better to describe the whole situation.
PC1 works as a server (installed NX server).
PC2 works as a client. (It is situated pretty far from PC1)
Printer is plugged into PC2.
If one prints from PC2 it's okay, but if one prints from PC2 during NX-session (running on PC1) using IPP  he gets double prints ((

Sorry if I it was confusing. Still hope for your help

---

### Post by tgalati4 on 2013-02-14
I'm not familiar with NX-server, but a quick wiki review tells me that it's an older remote desktop technology.  What is the operating system on PC1?  Can you share the printer on PC2 by "publishing" the printer?  You should be able to print to your Color Laserjet by sharing the printer with SAMBA, and this will work with linux, mac, and Windows.  I'm not entirely sure how you are printing with NX-server.  Are you logged into PC2 (What operating system are you running on PC2?) using NX and then trying to print from there?

I'm thoroughly confused.

Somehow I didn't guess the network configuration from your original post.

---

