---
title: "Busybox"
date: 2008-07-22
forum: General Help
---

### Post by iampriteshdesai on 2008-07-22
After the ubuntu loading screen it brought us to a "BusyBox v1.1.3(Debian 1:1.1.3-3ubuntu3) Built-inshell(ash)
enter 'help' for a list of built in commands." i tried "live break=top, then modprobe piix, exit" that didn't work anyone know WHY this is happening and HOW to fix it?
After restarting though the problem dissappears. It comes every once in a while.

---

### Post by Taxman415a on 2008-07-22
What version of Ubuntu are you running and what type of hardware? It's hard to tell without knowing more about what errors you are getting that are causing it. Most likely you get some error or another when it drops to busybox. Basically what busybox is is a backup shell when something else fails. When it happens look for errors. Or else go through the files in /var/log, use ```
less /var/log/syslog
``` for example to see if you can find any examples of the times that it booted unusually and what happened just before it did so. See [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles) for more background on the log files.

As to the commands you tried, those are very specific to problems other people had. I couldn't find documentation on the < > break=< > command but where you put live you didn't want live unless you were trying to boot a livecd. As for modprobe piix that tries to load a specific kernel module (that I don't even have on my Hardy system, I have thinks like ata_piix.ko and pata_mpiix.ko instead.) You would only need that if that were the specific module that were failing to load. Looks like you did some googling though, so good work on that.

I did find some links that specified other options to the break command and that the options are in the script /usr/share/initramfs-tools/init  the links are [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/126146](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/126146) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/181561](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/181561) but they don't really do much good unless you know what you're doing.

---

