---
title: "[SOLVED] Auto-Starting Programs"
date: 2008-10-11
forum: General Help
---

### Post by LonelyTraveler on 2008-10-11
How do I make a program auto-start on startup?

---

### Post by Idefix82 on 2008-10-11
There are several ways, depending on what it is that you want to start up.
Here is a great tutorial on runlevels, which you need to understand if you need to start some low level stuff like some drivers:
[http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/]("http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/")

If it's a module like an ethernet or wireless driver then you can add a line starting it into the /etc/modules file.

Finally, if you click on System->Preferences->Sessions you can add programs to be started when you log into our account.

---

### Post by LonelyTraveler on 2008-10-11
> **Idefix82 said:**
> There are several ways, depending on what it is that you want to start up.
Here is a great tutorial on runlevels, which you need to understand if you need to start some low level stuff like some drivers:
[http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/]("http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/")

If it's a module like an ethernet or wireless driver then you can add a line starting it into the /etc/modules file.

Finally, if you click on System->Preferences->Sessions you can add programs to be started when you log into our account.

Thanks a lot Idefix. The session option did it for me.

---

