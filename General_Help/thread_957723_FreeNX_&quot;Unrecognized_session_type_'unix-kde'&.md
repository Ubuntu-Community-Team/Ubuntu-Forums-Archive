---
title: "FreeNX &quot;Unrecognized session type 'unix-kde'&quot;"
date: 2008-10-24
forum: General Help
---

### Post by KNO3 on 2008-10-24
Hello,
I am trying to setup a freenx server on my Ubuntu Server Edition.
I have installed kde4 by the command```
sudo apt-get install kubuntu-kde4-desktop
```
And have installed freenx following this guide: [http://www.drtek.ca/freenx-server-ubuntu-hardy](http://www.drtek.ca/freenx-server-ubuntu-hardy)
I am now trying to connect to a kde session through the nx client for windows, and it seems to connect fine, and then just as the window begins to load (showing the NX logo), it terminates.
Here is the log of the connection:
```
Info: Display running with pid '444' and handler '0xe06ce'.

NXPROXY - Version 3.2.0

Copyright (C) 2001, 2007 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '4700'.
Session: Starting session at 'Fri Oct 24 20:52:57 2008'.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-kde'. Assuming agent session.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using pack method 'adaptive-9' with session 'unix-kde'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '11000'.
Session: Session started at 'Fri Oct 24 20:52:57 2008'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Fri Oct 24 20:52:59 2008'.
Session: Session terminated at 'Fri Oct 24 20:52:59 2008'.
```
The line saying that 'unix-kde' is an unrecognised session concerns me.  Is there something I need to do to point freenx at my kde4 installation? Or can anybody think of anything else that could be going wrong?
Thanks in advance!

P.S. Does anybody know of a way in which freenx can be used to broadcast the current/first desktop session (the one open on the screen of the computer) like vnc can?  I have heard of a way which is aparently not very effective of tunneling an vnc connection through the an nx connection, can anybody think of a better way, or if not, can they give me an idea as to what this method entails?

---

### Post by KNO3 on 2008-10-24
anyone have any ideas? please?

---

