---
title: "No Network Printing"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by jackn on 2007-07-20
I have an HP printer attached to a desktop (the server machine). I can print just fine from the desktop to the attached printer.

A laptop is on a network with the server. I cannot, however, netwrok print from the laptop.  Both machines run Feisty.

In setting this up, I've followed the [Ubuntu Wiki]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu"), using CUPS IPP and port 631.

Both computers show the proper printer icon, but the printer doesn't budge when I send jobs from the laptop.

```
tail /var/log/cups/error_log
```

on the client laptop gives:

```
No %%BoundingBox: comment in header!

```

In addition, after about three minutes of trying to process the job, the same log says:
```
 Unable to connect to IPP host: Connection timed out
```

I don't know what I should expect on the server CUPS log, but it doesn't seem at all aware of the job, as its latest entries (with 'tail'') are from an earlier time than the last job sent by the laptop.

The client's web adminstration interface, under the 'jobs' tab, says:

```
processing since Fri 20 Jul 2007 09:10:09 PM CEST 
```

The server's web interface says 'no jobs'.

What can I do? 

Thank you kindly,
Jackn

---

### Post by jackn on 2007-08-14
Network printing is working.

Ok, so what was wrong?

To cut a long story short, my networking wasn't working. 
More details [here]("http://www.linuxquestions.org/questions/showthread.php?t=573711"), post #8.

In short, as I found out later, although I had pinging and net access going, no protocols were working (nfs, ssh, rsync). Networking printing was just one of those protocols that weren't working.

I don't know what stops such protocols while allowing pinging and net access...

In any case, following [advice]("http://ubuntuforums.org/showthread.php?t=341357") to use Network Manager to run the system, all went well.

---

