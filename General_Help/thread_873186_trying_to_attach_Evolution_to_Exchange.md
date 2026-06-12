---
title: "trying to attach Evolution to Exchange"
date: 2008-07-28
forum: General Help
---

### Post by jados1ms on 2008-07-28
I am trying to connect Evolution in Ubuntu to Exchange 2007.  I try  to add it using th connector and I get this error: Evolution Error + the server is not compatible with Exchange connector.  It says I am running exchange 5.5 when i am really running 2007.  Any thoughts would be great.

---

### Post by nlinux on 2008-08-04
Evolution does not do Exchange 2007

---

### Post by JWarren on 2008-08-10
I have the same problem.  Am running Hardy.  New to the Ubuntu world, already having lots of fun.

In dredging the net i have found lots of "stuff" about Exchange 2007 and Evolution development.  Some deliverable dates, now past have even been mentioned.

Anybody out there have comment on when the Evolution - Exchange 2007 Connector will finally makes its appearance??:confused:

---

### Post by foresto on 2008-08-28
The [OpenChange]("http://www.openchange.org/") project has been working on open source code (libmapi) that will connect to Exchange using the same network protocol that Outlook uses.  It was [recently accepted]("http://packages.qa.debian.org/o/openchange.html") into Debian's package system.  There is now a [sync request]("https://bugs.launchpad.net/ubuntu/+bug/260786") to bring that code into Ubuntu.  I have read reports that a new Evolution/Exchange connector that uses libmapi is on its way, perhaps as early as Evolution 2.23.

In short, it looks like help is on the way.  Assuming there is sufficient demand and people willing and able to do the remaining work, I'm guessing we'll see this stuff in the next few months.

---

