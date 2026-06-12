---
title: "Broken package manager"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by Ratscallion on 2009-03-07
Hi. I'm using Ubuntu Intrepid under Wubi. When I try to run all of the following:

[LIST]
[*]Synaptic
[*]Upgrade Manager
[*]Add/Remove Programs
[/LIST]
I get an error message.```
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```I have no idea why this is happening, nor what I can do to prevent/solve it. Thanks. Help is appreciated. Most questions regarding soft/hardware can be answered.

---

### Post by utnubuuser on 2009-03-07
try re-installing synaptic.

If you cant do it from a graphical desktop, try ctrl+alt+F1 to get to a console, then type> sudo apt-get install synapticand ctrl+alt+F7 to get back to your graphical environment.

you could also try > sudo dpkg --configure -a - make sure synaptic is closed when you run this command.

and here is  a thread [http://wiki.eeeuser.com/howto:unable_to_tparse]("http://wiki.eeeuser.com/howto:unable_to_tparse")

---

### Post by Skripka on 2009-03-07
> **utnubuuser said:**
> try re-installing synaptic

That might be a bit difficult if all the GUI front ends of apt cannot run due to a problem with dpkg or apt-get ;)


To the OP, what does Terminal spit back at you when you type:

```

sudo apt-get update

```

You'll probably get an error-what is it?

---

### Post by Ratscallion on 2009-03-09
> 
To the OP, what does Terminal spit back at you when you type:

```

sudo apt-get update

```You'll probably get an error-what is it?It used to spit back the error I posted above, though a reboot, and this command
> and ctrl+alt+F7 to get back to your graphical environment.

you could also try
```
sudo dpkg --configure -a
```did works. Thanks to [utnubuuser]("http://ubuntuforums.org/member.php?u=370166") for this :D

---

