---
title: "Loss of network connection after shutdown"
date: 2008-11-10
forum: General Help
---

### Post by Goldmangun on 2008-11-10
I posted this on the network forum but didn't get any reply, so thought I would try here!

I am new to Ubuntu, but have successfully installed 8.10 under Wubi. 8.10 is therefore running as a program within Windows XP Home on a PC.

Ubuntu is working fine, but when I restart or shut down and boot back into Windows, the (wired) connection to the router is lost; the message is that a network cable is unplugged. This is definitely not the case, and if I reboot into Ubuntu it picks up the router connection again with no problem.

When shutting down Ubuntu, I notice the connection light go out on the router for the relevant socket. The remaining lights, eg - for network printer, wireless etc remain on. I am thinking that Ubuntu is somehow switching off the connection in such a way that windows is prevented from finding a connection. Any help / suggestions would be gratefully received!

Adam.

---

### Post by ago on 2008-11-10
Most likely it is not related to Wubi but it sounds like a bug, you might want to run a search in launchpad.net

---

### Post by Goldmangun on 2008-11-10
Thank you. I have checked out launchpad.net and reported this as a new bug.

Incidentally, reading your sticky FAQ, I should report that I had ACPI problems and had to install using the relevant workaround; this allows me to run Ubuntu 8.10 but not Compiz or any of the special visual effects, eg - wobbly windows.

---

### Post by Yashiro on 2008-11-11
Which network adapter is it?

---

