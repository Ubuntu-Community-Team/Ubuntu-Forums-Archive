---
title: "dependency error and problem of upgrade system variables"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by ^[H3ad-Tr1p]^ on 2009-04-26
Hi buddies,

I had had many problems with a jaunty installation and now I have some inconsistency in my filesystem. I don't know how I can find the problem because in the log of my system there isn't nothing that could tell me where I can see to solve these things

for exemple:

I've installed jaunty and I've performed an apt-get dist-upgrade

then I've put on my sources.list some additional repositories like wine ,medibuntu and googlepack

then I've installed ,for example , wicd instead of network manager and in stage of installation it returned an error which told me that wicd couldn't take the setting of network manager,and after installation I had to setting up wicd manually

now in /var/log/messages I can see these inconsistency

Apr 26 15:43:33 Amelie console-kit-daemon[2912]: WARNING: Couldn't read /proc/2911/environ: Failed to open file '/proc/2911/environ': No such file or directory
Apr 26 15:43:44 Amelie x-session-manager[3513]: WARNING: Could not launch application 'nm-applet.desktop': Unable to start application: Failed to execute child process "nm-applet" (No such file or directory)

why my system wasn't upgraded correctly?

then another singular thing:



when I've added new repositories in my sources list like medibuntu and googlepack to be able to install googleearth,picasa and skype ,I've noticed another problem

after I've performed apt-get update,where  I opened synaptic to search googleearth ,picasa or skype,I couldn't found theme inside synaptic:I mean that also if I had performed apt-get update,synaptic it seems not upgraded; it couldn't find googleearth,picasa neither skype. And this is strange

to install these software,I have to install theme with apt-get install googleearth picasa skype

why?

It seems a problem of some variables inside my system but I don't knok how I can solve this,neither why this problem was born

---

### Post by ^[H3ad-Tr1p]^ on 2009-04-27
up](*,)

---

