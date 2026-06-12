---
title: "apt database gone awry"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by undo on 2006-02-17
Hi all

When I was routinely running the adept updater yesterday, something went wrong. And now, when I run any frontend to apt, the same thing keeps happening over and over again.

The updater downloaded some 10 or 20 packages and then started replacing outdated packages by new ones. Although I am not very familiar with apt, it looks to me like it was going over some list of dependencies when it suddenly stalled. The last line of output from apt was:

[b][...]
Setting up linux-image-2.6.12-10-386 (2.6.12-10.28) ...[/b]

It just totally got stuck at that point. I waited half an hour and then tried to see what was going on. But unfortunately, the system had become unresponsive. Or, to be more precise, all processes that had been running continued doing so, but I could absolutely not start anything new. I couldn't open a new console, I could not ssh into the machine, nothing. I could still ping it though because apparently whatever is reponsible for replying to pings was already running.

I had no choice and did a hard reboot. The box came up again, but ever since, all apt frontends have been exhibiting strange bugs. On the console, aptitude runs fine, lets me select packages to upgrade or install, but then gets stuck with the same message as above. Under KDE, adept and the adept updater don't work at all. After entering my password into kdesu's dialog, I get a few seconds of nothing and then both programs complain about not running as root - but they *are* running as root, through kdesu. I tried launching them from a root console to make 100% sure they were running as root and got the same errors.

So, it seems to me that something in my apt database (or the linux-image package?) is corrupted and apt-get as well as the frontends choke on it. Is there something I can do to fix this? Or at least debug it? If nothing else helps, I will just wipe the box and reinstall. But I would rather like to avoid having to set it up from scratch.

- Bartosz

PS: All of this is on Kubuntu Breezy

PPS: Because I am doing OpenGL shader development, I have installed NVidia's latest graphics card drivers. They are not available in any repository I know of, so I used NVidia's installation program. This means that there is one additional kernel module running that didn't get there through apt. Could apt be choking on this?

---

### Post by stalefries on 2006-02-17
It may be that. 

Whatever it is, seeing your /etc/apt/sources.list file may be helpful. 
Can you post the output of "cat /etc/apt/sources.list" here?

---

### Post by undo on 2006-02-18
[QUOTE=stalefries]Can you post the output of "cat /etc/apt/sources.list" here?[/QUOTE]

Sure thing. I have been running with this sources.list for a while and it never gave me any troubles.

```
## Main distribution

deb http://de.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://de.archive.ubuntu.com/ubuntu breezy main restricted

deb http://de.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

## Universe

deb http://de.archive.ubuntu.com/ubuntu breezy universe
deb-src http://de.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## Multiverse

deb http://de.archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://de.archive.ubuntu.com/ubuntu breezy multiverse

deb http://security.ubuntu.com/ubuntu breezy-security multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security multiverse

# KDE 3.5.1 for Breezy
deb http://kubuntu.org/packages/kde351 breezy main

## Backports
# deb http://de.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

---

