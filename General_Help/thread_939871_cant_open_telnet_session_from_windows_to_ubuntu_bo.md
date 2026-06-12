---
title: "cant open telnet session from windows to ubuntu box"
date: 2008-10-06
forum: General Help
---

### Post by malanco on 2008-10-06
hi guys, i bought a backup solution named ultrabac, and i have the unix client, so i installed here in my ubuntu box, but i cant access my box from a windows 2003 server , so i tried making a telnet session between my win server and my ubuntu and i have this error:


[IMG]http://img519.imageshack.us/img519/1869/dibujool2.jpg[/IMG]


- i have open ports in my ubuntu and windows box

THANKS! :)

---

### Post by Titan8990 on 2008-10-06
Telnet is a fairly dead technology typically only used for diagnosing network issues these days. I notice you are also trying to hit a non-standard telnet port. Did you configure this properly for telnet server on the Ubuntu box?

For a much more secure, safer solution, use ssh:

sudo apt-get install ssh-server

Then you can remote in on Windows via PuTTy:

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

---

### Post by patrickballeux on 2008-10-06
The problem is not your telnet communication, it is in the client side of your ubuntu agent having a problem loading some kind of software or library.

Is that client compatible with Ubuntu (I mean explicitly)?  Because just being Unix compatible is not enough.  Ubuntu is Linux, not Unix.

Look at your logs on the ubuntu pc to see if there is something related.  

There is a line sayng: "dependent modules /unix".  That is strange on a ubuntu setup...  

You should ask people of Ultrabac is there is a Ubuntu/Linux compatible client for their software.

From this page: [http://www.ultrabac.com/kb/ux_agent.htm](http://www.ultrabac.com/kb/ux_agent.htm), it is mentionned that they support Linux...  So you should have the proper agent, make sure that you pick the right agent for Ubuntu.



Good luck!

---

