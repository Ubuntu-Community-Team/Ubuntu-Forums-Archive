---
title: "Starting and Shutting down a server remotely"
date: 2008-10-01
forum: General Help
---

### Post by sipickles on 2008-10-01
Hi,

I have got my Ubuntu Hardy server up and running.

Two problems.

Shutdown
--------

I have a remote SSH client logged into the server. When I type 'sudo shutdown now', it begins to shutdown, then cuts to a blue screen (nearly a BSOD!) saying:

Recovery Menu
resume - resume normal boot
dpkg - Repair broken packages
root - drop to root shell prompt
xfix - try to fix xserver

No option makes any difference. dpkg doesn't install anything, xfix runs a test. No change. resume heads back to login (I should point out I have the gnome-desktop installed, being a server noob).

STARTUP
-------
I am trying to perform a WakeOnLAN. I have enabled WOL in my bios, opened port 9 on my firewall, redirected it to the server pc, made a note of my adapters MAC address.

Remotely, I am using WOL Magic Packet Sender on WinXP. I am entering all the details but its timing out. This is the same PC that can reach the server by SSH or NX (when server is on of course!).

Any ideas welcome.

Thanks

Simon

---

### Post by NT4usB on 2008-10-01
Shutdown:```
 sudo shutdown now -h
```
-h for halt. -r for reboot

---

### Post by sipickles on 2008-10-01
Thanks,

thats shutdown sorted.

For WoL, I am following this without much luck [http://ubuntuforums.org/showthread.php?t=234588&highlight=shutdown+remotely&page=3](http://ubuntuforums.org/showthread.php?t=234588&highlight=shutdown+remotely&page=3)

---

### Post by sipickles on 2008-10-02
Okay, so I have WOL working, sending the magic packet from a WinXP machine on my local network.

Really I want to do this over the internet - WoW ;)

Still got the same problem with the remote connection tho...

---

