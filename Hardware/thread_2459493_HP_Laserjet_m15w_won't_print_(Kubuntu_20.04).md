---
title: "HP Laserjet m15w won't print (Kubuntu 20.04)"
date: 2021-03-19
forum: Hardware
---

### Post by Jack the R on 2021-03-19
The HP shows up in System Settings>Printer. By default it is coming up with "reject print jobs" checked, and the printer is paused. After I fix that and try to print, the job shows up in the print queue as "pending," but after a few moments disappears without printing. The print queue and the system settings entry say "the printer is not responding."

I don't believe I have HPLIP installed, although I've tried, following these instructions - [Link](https://www.tipsonunix.com/2020/05/install-hplip-3-20-5-in-ubuntu-20-04-linuxmint/)

A lot of things failed to install, and I'm looking at repository issues, following the instructions here - [Link](https://help.ubuntu.com/community/Repositories/Ubuntu)

In the software manager, I didn't have the "Source code" box checked, so I checked that and hit the close dialogue, then hit "Reload" to update the list, which gave me this error message - 

> pk-client-error-quark: E: Malformed entry 1 in list file /etc/apt/sources.list.d/wine-obs.list (Suite)
E: The list of sources could not be read.
(281)

I did have to mess with WINE earlier to get a 32 bit program to run. My skill level is basically "find instructions on web site, paste into terminal and hope for the best," so if WINE is messed up fixing it is beyond me. However it is fixed, I need my 32 bit compatibility.


edit - Tracked the problem down, somehow a url in wine-obs.list got a line break in it, making it impossible to access a repository.  Taking the line break out worked - 

```
deb http://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04 ./
```

---

