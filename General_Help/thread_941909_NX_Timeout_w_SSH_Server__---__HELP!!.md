---
title: "NX Timeout w/ SSH Server  ---  HELP!!"
date: 2008-10-08
forum: General Help
---

### Post by bolds on 2008-10-08
Looking for some help on NX - NoMachine
I am very new to linux, but getting better each day!

Here is the details from my Windows XP client.

NX> 203 NXSSH running with pid: 5356
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 10.60.100.15 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-16 - LFE
NX> 105 Hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: bolds
NX> 102 Password: ***********
NX> 500 ERROR: Operation timeout in communication with SSH server
NX> 999 Bye.
NX> 280 Exiting on signal: 15


I can post other details, logs, ect.  I am just looking for someone to help me fix NX.  You can reach me on MSN at [email]brandon_olds@hotmail.com[/email].

Thanks, 
Brandon

---

### Post by rsambuca on 2008-10-08
You will have to change the line in the node.conf (on your server) to allow a longer startup timeout.  Find the line that looks like this and take the number sign out.```
# The number of seconds we wait for the nxagent to start before
# deciding startup has failed
AGENT_STARTUP_TIMEOUT="60"
```

---

### Post by bolds on 2008-10-08
Rsambuca - I have attached my node.conf file.  It didn't have the section that you told me to change.  So I went ahead and added it to the file (last lines).  I also, changed the line SSHAuthorizedKey = "authorzied _keys2".  Other than that nothing has been changed.  

Let me know if you can help me find my issue.  Thanks, Brandon

---

### Post by rsambuca on 2008-10-08
Hmmm... It doesn't look like I will be able to help out any further here.  My node.conf is actually a little bit different from yours.  Must be because I am using Arch Linux at the moment, and they are obviously using different versions.

---

### Post by taigaChi on 2008-10-22
In the most recent version of NXserver, the timeout setting is no longer in node.cfg, but server.cfg

```

NodeResponseTimeout = "60"

```

However I'm suffering from the same problem after a "Disconnected" session. Afterwards trying to reconnect always times out.

Any suggestions?

---

