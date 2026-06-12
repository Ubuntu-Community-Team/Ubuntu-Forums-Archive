---
title: "Errors with mounting/reading ipods and dvd's"
date: 2008-11-12
forum: Hardware
---

### Post by tdreyer1 on 2008-11-12
I recently wiped my old Ubuntu install and did a clean install of intrepid. Now, I'm getting DBus errors in multiple places. First is when I attach my iPod touch to recharge (i don't care about mounting, it just tries to mount automatically) I get the error 

```
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
```

I get a very similar error (ie:  "org.freedesktop.DBus.Error.NoReply") every time I try to burn a dvd, and sometimes when I try to read them. After the error with the dvd's, the disc still looks mounted, but cannot be read, unmounted, or ejected.

Please let me know what additional info you need, and thanks for the help!

---

### Post by wujaklija on 2008-11-12
i have that problem too ... on hardy everything was perfect , and now on a fresh install of ibex ,for every dvd i put in dvd-rom that message appears . many times , after that message , dvd is mounted after a minute , but sometimes nothing happens ... here is whole message : "DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

---

### Post by alfa81 on 2008-11-15
Hi...I have the same problem, I do only an update from 8.04 to 8.10. I now i lost a CD/DVD reader.

The message:

-
Impossibile montare 'Nome CD'

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
-

Help please....

---

### Post by Psimon on 2008-11-15
I have the same problem  - but only on one of my drives. Thw cd/dvd mounts after about 220 to 30 seconds but I get a couple of the above messages.

---

### Post by Psimon on 2008-11-15
Sorry, make that both drives now. I didn't have this problem at first - it just appeared this morning, and so far as I know I haven't made any changes.

---

### Post by DanEdwards on 2008-11-16
> **Psimon said:**
> I have the same problem  - but only on one of my drives. Thw cd/dvd mounts after about 220 to 30 seconds but I get a couple of the above messages.

On my HP Pavillion N5420 I have pretty much the same thing.  Under Hardy everything was fine, but with Ibex I get lots of dbus errors with the DVD.  Strangly DVD movies play fine, I have problems with DVD-ROMs I have burned.  The specific error I get while trying to mount a DVD-ROM called 'Laptop is...

```
Unable to mount Laptop
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

After I get that error, the disk finally mounts.  I think a recent update may have improved it.  Because when I first upgraded to Ibex DVD-ROMs would not work at all, but DVD's would play fine without displaying any error.

---

### Post by tdreyer1 on 2008-11-19
Bump

---

### Post by hewhowatches on 2008-11-22
I get a similar error mounting DVDs burned in Brasero.

Found a bug report with same error message logged here:
[https://bugs.launchpad.net/ubuntu/+bug/295795](https://bugs.launchpad.net/ubuntu/+bug/295795)

No answers as yet whether this is a hardware, software or OS related problem, though.

---

### Post by tdreyer1 on 2008-11-26
bump

---

### Post by tdreyer1 on 2008-11-29
bump

---

### Post by tdreyer1 on 2008-12-05
bump

---

