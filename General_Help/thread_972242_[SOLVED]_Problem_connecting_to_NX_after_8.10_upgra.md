---
title: "[SOLVED] Problem connecting to NX after 8.10 upgrade"
date: 2008-11-05
forum: General Help
---

### Post by FizzBuntu on 2008-11-05
Hi
After upgrading from 8.04 to 8.10, my NXserver doesn't work anymore and I can't get the cause of the problem.
Authentication seems to be ok, but session does'nt start...

NX> 203 NXSSH running with pid: 789
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.0.10 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-16 - LFE
NX> 105 Hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: fizzbuntu
NX> 102 Password: ***********
NX> 103 Welcome to: macserver user: fizzbuntu
NX> 105 Listsession --user="fizzbuntu" --status="suspended\054running" --geometry="1280x1024x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: fizzbuntu
NX> 105 Start session with: --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="MacServer\040local" --type="unix-gnome" --geometry="1270x720+5+139" --client="macosx" --keyboard="query" --screeninfo="1270x720x32+render" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 9135DADE. To get detailed information about
NX> 595 ERROR: the error search for the string 9135DADE in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15

---

### Post by Peter09 on 2008-11-05
Yes,
I had this as well, I had to reinstall the NX server

---

### Post by FizzBuntu on 2008-11-05
well
I've already de-installed it (nxserver,nxnode,nxclient)
and re-installed nxclient, nxnode, nxserver

no changes...

---

### Post by rsambuca on 2008-11-05
What did the error messages log say?

---

### Post by FizzBuntu on 2008-11-06
looks cryptic to me...

