---
title: "Can't log onto SSH"
date: 2008-08-18
forum: General Help
---

### Post by Coruba67 on 2008-08-18
Hi guys,

Have setup openssh-server on a PC here and when I go to ssh onto it from my laptop it comes up and asks me for the password, then just seems to hang.

Any idea's?

---

### Post by amo-ej1 on 2008-08-18
Try passing the -vv option to ssh to get some more information on what ssh is doing (or supposed to be doing), I assume you can ssh to other systems without problems ? 

And you get this after entering your password ? 

Waiting a very long time doesn't solve anything ?

---

### Post by Coruba67 on 2008-08-18
Hi there...  This is what I get after I put the password in.

debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug1: Sending environment.
debug1: Sending env LANG = en_AU.UTF-8
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768


And thats where it stops.  Yeah I can SSH onto heaps of other servers.

Thanks for your help!

---

### Post by amo-ej1 on 2008-08-18
And ssh'ing to the localhost on the 'faulty' system also works properly i assume ? 

How long have you tried waiting ? It can't be something stupid like a dns timeout ?

---

### Post by Coruba67 on 2008-08-18
Yes if I SSH onto it locally its all good!  So I thought it may have been a firewall issue, but there is no firewall on that machine (and I am on the local network).

And yeah, I have left a terminal window up for ages and am connecting via IP not a DNS name!?!   Though I have tried that as well...

---

### Post by amo-ej1 on 2008-08-18
Well I doubt that it is firewall related, if it were you probably wouldn't be able to authenticate. 

Is the system healthy ? I mean there's no tremendously high load average or something preventing it to spawn a shell ? There are no magic things in your profile which get executed when logging in ?  And the logs on the remote system don't learn you anything as well ? Can you see the user being authenticated ? 

When you run who do you see the user there ? When you run ps -aux and grep for the pty allocated to the user do you see any processes ?

---

### Post by Coruba67 on 2008-08-18
No its not really running anything, a webserver I use for development, MySQL and PHP - ubuntu desktop 8.04

I am really the only person that ever connects to it.

auth.log is showing

Aug 18 23:33:32 miccy sshd[6909]: Accepted password for support from 127.0.0.1 port 41161 ssh2
Aug 18 23:33:32 miccy sshd[6915]: pam_unix(sshd:session): session opened for user support by (uid=0)
Aug 18 23:33:34 miccy sshd[6915]: pam_unix(sshd:session): session closed for user support
Aug 18 23:34:03 miccy sshd[6998]: Accepted password for support from 10.1.1.3 port 36743 ssh2
Aug 18 23:34:03 miccy sshd[7003]: pam_unix(sshd:session): session opened for user support by (uid=0)
Aug 18 23:34:46 miccy sshd[7108]: Accepted password for michelle from 10.1.1.3 port 36744 ssh2


ps -aux is showing these relevant lines

root      6876  0.0  0.0   5316  1016 ?        Ss   23:32   0:00 /usr/sbin/sshd
root      6998  0.0  0.2   8080  2640 ?        Ss   23:33   0:00 sshd: support [priv]
support   7003  0.0  0.1   8080  1536 ?        S    23:34   0:00 sshd: support@pts/0
support   7004  0.0  0.3   5740  3148 pts/0    Ss+  23:34   0:00 -bash


ps -ad is showing

 7003 ?        00:00:00 sshd
 7110 ?        00:00:00 sshd


It makes no sense to me...

---

### Post by Coruba67 on 2008-08-19
Would you believe it ended up being stupid wireless network drivers.  The buggy machine is an inspiron 1525 (dell) and the restricted drivers to get the network card running didn't handle the encryption in SSH at all...  So using NDISWrapper I installed the drivers from Dell's website and voila!  All good!

I mean what da!  Anyway all good!

---

