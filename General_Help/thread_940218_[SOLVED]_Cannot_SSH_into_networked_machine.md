---
title: "[SOLVED] Cannot SSH into networked machine"
date: 2008-10-06
forum: General Help
---

### Post by rugbert on 2008-10-06
Im running Ubuntu 8.04 on both boxes (one is server edition), but I cannot ssh into my other machine. I could with fedora 8 but now that ive made the switch I can no longer ssh over.

Terminal lets me input my password, but then it just hangs. What gives?

 also - I can ssh in though my DynDNS entry tho....

---

### Post by taladan on 2008-10-06
may sound like a dumb question, but is this a fresh install?  If so, you'll have to add the ssh server via

```
sudo apt-get install openssh-server
```

Though if it's prompting you for a password, that sounds like the port is open.  Check 
```
ps -ef|grep sshd
```
and make sure the service is running if you know it was installed.

Tal

---

### Post by thinkdez on 2008-10-07
If you migrated to Ubuntu from Fedora make sure that the Client's known_hosts [located in your user folder /home/usernamee/.ssh/known_hosts] file has the correct information in regards to the new machine.  It may be worthwhile to remove the file and try to ssh to the migrated system again.

---

### Post by rugbert on 2008-10-07
> **thinkdez said:**
> If you migrated to Ubuntu from Fedora make sure that the Client's known_hosts [located in your user folder /home/usernamee/.ssh/known_hosts] file has the correct information in regards to the new machine.  It may be worthwhile to remove the file and try to ssh to the migrated system again.

yeeeea that did it, thanks!

---

### Post by rugbert on 2008-10-07
unsolved, i got home from work and even tho im using the same laptop to ssh in, it once again hangs after inputting the password...

---

### Post by Mister.Vash on 2008-10-07
What may help is making ssh verbose for that connection add -vvv to the command - for example

ssh -vvv destinationmachine

just add the -vvv right after ssh and prior to what you are currently using


It will output a lot of information, and they may indicate what the exact issue is

---

### Post by rugbert on 2008-10-08
```

kyle@192.168.0.11's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
hangs here

```

Ill do the same at work when I get there

---

### Post by Mister.Vash on 2008-10-09
Take a look at this thread and see if the solution works:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/237894](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/237894)

It is a report of the client hanging at the same point, "channel 0: open confirm rwindow 0 rmax 32768"

---

### Post by rugbert on 2008-10-12
> **Mister.Vash said:**
> Take a look at this thread and see if the solution works:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/237894](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/237894)

It is a report of the client hanging at the same point, "channel 0: open confirm rwindow 0 rmax 32768"

this was exactly it, the restricted wl driver for my wireless chipset was the culprit, thanks!

---

