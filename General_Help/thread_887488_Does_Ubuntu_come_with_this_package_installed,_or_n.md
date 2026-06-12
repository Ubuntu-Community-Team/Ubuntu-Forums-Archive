---
title: "Does Ubuntu come with this package installed, or not?"
date: 2008-08-12
forum: General Help
---

### Post by jhsachs on 2008-08-12
As part of the setup process for my new Ubuntu system (v8.04), I'm trying to install and configure Amanda, the tape backup application.

Following Amanda's setup instructions, I found that the first thing I might have to do was install xinetd.  I found that it was not installed, so I proceeded to install it.

I was taken aback when apt-get gave me a warning that installing xinetd required removal of openbsd-inetd, and Amanda depended on that. This was my first hint that the Ubuntu distribution came with Amanda already installed. I hoped I had not messed up my system.

This morning I tried to configure Amanda and discovered some anomalies that led me to search the entire file system for file names containing 'Amanda'.  I found that --

-- The man pages for Amanda are there.

-- A lot of other files, such as configuration files and shared objects, are there.

-- the Amanda user, required to run the server or client, is not defined.

-- only one of the several Amanda executables is there: _amandad_, which I presume is a daemon.

-- when I try to run the commands described in the Amanda configuration instructions, I get "command not found."

It appears that Ubuntu comes with Amanda partly installed, but not completely.

Does this make sense?  What does it mean; how should I proceed? The obvious next step is to try to install the Amanda package, but I'm concerned that if I make more changes without understanding what is going on I could make things worse.

---

### Post by louieb on 2008-08-12
If you look in System>Administration>Synaptic you will find packages
**amanda-server amanda-common **and [B]amanda-client.

[/B]If the box next to them is green then that package has been installed. If not then right click a choose install. 

Don't use amanda myself but by using Synaptic that should get it installed and ready to configure and use.

Good Luck.

---

