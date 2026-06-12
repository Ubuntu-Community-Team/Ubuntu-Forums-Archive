---
title: "How the latest upgrade killed my GUI, and how I fixed it"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by kennsj on 2009-03-06
I couldn't find anything that really helped me solve this issue, so I thought I'd post here for the sake of anyone who might potentially be assisted by this method of fixing a pretty horrific problem caused by the latest Ubuntu upgrade.

Upon restarting after downloading and installing the updates yesterday, most of which appeared to relate to network security (useful and pertinent, since I'm running an Ubuntu Server domain controller/file & print server in my ICT classroom), my GUI appeared as **a mess of colours with vertical lines across the screen**.  This alternated at times with grey and black vertical lines.

Found a lot of references to troubleshooting the X-Server component, but it was all incredibly technical with a steep learning curve; one for which I don't have time at work.

The solution I found for myself was a decidedly intuitive one.  Here's what I did...

[LIST=1]
[*]Press "Esc" at startup and enter Recovery Mode.
[*]Drop to root command line.
[*]Install Gnome by typing...
```
aptitude install gnome
```
[*]Uninstall Ubuntu Desktop from the command line by typing...
```
aptitude remove ubuntu-desktop
```
[*]Restart the system by typing...
```
reboot
```
[/LIST]

It was a massive relief to see my regular GUI login screen again when the computer finished restarting.

I have now made system updates entirely manual.  The server's system is working, so it can stay just the way it is for now.

Hope that helps somebody with a similar problem.

---

