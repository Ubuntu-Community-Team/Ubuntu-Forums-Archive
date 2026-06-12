---
title: "[SOLVED] Auto login, auto start-up script"
date: 2008-11-07
forum: General Help
---

### Post by DefineByte on 2008-11-07
Before I go searching how to do this I thought I better make sure it can actually be achieved.

I need a script that will do the following (I think xD):
[LIST=1]
[*]Automatically login as a standard user
[*]If no keyboard other than "/dev/input/by-id/usb-HOLTEK_YaoCoo-event-kbd" (my remote) is present, run ncmpc
[*]When exiting ncmpc check again for the presence of a keyboard other than my remote and if not present, shutdown (I've already set it up to allow shutting down as non-root)
[/LIST]

I'm running with just the terminal. I want to be able to hit the power button and have the music player usable without further input. Should I need to do anything else on the box I'd like to be able to simply plug in a keyboard and go.

Is this doable?

---

### Post by DefineByte on 2008-11-07
Thanks to [this](http://www.lalitkapoor.com/blog/2008/06/30/ubuntu-server-desktop-autologin/) blog post I've got the auto login, now for the rest (in .profile? .bash_profile? .bashrc? who knows :D).

Edit: Answer my own question... :redface:
I've managed to cobble something together. There may well be a better way to do it but hey, it works.\\:D/
In ~/.bash_profile I put:
```
#!/bin/sh
if ! (ls /dev/input/by-id|grep "kbd$"|grep -v "HOLTEK");
then
        irpty ~/ncmpc.lirc -- ncmpc
        if ! (ls /dev/input/by-id|grep "kbd$"|grep -v "HOLTEK");
        then
                halt
        fi
fi
```
Thanks everyone! ):P

---

