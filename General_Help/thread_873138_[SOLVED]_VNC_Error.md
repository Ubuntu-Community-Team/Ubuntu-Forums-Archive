---
title: "[SOLVED] VNC Error"
date: 2008-07-28
forum: General Help
---

### Post by rh10023 on 2008-07-28
Just installed Ubuntu 8.04 (been a long time Fedora/RedHat user).  Followed all the steps in the HOWTo fir Tichondrius.  But I get an error that I am not sure how to solve.  Looking in the Xvnc logs this is what I see:

Jul 28 16:15:50 intrepid xinetd[7788]: warning: can't get client address: Transport endpoint is not connected
Jul 28 16:15:50 intrepid xinetd[7789]: warning: can't get client address: Transport endpoint is not connected
Jul 28 16:15:50 intrepid xinetd[7738]: Deactivating service Xvnc due to excessive incoming connections.  Restarting in 10 seconds.

This error is occurring from static IP clients, DHCP clients and on the machine itself when I do a vncviewer localhost:1.  Any suggestions on how I can best resolve?

---

### Post by rh10023 on 2008-07-28
> **rh10023 said:**
> Just installed Ubuntu 8.04 (been a long time Fedora/RedHat user).  Followed all the steps in the HOWTo fir Tichondrius.  But I get an error that I am not sure how to solve.  Looking in the Xvnc logs this is what I see:

Jul 28 16:15:50 intrepid xinetd[7788]: warning: can't get client address: Transport endpoint is not connected
Jul 28 16:15:50 intrepid xinetd[7789]: warning: can't get client address: Transport endpoint is not connected
Jul 28 16:15:50 intrepid xinetd[7738]: Deactivating service Xvnc due to excessive incoming connections.  Restarting in 10 seconds.

This error is occurring from static IP clients, DHCP clients and on the machine itself when I do a vncviewer localhost:1.  Any suggestions on how I can best resolve?

Ended up solving this by digging and searching in the forum some more.  Came across this article:

[http://ubuntuforums.org/showpost.php?p=5229232&postcount=458](http://ubuntuforums.org/showpost.php?p=5229232&postcount=458)

This was the correct step by step guide for running VNC for me.

---

