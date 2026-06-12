---
title: "Where are the 7.10 repos??"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by Fisher on 2008-12-15
Hi, I'm using Ubuntu 7.04 as a terminal server, since the clients are pretty old machines, I could not update to a new version. 
   The problem is that I cannot install any other software from the repositories, Synaptic keep giving error 404. 
   Does the official repositories have been archived somewhere? Is there a way I can still access them? Maybe I should do a local mirror, because an upgrade is not planned for a looong time...

---

### Post by ajgreeny on 2008-12-15
7.04 is no longer supported so you can't update that, and I think that means you will find it difficult to update to 7.10 as well, if your 7.04 is not fully updated to its final update situation.  It is possible that you could try manually editing your /etc/apt/sources.list file and changing all references of feisty to gutsy, and see if that works.  You may be lucky, but then you really need to get to an even newer version as gutsy support will also go in 4 months.  Hardy would be the best for you, I think as it is supported until 2011, I believe, for the server install.

---

### Post by BUGabundo on 2008-12-15
you still can upgrade:
[https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)

u will need to change the mirrors:
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse

---

### Post by Fisher on 2008-12-15
Cool! I'll try these repos tomorrow.
I really would like to upgrade, but if I use ltsp in 8.04, the machines starts ok, but then I get a kernel panic!! They are some 486s, most of then are Pentiums S all with 16 MB of RAM. They run fine for their purpose.
If I exchange the ltsp version, I can boot ok, but I cannot connect to xdmcp, it seems since 7.10 X is using some kind of different protocol wich breaks compatibility. 
And I thought it only happens with closed source software...
Nevermind...

---

### Post by BUGabundo on 2008-12-16
> **Fisher said:**
> Cool! I'll try these repos tomorrow.

Read that page 1st, so u know exactly what to do.

> I really would like to upgrade, but if I use ltsp in 8.04, the machines starts ok, but then I get a kernel panic!! They are some 486s, most of then are Pentiums S all with 16 MB of RAM. They run fine for their purpose.

Thats a really low amount of RAM, even for LTSP, isnt it?


> If I exchange the ltsp version, I can boot ok, but I cannot connect to xdmcp, it seems since 7.10 X is using some kind of different protocol wich breaks compatibility.

Have you looked in Launchpad for that kind of bugs?

[https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

---

### Post by Fisher on 2008-12-16
> Thats a really low amount of RAM, even for LTSP, isnt it?

Not really, 16MB of RAM have been enough to run ltsp 4. It started to be used with slackware, then I changed to Ubuntu 7.04, a more user friendly distro.

> I really would like to upgrade, but if I use ltsp in 8.04, the machines starts ok, but then I get a kernel panic!!

I have talked on efnet on #ltsp. The guys in there said that the new ltsp requires a 400 MHz processor with 128 MB of RAM. Wich, in my case the machines with these specs are all standalone machines.
Am I missing something or one of the objectives of LTSP were to reuse pretty old machines, avoiding then to go to the junk?

By the way, the repos did not work, since I cannot upgrade and cannot install new software things are getting pretty bad. If I could just install build-essential maybe I could install all packages from source... 

I have heard about old Ubuntu repos on DVD. Does anyone know a place where I can download then?

---

### Post by BUGabundo on 2008-12-16
did u change the repos to gutsy instead of edgy?

I just copied it from the page, so it got wrong distro version.

It should work, since other users just used it last week, and managed to get it working.

You will need to update the system (if u didnt before EOL), and make sure Update-manager is updated (i think 7.10 already used it)

Here is the correct link with instructions.
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

for some reason i thought u were tunning 7.04 and not 7.10.

---

### Post by BUGabundo on 2008-12-16
oh wait... re-reading your OP i see that you are indeed running 7.04... so the 1st link should work... and then u have to upgrade to gutsy, and only then, to hardy.


is it to much trouble to do a clean install?

---

### Post by Fisher on 2008-12-16
Stupid typo... I should have type 7.04 instead of 7.10 on title.
I cannot use this ltsp scenario with any newer Ubuntu distro. Why? The LTSP guys say it now uses ssh to connect to xdmcp, unfortunately, breaking backwards compatibility.
I haven't tried to talk to any X guru yet. Maybe someone gets the solution.

---

