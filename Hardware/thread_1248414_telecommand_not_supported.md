---
title: "telecommand not supported"
date: 2009-08-24
forum: Hardware
---

### Post by ProgVal on 2009-08-24
Hello,

I'm a french user of Ubuntu, and I tryed to get solution on the french support forum, but I can't get any solution.

My problem is the fellowing:
I've a remote controller included with my HP Pavilion dv7 Notebook PC. It works with Windows, but not with Linux.
I've already tryed xbindkeys, but when I press a key, the computer doesn't react (but it react when I press a key on the key board)

What must I do?

Thank you for advance,
ProgVal

---

### Post by ProgVal on 2009-08-28
Up!

---

### Post by IcarusR on 2009-08-29
If this is an infared remote you will need to use lirc package. 
Should be in repos.
Google for info on how to setup, not easy.
Try googling "remote name & linux"
Terminal program xev detects key inputs & will tell you if input is recognized.
Check out manpages.

---

### Post by ProgVal on 2009-08-29
I already have the "lirc" packet.

---

### Post by IcarusR on 2009-08-29
Have you set lirc up ??? 
Is the remote supported by lirc ??
Have you tried my other suggestions ???

---

### Post by ProgVal on 2009-08-29
The command *$ man lirc* don't say anything.

And I can't find anything on Google...



And I don't understand the other things you said...


EDIT: someone just said me to see this link: [http://lirc.sourceforge.net/remotes/hp/HSTNN-PRO7](http://lirc.sourceforge.net/remotes/hp/HSTNN-PRO7) But... what is it?

---

### Post by IcarusR on 2009-08-29
OK so there is no installed manpage. But is here [http://www.lirc.org/html/]("http://www.lirc.org/html/")

The page you linked is an lircrc for an HP HSTNN-PRO7 remote. If you read the lirc manual you will see that each remote need one of these files in order to work.

> And I can't find anything on Google...

Funny I got 750 results for "configuring lirc" .... Think out of the box !!

"setting up lirc" gets over 5000 results.

---

