---
title: "NXserver help, can't log in"
date: 2008-07-23
forum: General Help
---

### Post by malfist on 2008-07-23
When I try to login remotely with my main profile I get this error:
```

NX> 203 NXSSH running with pid: 3392
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.102 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-13 - LFE
NX> 105 Hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: jerome
NX> 102 Password: ******
NX> 103 Welcome to: jerome-desktop user: jerome
NX> 105 Listsession --user="jerome" --status="suspended\054running" --geometry="1280x768x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: jerome
NX> 105 Start session with: --link="wan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="test" --type="unix-gnome" --geometry="1277x737" --client="winnt" --keyboard="pc102\057en_US" --screeninfo="1277x737x32+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 21827586. To get detailed information about
NX> 595 ERROR: the error search for the string 21827586 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15

```

Frepping /var/log/messages gives me this:
```

Jul 23 18:26:21 jerome-desktop NXSERVER-3.2.0-13[10215]: ERROR: (exception id 21827586) NXNodeExec::exec('startsession', 'user=jerome&userip=192%2e168%2e1%2e101&uniqueid=0D58F9A102E53586...', 'localhost', 22) called at handlers/nxserver.pl line 3398
Jul 23 18:26:21 jerome-desktop NXSERVER-3.2.0-13[10215]: ERROR: (exception id 21827586) NXShell::handler_session_start('--link="wan" --backingstore="1" --encryption="1" --cache="16M" -...') called at NXShell.pm line 373
Jul 23 18:26:21 jerome-desktop NXSERVER-3.2.0-13[10215]: ERROR: (exception id 21827586) NXShell::handle_command('startsession', '--link="wan" --backingstore="1" --encryption="1" --cache="16M" -...') called at NXShell.pm line 145
Jul 23 18:26:21 jerome-desktop NXSERVER-3.2.0-13[10215]: ERROR: (exception id 21827586) NXShell::run() called at nxserver.pl line 4461
Jul 23 18:26:21 jerome-desktop NXSERVER-3.2.0-13[10215]: ERROR: (exception id 21827586) eval {...} called at nxserver.pl line 4420

```

Can someone tell me how to fix this, I can log in as another user just fine, but I can't get in with my main profile.

---

