---
title: "NoMachine NX Server - Breezy issue"
date: 2005-11-23
forum: General Help
---

### Post by jblaty on 2005-11-23
I'm trying to install the 30-day evaluation license of NX server on Breezy.  I'm having a problem, and I'm wondering if anyone else has gotten this to work.  I'm hesitant to pay a licensing fee unless I know the software will work on Ubuntu, hence the evaluation.

I have a feeling that this is a simple issue, but can't get a response from NoMachine as to how to fix it.  Might someone point me in the right direction?

I again want to emphasize that this is NOT FreeNX, but an evaluation of the commercial version of NX Server.

I've Googled the issue, and am not finding much help on it.  Most of the Google posts are for FreeNX.

When running the latest NX Client on Windows, I'm getting the following in the connection details:

NX> 203 NXSSH running with pid: 5900
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 192.168.2.210 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.5.0-70 PE (Evaluation)
NX> 105 Hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: blarg
NX> 102 Password: *******
NX> 103 Welcome to: zen user: blarg
NX> 105 Listsession --user="blarg" --status="suspended\054running" --geometry="1600x1200x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: blarg
NX> 105 Start session with: --session="zen-linux" --type="unix-gnome" --cache="8M" --images="32M" --link="lan" --kbtype="pc102\057en_US" --nodelay="1" --encryption="1" --backingstore="never" --geometry="1280x1024" --media="1" --mediahelper="esd" --agent_server="" --agent_user="" --agent_password="" --agent_domain="" --screeninfo="1280x1024x32+render" 

NX> 399 Cannot add NX server key. Cannot create file: /home/blarg/.ssh/authorized_keys2. Error is: 13 'Permission denied'
NX> 700 Session id: zen-1006-E63C5EF0C9EF473689E5EBB1BA6A2A3E
NX> 705 Session display: 1006
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 5AAD843BF3A6B683B05812EFB2B084EC
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 5AAD843BF3A6B683B05812EFB2B084EC
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 710 Session status: running
NX> 105

---

### Post by bugmenot on 2005-11-24
the error is pretty clear isn't it?
```
NX> 399 Cannot add NX server key. Cannot create file: /home/blarg/.ssh/authorized_keys2. Error is: 13 'Permission denied'
```

make sure that the nevessary perms are set in that dir.

---

### Post by schdefan on 2005-11-24
It has been a while that i have tested the evalution version of NX Server. As far as i remember you need to copy the server.lic file to  /usr/NX/etc/
In the client GUI I choose where it says Desktop Unix and XDM (not GDM).
And I always get an errror the first time i try to login. After restarting the client I can login. 
Hope this is some little help.
schdefan

---

### Post by jblaty on 2005-11-27
FYI, I received this response from NoMachine...

-------------------------------

Many of our users are adopting Ubuntu as their Linux OS and
there have been a few issues reported  to us about its correct
functioning, one of which is the error that you have pasted
in your email.

We are currently investigating it and if there is a bug, it will
no doubt be fixed in the next maintenance release of the server.
As an evaluation user you will have the option to try it again
to confirm its suitability before deciding whether to purchase.

For your information:

[http://www.nomachine.com/ar/view.php?ar_id=AR11C00308](http://www.nomachine.com/ar/view.php?ar_id=AR11C00308)
[http://www.nomachine.com/ar/view.php?ar_id=AR08C00240](http://www.nomachine.com/ar/view.php?ar_id=AR08C00240)
[http://www.nomachine.com/supported_applications.php](http://www.nomachine.com/supported_applications.php)

Once again, we thank you for having reported the error.

Kind regards,

The NoMachine Team 

-------------------------------

FYI, I have since moved back to FreeNX, and it's working fine.  I also offered to beta test the next version of NX Server, should it support Ubuntu directly.

---

