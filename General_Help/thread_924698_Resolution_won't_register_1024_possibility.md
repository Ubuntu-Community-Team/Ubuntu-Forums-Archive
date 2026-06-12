---
title: "Resolution won't register 1024 possibility"
date: 2008-09-19
forum: General Help
---

### Post by godd4242 on 2008-09-19
Hi. I have a problem that you answered in a previous thread, although it has a bit of a complication. This is in regards to screen resolution, and not being able to change it. I just reinstalled latest drivers for my nvidia card from before I managed to damage this too, so that isn't the issue. What happened was, I booted into a different kernel then the default. When the screen loaded, the resolution was down, after checking the menu I saw that it was at 640x480. "Well," I say to myself "that was pointless" and go back to my standard, latest kernel. Now that, when the desktop loads, is also at 640. When I went into screen resolution to change it, none of the drop down menus had any options in them. I checked my drivers and there hadn't been any change, so I reinstalled latest, and no change, so I went and found the older drivers and did those too. No luck. I've gone down the list of all the kerenls I have, including recovery modes, which I think is what I booted into to start this problem, and I haven't been able to get my computer out of 640 screen res. I tried what you said, but 0 for me is just 640x480 still.

What I think it is, that when I went into recovery mode, it knocked my res down to 640. When I rebooted into standard, it didn't register a change? I guess? Also, I've tried a few fixes on the forums, but the xrandr - # fix only sets my thing back to a maximum of 640. So I guess if I could make Ubuntu recognize that my monitor can do up to 1400, I'd be ok. Is there a way to just tell xorg to shut up and display at 1400? Maybe that would work?

---

### Post by godd4242 on 2008-09-19
After a little more searching, I've run into what I thought might work, an xorg edit to just tell my computer to run in 1024. Problem is, this comes up:

dking@dking-laptop:~$ dexconf
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
dexconf: error: unable to write to "/etc/X11/xorg.conf"
dking@dking-laptop:~$ sudo dexconf
sudo: unable to resolve host dking-laptop
[sudo] password for dking: 
dking@dking-laptop:~$ dexconf
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
dexconf: error: unable to write to "/etc/X11/xorg.conf"
dking@dking-laptop:~$ sudo
sudo: unable to resolve host dking-laptop
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
dking@dking-laptop:~$ 

Now I've tried sudo in other uses, and still no go.

---

### Post by Dayne89 on 2008-09-19
disable any proprietary drivers and go to System > preferences > main menu, turn on 'screens and graphics' in others and open it from main menu. set your scene to LCD panel 1280x1024. log out then back in and enable drivers.

---

