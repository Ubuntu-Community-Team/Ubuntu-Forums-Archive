---
title: "[SOLVED] NX Server Suddenly Quit Working?"
date: 2008-11-14
forum: General Help
---

### Post by jrollf on 2008-11-14
I have been using nomachine nxserver (and their nxclient & nxnode) for about 6 months with no issues to access my headless ubuntu server.   Now all of a sudden when I try to log in with nxclient I get the following error message:

"The NX service is not available or the NX access was disabled on host *myhost*."

When I click on the details button I get:

NX> 203 NXSSH running with pid: 3188
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.71 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

I can still log into my server via ssh using putty from both my LAN and the Internet.  I have tried using three different PC's with nxclient (two XP, one Vista) and have been unsuccessful, I get the same error message above on all three, all of which were able to connect in the past.

As far as I know, the only changes I have made recently are:
1) I changed my password on the system and added another user to the system, but I did not set up the new user for access to the nxserver.
2) I changed my samba config from allowing public access to the file shares to allowing only specified users.  Samba seems to be working fine.
3) Any updates that Ubuntu has has published.  
 

 I have gone as far as un-installing the NoMachine NX client, node, and server, and then re-installed them from scratch using NoMachines instructions.  This is the method is what I used when it worked 6 months ago.
 

 Here is the part I don't understand.  If I issue the command:
 

 /usr/NX/bin/nxserver --status
 

 I get:
 NX> 900 Connecting to server ...
 NX> 204 Authentication to NX server failed.
 NX> 110 NX Server is stopped.
 NX> 999 Bye.
 

 Implying the server is not running, so if I issue:
 

 /usr/NX/bin/nxserver –start
 

 I get:
 NX> 500 Service already running.
 NX> 999 Bye.
 

 Implying that the server is running ?!  So what is it, is the server running or not?  Any suggestions?
 

 Thanks

---

### Post by jrollf on 2008-11-15
Figured it out, somehow my sshd_config file got messed up.  I used the config in the post:

[http://ubuntuforums.org/archive/index.php/t-449382.html](http://ubuntuforums.org/archive/index.php/t-449382.html)

And now it works again!  I still don't know how the config file changed. I don't recall doing anything with it.

---

### Post by NitroBooster on 2008-11-21
I have the same problem, but the solution offered  did not help.

> 
admin@454545:~$ sudo nano /etc/ssh/sshd_config
[sudo] password for admin:
admin@454545:~$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server sshd                                                    [ OK ]
admin@454545:~$ sudo /usr/NX/bin/nxserver --status
NX> 900 Connecting to server ...
NX> 900 ssh_exchange_identification: Connection closed by remote host
NX> 110 NX Server is stopped.
NX> 999 Bye.
admin@454545:~$ sudo /usr/NX/bin/nxserver --shutdown
NX> 123 Service stopped.
NX> 153 Stopping NX server monitor.
NX> 153 NX server monitor already stopped.
NX> 115 Shutting down.
NX> 115 Shutdown complete.
NX> 999 Bye.
admin@454545:~$ sudo /usr/NX/bin/nxserver --start
NX> 122 Service started.
NX> 999 Bye.
admin@454545:~$ sudo /usr/NX/bin/nxserver --status
NX> 900 Connecting to server ...
NX> 900 ssh_exchange_identification: Connection closed by remote host
NX> 110 NX Server is stopped.
NX> 999 Bye.
admin@454545:~$ 


---

