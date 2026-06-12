---
title: "web interface for FTP client"
date: 2008-08-12
forum: General Help
---

### Post by krypton.kr on 2008-08-12
Hello,

So many apps now have a web interface to control them, cacti, torrentflux, vmware, etc...

I'm looking for a ftp client that can run on a headless box thats gui is based around a webinterface.

The reason for this is that i use my server for all my downloads, but it doesn't have X.

I could allways ssh into the box, screen into another terminal, start the FTP file transfer and then exit the screen and the shh session.

Then i can connect back to the box, enter the screen and check the status. This seems a right pain.

Surely there must be a ftp client that doesn't require X?

Many thanks

---

### Post by timcredible on 2008-08-12
install normal ftpd and then manage it with webmin.  webmin is a web interface to just about all server type applications, it's actually easier to run many server apps locally with webmin than anything else.

---

### Post by krypton.kr on 2008-08-12
> **timcredible said:**
> install normal ftpd and then manage it with webmin.  webmin is a web interface to just about all server type applications, it's actually easier to run many server apps locally with webmin than anything else.


Thank you for your reply.

I'm gonna clarify the mater a bit:

1) I have a dedicated server in a remote location with no X.

2) I want to enable it to connect to a specific FTP server and download the files I need through a web based interface (download the files on that same dedicated server, and not on the computer accessing the web interface).

3) The reason screen isn't an option is because it will be used by some people who are not familiar with a command prompt.


Thanks.

---

