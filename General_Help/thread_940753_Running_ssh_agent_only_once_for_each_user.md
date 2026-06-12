---
title: "Running ssh_agent only once for each user"
date: 2008-10-07
forum: General Help
---

### Post by sdyshel on 2008-10-07
Hi, 

I'm using number of linux machines and I frequently do ssh/scp from one to another. In order to avoid typing password every time I'm using RSA authentication and I also added this to my shell profile on every machine:
```
eval `sshagent -s`
```.

So currently the problem is that every login spawns it's own copy of ssh-agent process. Is there a way to have only one ssh-agent running for my user on every machine?

---

### Post by bodhi.zazen on 2008-10-07
just add an "if" to test if ssh-agent is already running, if not start it, if so, do not start it.

---

