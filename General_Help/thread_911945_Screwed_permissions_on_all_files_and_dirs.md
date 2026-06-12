---
title: "Screwed permissions on all files and dirs"
date: 2008-09-06
forum: General Help
---

### Post by SaturnusDJ on 2008-09-06
A few minutes ago I forgot removing one interspace in the terminal. This ended up in wrong file and dir permissions for just everything.
The story:
A Samba update was installed and I needed to reshare a folder. But to do that I had to be owner. So I did:
```

sudo chown -hR myusername / Media

```

You see the mistake? I think everything is on my username now. Ofcourse very bad for the security.

So, I tried:
```

sudo chown -hR root / Media

```

But got:
```
sudo: /etc/sudoers is owned by uid 1000, should be 0 
```

So, I did [this]("http://ubuntuforums.org/showthread.php?t=399013") in recovery mode:
```
chown root:root /etc/sudoers
chmod 440 /etc/sudoers

```

Sudo was restored.

Again I tried:
```

sudo chown -hR root / Media

```

This time it worked, but as you can guess: Everything was root then. So I didn't had any rights. My account was useless.

Booted again to recovery and did:
```

sudo chown -hR myusername /home

```

With this done my account was working again, but STILL the system isn't stable as it was before.

When starting for example 'networking' from the 'Admin' menu I get: "You are not allowed to access the system configuration"

I know much more is still not working so future problems are also a fact.

([http://ubuntuforums.org/showthread.php?t=50701](http://ubuntuforums.org/showthread.php?t=50701) could be (almost) the same, but a solution is missing there.)

Network connections are broken too.


**How do I restore this without losing anyting on the harddisks?**
Is there a special command to restore everything?


[SIZE="1"](Note that this is a server running on Ubuntu 8.04 desktop. Please, don't tell me to run the server version, I already know  but I'm new at Linux and I'm starting with desktop.)[/SIZE]



17:54
Ok, still no reply. Like I said it's a server so it should be running now.
My goals is having the important stuff up before I got to sleep.
I'll try mounting EXT3 in windows. Then backup, then reinstall. :(

Please, don't see it as solved now. More people are waiting for a solution.

---

### Post by SaturnusDJ on 2008-09-06
Nobody a suggestion?

I think I'll launch the reinstall process this hour so please post when you think you got an idea.

---

