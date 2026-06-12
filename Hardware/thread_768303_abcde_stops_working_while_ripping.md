---
title: "abcde stops working while ripping"
date: 2008-04-26
forum: Hardware
---

### Post by kimvall on 2008-04-26
I've ripping CDs using abcde (great software) yet after a couple CDs it stops working. Here's the error message I get:

Getting CD track info... Querying the CD for audio tracks...
[WARNING] something went wrong while querying the CD... Maybe a DATA CD?
[INFO] The disc does not contain any tracks. Giving up...

After a while I gave up on there being something wrong with abcde, and that it perhaps has to do with the eject command, or perhaps cdparanoia? But I haven't been able to find a solutions.

I also googled the message but I got from that was that this problem ws solved in a previous version (but I guess not?).

Any clues anyone?

---

### Post by kajk on 2008-11-07
Hi. I played around with the abcde.conf file and then suddenly also got the same error message. finally I found out, that I set a wrong "CDPARANOIACDROMBUS" value. after I just added a # to the beginning of that line. abcde work fine again

---

### Post by andrew.46 on 2008-11-07
Hi,

There are perhaps 2 things you could try:

[LIST=1]
[*]Run abcde with sudo. This has worked in some cases.
[*]Instead of 'CDROMREADERSYNTAX=cdparanoia ' try 'CDROMREADERSYNTAX=cdda2wav'.
[/LIST]

  Andrew

---

