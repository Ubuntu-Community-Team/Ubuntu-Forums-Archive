---
title: "Unlocking Users and Groups with FreeNX"
date: 2008-10-10
forum: General Help
---

### Post by john17 on 2008-10-10
Hi, I have run into a problem with remote setup of users and groups. I have a Hardy LTS server with a working version of FreeNX server (0.7.1) courtesy of daflames excellent [howto]("http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx"). My problem is that when I connect via FreeNX client the Unlock button in System --> Administration --> Users and Groups is always greyed out.  I used to use NoMachines NX Server and this had the same problem, the workaround was to use shadowing but when I try shadowing with FreeNX I get the error "Session shadowing not supported on this server".

btw vncviewer, xvnc4viewer and VNC Client 4.1 do not give access to the unlock button either.

Any help greatly appreciated

John

---

### Post by forger on 2008-10-10
Try running in terminal
```
users-admin
```
..in a normal user account, **without** gksu/gksudo/sudo/su nor in a root account..
does this fix it?

---

### Post by john17 on 2008-10-12
Hi forger,

got the following error

** (users-admin:30385): CRITICAL **: Unable to lookup session information for process '30385'

and the unlock button is still disabled

---

### Post by forger on 2008-10-12
I would file a bug report
[https://bugs.launchpad.net/bugs/+filebug](https://bugs.launchpad.net/bugs/+filebug)

---

### Post by john17 on 2008-10-12
Thanks forger,

as I was filing the bug I came across a solution from Martin Pitt.

"Remote sessions do not get a ConsoleKit entry (since they are
not on a physical console), and gnome-system-tools currently does not allow administration from remote places [1]

You should be able to change that using System -> Administration ->
Authorizations, freedesktop -> systemtoolsbackends -> Manage system
configuration, Edit, allow for anyone (Admin authentication).

[1] /usr/share/PolicyKit/policy/system-tools-backends.policy"

Catch 22 is that I need to be at the terminal in order to make these changes.  Will try it next week when I am next on the premises and if it works will mark the thread as SOLVED.

**Tried the above but still no good**

---

### Post by Euperia on 2008-10-12
This sounds similar to my issue at [http://ubuntuforums.org/showthread.php?t=945489](http://ubuntuforums.org/showthread.php?t=945489)

I've just tried changing the Administrator > Authorisations options, but unfortunately, the 'Grant' buttons are also disabled.

---

### Post by daveysan on 2008-12-05
I have just come across a similar problem. It looks like to solve this you need to revert back to the command line. I was able to add a user using the following commands:

sudo addgroup fred
sudo adduser --ingroup fred fred

This should prompt you for password and a couple of basic user fields. Hope it works for you ...

---

### Post by john17 on 2008-12-05
Daveysan,

I should have mentioned earlier that I was attempting to remotely change a password for an existing user. Could this be done at command line and if so, how?

thanks

John

---

### Post by daveysan on 2008-12-08
Hi john17

You can change an user's password on the command line via the following command

sudo usermod -p `mkpasswd harDtOcracK` <userid>

You need the exact quotes above (i.e. top left to bottom right slant)  which mean that the contents are executed and the result returned and used in the enclosing command.

Hope this helps ...

---

### Post by john17 on 2008-12-08
Thanks daveysan,

works a treat

john17

---

