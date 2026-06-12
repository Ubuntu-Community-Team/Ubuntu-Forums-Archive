---
title: "Synaptic Package  manager error occured"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-06-26
when I try ro run synaptic manager I get the following error.


E: Type 'Executing:' is not known on line 1 in source list /etc/apt/sources.list.d/pidgin-ppa.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by drs305 on 2009-06-26
You can post your /etc/apt/sources.list.d/pidgin-ppa.list and we can inspect it.

Most likely you have a bad first (and maybe more) bad lines.

Every line in a source list should begin with either a "#" symbol or "deb". Anything else is erroneous.

If you would like to edit the file yourself:
```

sudo cp /etc/apt/sources.list.d/pidgin-ppa.list /etc/apt/sources.list.d/pidgin-ppa.list.bak # make backup
gksudo gedit /etc/apt/sources.list.d/pidgin-ppa.list

```

Added: This is what my pidgin *_developers_* source list looks like just to give you an idea of the format:
> deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu)  jaunty main

---

### Post by hoboy on 2009-06-26
> **drs305 said:**
> You can post your /etc/apt/sources.list.d/pidgin-ppa.list and we can inspect it.

Most likely you have a bad first (and maybe more) bad lines.

Every line in a source list should begin with either a "#" symbol or "deb". Anything else is erroneous.

If you would like to edit the file yourself:
```

sudo cp /etc/apt/sources.list.d/pidgin-ppa.list /etc/apt/sources.list.d/pidgin-ppa.list.bak # make backup
gksudo gedit /etc/apt/sources.list.d/pidgin-ppa.list

```

Added: This is what my pidgin *_developers_* source list looks like just to give you an idea of the format:

Here is waht you hace asked.

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com   67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8 cho deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu)   jaunty main

---

### Post by hoboy on 2009-06-26
problem solved.

I have used [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

---

### Post by drs305 on 2009-06-26
> **hoboy said:**
> Here is waht you hace asked.

Executing: [COLOR="Blue"]gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com   67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8[/COLOR] cho [COLOR="DarkRed"]**deb [noparse]http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu[/noparse] jaunty main**[/COLOR]

Glad you were able to get the upgrade installed. If you haven't fixed the source list, you will continue to get the same error message until you disable the repository listing or remove it.

Notice the [COLOR="DarkRed"]highlighted area[/COLOR] in what you posted. That is all that should be in the /etc/apt/sources.list.d/pidgin-ppa.list  All the preceeding in [COLOR="Blue"]blue[/COLOR] up to "cho" is part of a command that should have been run in a terminal to add the security keys. The "**cho**" was probably a part of the "**echo"** command.

---

