---
title: "FreeNX/SSH problem"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by binaryPanda on 2009-01-06
Hey,
I know this has been done to death with the amount of queries about the place but I've been going through steps all afternoon trying to sort this out here:
Installed everything fine through some guides and set up a custom (client) key then transfered to the laptop.
I'm getting an error about the public key while trying to ssh over.

/var/log/nxserver say:

HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: panda
NX> 102 Password: 
Info: Auth method: passdb ssh panda@127.0.0.1's password:
Permission denied (publickey,password).

FREENX> 716 Slave mode failed to start.
Info: Closing connection to slave with pid 11422.

NX> 404 ERROR: wrong password or login
NX> 999 Bye

User/Password I set is correct in accordance to "sudo nxserver --listuser"

:confused::confused:

---

