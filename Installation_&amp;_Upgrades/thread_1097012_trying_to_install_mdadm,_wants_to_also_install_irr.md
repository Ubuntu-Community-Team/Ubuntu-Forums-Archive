---
title: "trying to install mdadm, wants to also install irrelevant pkgs"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by JohnDow on 2009-03-15
Hi all,

Trying to install mdadm, but apt-get says it also wants to install a whole mess of irrelevant 'dependencies'.

[INDENT]# apt-get install mdadm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  citadel-common citadel-mta citadel-server db4.6-util libcitadel1 libical0 libsieve2-1
Recommended packages:
  mail-transport-agent
The following NEW packages will be installed:
  citadel-common citadel-mta citadel-server db4.6-util libcitadel1 libical0 libsieve2-1 mdadm
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 1330kB of archives.
After this operation, 5247kB of additional disk space will be used.
Do you want to continue [Y/n]? n[/INDENT]

Just to make sure that mdadm is the raid handler and not something else:

[INDENT]tool to administer Linux MD arrays (software RAID)
The mdadm utility can be used to create, manage, and monitor MD
(multi-disk) arrays for software RAID or multipath I/O.

This package automatically configures mdadm to assemble arrays during the
system startup process. If not needed, this functionality can be disabled[/INDENT].

First question:  how do I fix this so I just get the raid package(s), not the useless stuff?

Second question:  what in the world does groupware have to do with raid arrays?

Thanks!

---

### Post by michael491 on 2009-03-21
I had this same problem. I installed mdadm through Synaptic without paying attention to the prompts. And during the install, I was being prompted for Citadel configuration. This is strange.

---

### Post by burningapathy on 2009-03-31
JohnDow,
     I just faced this same problem.  

First question:  Those extra packages I guess are called "recommended packages" which will be installed by default.  You can prevent them from being installed by using this command:

apt-get --no-install-recommends install mdadm

Second question:  The reason that groupware is installed is because mdadm recommends an MTA (mail server) installed so that it can send an email if a raid drive fails.  I guess the Citadel groupware includes an MTA and is the one chosen by mdadm/apt-get to install.  I have no idea why it wouldn't install sendmail or give you a choice, but I'm sure there's a reason.  

Best of luck,

-ba

---

