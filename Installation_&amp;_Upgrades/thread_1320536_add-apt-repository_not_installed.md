---
title: "add-apt-repository not installed"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by jabbr on 2009-11-09
Hi all

I just upgraded my 9.04-server to 9.10-server (amd64) and want to add the Wine-repository back to the repositories list.

I am supposed to do this using the add-apt-repository command.

When I try this I get 
```
sudo: add-apt-repository: command not found
```

When I do a search with whereis, it turns out there is no add-apt-repository command on the machine. 
Whereis can find e.g. the apt-get command in the /usr/bin-directory, but the add-apt-repository command is not there.

How can I have this command installed?
And how can I verify there aren't any other bits-and-pieces missing after this upgrade?

-
Alwin

---

### Post by michy99 on 2009-11-09
I don't know about 64 bit, but on 32 bit, add-apt-repository is provided by the package python-software-properties.

You could always add the repository to /etc/apt/sources.list manually.

---

### Post by jabbr on 2009-11-09
That did the trick, thank you.
:popcorn:

---

### Post by arbabnazar on 2012-01-31
The solution is to install python-software-properties:

sudo apt-get install python-software-properties

---

### Post by oldos2er on 2012-01-31
Closed, necromancy.

---