Nov  6 11:22:13 macserver NXSERVER-3.2.0-16[2750]: User 'fizzbuntu' logged in from '82.239.80.3'. 'NXLogin::set'
Nov  6 11:22:15 macserver NXSERVER-3.2.0-16[2750]: Selected node host:localhost with port:22 'main::selectNode'
Nov  6 11:22:15 macserver NXSERVER-3.2.0-16[2750]: Current selected node: localhost is in status: running  'main::selectNode'
Nov  6 11:22:15 macserver NXSERVER-3.2.0-16[2750]: Selected session type: unix-gnome allowed in the profile of user: fizzbuntu 'NXShell::Static'
Nov  6 11:22:18 macserver NXNODE-3.2.0-13[2855]: ERROR: NX> 596 ERROR: NXNODE Ver. 3.2.0-13  (Error id e2DE27B) [e2DE27B] Logger::log nxnode 2893
Nov  6 11:22:18 macserver NXNODE-3.2.0-13[2855]: ERROR: NX> 596 ERROR: create session: run commands [e2DE27B] Logger::log nxnode 2893
Nov  6 11:22:18 macserver NXNODE-3.2.0-13[2855]: ERROR: NX> 596 ERROR: execution of last command failed [e2DE27B] Logger::log nxnode 2893
Nov  6 11:22:18 macserver NXNODE-3.2.0-13[2855]: ERROR: NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/fizzbuntu/.nx/C-macserver-1002-D974B58FC7F107AC69699AD0F979B715/scripts/authority' [e2DE27B] Logger::log nxnode 2893
Nov  6 11:22:18 macserver NXNODE-3.2.0-13[2855]: ERROR: NX> 596 exit value: 1 [e2DE27B] Logger::log nxnode 2893
Nov  6 11:22:18 macserver NXNODE-3.2.0-13[2855]: ERROR: NX> 596 stdout:  [e2DE27B] Logger::log nxnode 2893
Nov  6 11:22:18 macserver NXNODE-3.2.0-13[2855]: ERROR: NX> 596 stderr: xauth:  error in locking authority file /home/fizzbuntu/.Xauthority [e2DE27B] Logger::log nxnode 2893
Nov  6 11:22:18 macserver NXNODE-3.2.0-13[2855]: ERROR: NX> 596 . [e2DE27B] Logger::log nxnode 2893
Nov  6 11:22:18 macserver NXNODE-3.2.0-13[2855]: ERROR: NX> 596 init: stdin arguments: user=fizzbuntu,userip=82%2e239%2e80%2e3,uniqueid=D974B58FC7F107AC69699AD0F979B715,display=1002,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=192%2e168%2e0%2e10,encryption_mode=3,connection=local,images=32M,cache=8M,client=winnt,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,imagecompressionlevel=%2d1,imagecompressionmethod=3,shpix=1,rootless=0,composite=1,session=MacServer,shmem=1,type=unix%2dgnome,virtualdesktop=1,render=1,screeninfo=1270x720x32%2brender,keyboard=pc102%2ffr,geometry=1270x720,link=adsl Logger::log nxnode 2893
Nov  6 11:22:19 macserver NXNODE-3.2.0-13[2855]: getting agent pid: cannot read pid file '/home/fizzbuntu/.nx/C-macserver-1002-D974B58FC7F107AC69699AD0F979B715/pids/agent'. Exiting. main::get_agent_pid nxnode 8717
Nov  6 11:22:19 macserver NXNODE-3.2.0-13[2855]: directory '/home/fizzbuntu/.nx/C-macserver-1002-D974B58FC7F107AC69699AD0F979B715' moved into '/home/fizzbuntu/.nx/F-C-macserver-1002-D974B58FC7F107AC69699AD0F979B715' for investigation Logger::log nxnode 8774
Nov  6 11:22:19 macserver NXSERVER-3.2.0-16[2750]: ERROR: (exception id CB9583B6) NX> 596 ERROR: NXNODE Ver. 3.2.0-13  (Error id e2DE27B)
Nov  6 11:22:19 macserver NXSERVER-3.2.0-16[2750]: ERROR: (exception id CB9583B6) NX> 596 ERROR: create session: run commands
Nov  6 11:22:19 macserver NXSERVER-3.2.0-16[2750]: ERROR: (exception id CB9583B6) NX> 596 ERROR: execution of last command failed
Nov  6 11:22:19 macserver NXSERVER-3.2.0-16[2750]: ERROR: (exception id CB9583B6) NX> 596 last command: /bin/bash --login -c 'xauth -v source /home/fizzbuntu/.nx/C-macserver-1002-D974B58FC7F107AC69699AD0F979B715/scripts/authority'
Nov  6 11:22:19 macserver NXSERVER-3.2.0-16[2750]: ERROR: (exception id CB9583B6) NX> 596 exit value: 1
Nov  6 11:22:19 macserver NXSERVER-3.2.0-16[2750]: ERROR: (exception id CB9583B6) NX> 596 stdout: 
Nov  6 11:22:19 macserver NXSERVER-3.2.0-16[2750]: ERROR: (exception id CB9583B6) NX> 596 stderr: xauth:  error in locking authority file /home/fizzbuntu/.Xauthority
Nov  6 11:22:19 macserver NXSERVER-3.2.0-16[2750]: ERROR: (exception id CB9583B6) NX> 596 init: stdin arguments: user=fizzbuntu,userip=82%2e239%2e80%2e3,uniqueid=D974B58FC7F107AC69699AD0F979B715,display=1002,license=%28None%29,subscriptionid=None,productid=LFE,reconnect=1,balance_host=192%2e168%2e0%2e10,encryption_mode=3,connection=local,images=32M,cache=8M,client=winnt,media=0,backingstore=1,encryption=1,strict=0,clipboard=both,imagecompressionlevel=%2d1,imagecompressionmethod=3,shpix=1,rootless=0,composite=1,session=MacServer,shmem=1,type=unix%2dgnome,virtualdesktop=1,render=1,screeninfo=1270x720x32%2brender,keyboard=pc102%2ffr,geometry=1270x720,link=adsl
Nov  6 11:22:19 macserver NXSERVER-3.2.0-16[2750]: ERROR: (exception id CB9583B6) NXNodeExec::exec('startsession', 'user=fizzbuntu&userip=82%2e239%2e80%2e3&uniqueid=D974B58FC7F107AC6...', 'localhost', 22) called at handlers/nxserver.pl line 3398
Nov  6 11:22:19 macserver NXSERVER-3.2.0-16[2750]: ERROR: (exception id CB9583B6) NXShell::handler_session_start('--link="adsl" --backingstore="1" --encryption="1" --cache="8M" -...') called at NXShell.pm line 373
Nov  6 11:22:19 macserver NXSERVER-3.2.0-16[2750]: ERROR: (exception id CB9583B6) NXShell::handle_command('startsession', '--link="adsl" --backingstore="1" --encryption="1" --cache="8M" -...') called at NXShell.pm line 145
Nov  6 11:22:19 macserver NXSERVER-3.2.0-16[2750]: ERROR: (exception id CB9583B6) NXShell::run() called at nxserver.pl line 4462
Nov  6 11:22:19 macserver NXSERVER-3.2.0-16[2750]: ERROR: (exception id CB9583B6) eval {...} called at nxserver.pl line 4421

---

### Post by FizzBuntu on 2008-11-07
c'mon, nobody ?

---

### Post by rsambuca on 2008-11-07
I think you need to check your config file.  Is the authentication Key correct?

---

### Post by FizzBuntu on 2008-11-07
ok, found it
I was able to login using newly created user.
So obviously it wasn't NX but user related.
I finaly found that the .Xauthority files in the users dir where the source of the problem
mad a backup, deleted it, and 
TADAAAAAA

it worked.
The thing is a have no idea of the use of Xauthority files, hopr I didn't break anything (seems to be working fine) cause the files had some weird access rights (something about 0600).

The experience was interesting, I've learn to uninstall and re-install NX in less than 3 minutes (took me about 3 days the first time) and i'm really beginning to enjoy the good'ol command line utilities...

---

