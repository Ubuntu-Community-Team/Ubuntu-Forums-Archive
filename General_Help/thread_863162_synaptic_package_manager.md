---
title: "synaptic package manager"
date: 2008-07-18
forum: General Help
---

### Post by slacksonof on 2008-07-18
help please 
im a absolute newbie to linux
and of course i have a problem, with synaptic package manager.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i have no idea what to do.
can anyone help.
castigation will be accepted
:confused:

and i was doing so well:(

---

### Post by dje on 2008-07-18
Do what it says, open a terminal (Applications >> Accessories >> Terminal) and type:
```
sudo dpkg --configure -a
```
enter your password (there will be no visual feedback when entering your password) and let it do its thing, then you should be away again :D

hope that helps,
dje

---

### Post by slacksonof on 2008-07-18
thanks for rapid reply.
its now doing its thing.
will it tell me when its finished?

signed
slack the stupid.

---

### Post by dje on 2008-07-18
yes it will return you to the terminal prompt, something like:
```
user@my-comp:~$
```

dje

---

### Post by slacksonof on 2008-07-18
ok thanks again.
guess it takes along time.

a very appreciative englishman in spain
 says bye bye.

---

