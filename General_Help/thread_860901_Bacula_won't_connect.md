---
title: "Bacula won't connect"
date: 2008-07-16
forum: General Help
---

### Post by Nigel74 on 2008-07-16
I have set up Bacula 2.2.8 on an Ubuntu 8.04.1 server. I am trying to connect to a 2.2.8 client on my Windows XP machine.

In bconsole, every time I try to estimate how long the backup is going to take I get an error message. They vary from:

JobId 0: Fatal error: Unable to authenticate with File daemon at "XXXXX:9102". Possible causes:
Passwords or names not the same or
Maximum Concurrent Jobs exceeded on the FD or
FD networking messed up (restart daemon).

or, if I restart the FD daemon:

Fatal error: Error sending Hello to File daemon at "XXXXX:9102". ERR=Connection reset by peer
Error: bsock.c:306 Write error sending 36 bytes to Client: XXXXX:9102: ERR=Connection reset by peer

Usually the ERR is Broken Pipe.

I have looked round the Internet, but with this problem Google has decided not to be my fried. Can anyone, anywhere, help?

I have turned off the firewall on my XP machine, and I can telnet on that port.

Thanks,

Nigel

---

