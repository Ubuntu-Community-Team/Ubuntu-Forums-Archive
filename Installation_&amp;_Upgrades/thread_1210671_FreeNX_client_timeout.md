---
title: "FreeNX client timeout"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by mexus on 2009-07-11
I have 2 server both running Ubuntu Server 9.04 + KDE,
same configs, same versions of FreeNX
One is AMD 64 / ATI graphicsq the other one is Intel i386 / Intel graphics.

I can connect to the one running on AMD 64 (X86_64 ubuntu), but
i get this error on the client (server running on Intel i386 (i386 ubuntu) :

> NX> 127 Sessions list of user 'user' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: user
NX> 105 startsession  --link="wan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --[/CODE]shpix="1" --strict="0" --composite="1" --media="0" --session="user.a-domain.com" --type="unix-kde" --geometry="1280x994" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1280x994x32+render" 

NX> 280 Exiting on signal: 15


Never got freenx to start a session.

Error on server (LOG LEVEL 7)
> HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: user
NX> 102 Password:
Info: Auth method: ssh user@127.0.0.1's password:
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 716 Slave mode started successfully.
nxnode_reader: NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
nxnode_reader: NX> 716 finished
nxnode_reader: NX> 1001 Bye.

NX> 103 Welcome to: user.a-domain.com user: user
NX> 105 listsession --user="user" --status="suspended,running" --geometry="1280x1024x32+render" --type="unix-kde"
NX> 127 Sessions list of user 'user' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: user
NX> 105 startsession  --link="wan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="user.a-domain.com" --type="unix-kde" --geometry="1280x994" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1280x994x32+render"

Info: Using /etc/nxserver/nxacl to change session parameters or deny session.
&link=wan&backingstore=1&encryption=1&cache=16M&images=64M&shmem=1&shpix=1&strict=0&composite=1&media=0&session=user.a-domain.com&type=unix-kde&geometry=1280x994&client=winnt&keyboard=pc102/en_US&screeninfo=1280x994x32+render&clientproto=3.2.0&login_method=SSH&user=user&userip=censored&uniqueid=censored display=1001&host=127.0.0.1
nxnode_reader: NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
server_nxnode_echo: NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
nxnode_reader: NX> 700 Session id: user.a-domain.com-1001-censored
nxnode_reader: NX> 705 Session display: 1001
Info: Closing connection to slave with pid 5672.
NX> 1004 Error: Session did not start.
Info: Closing connection to slave with pid 5672.


---

