---
title: "How to save boot messages?"
date: 2005-02-08
forum: Hardware &amp; Laptops
---

### Post by drasko on 2005-02-08
Hi. I can't see any boot.log at the /var/log directory. I was wondering how to save all those messages written on the screen at the boottime, for viewing them later, but I want them saved at the exact form, not scattered allover in the different logs, like in messages or in syslog, etc...

Why there is not boot.log in Ubuntu, and gow to configure /etc/syslog.conf to get one?

Thanks,
Drasko

---

### Post by m4ng0 on 2005-02-08
Make sure you start bootlog daemon (it is in /etc/init.d/bootlogd).

---

### Post by drasko on 2005-02-10
Do I have to edit the /etc/init.d file, or can i write some command like update-rc.d bootlogd default?

i'll try and see what happens. 

also, do I have to make file boot.log, or it wil be automaticly created.
Drasko

---

### Post by drasko on 2005-02-10
Ok,

root@ic-07:/home/drasko # update-rc.d  bootlogd defaults
 System startup links for /etc/init.d/bootlogd already exist.

I cheked it, bootlogd script is already in /etc/init.d folder. How to start this deamon? Should it be start by editing /etc/inittab somehow?

Where it will make this log - where to search boot.log (or how is it called?) after the boot?

Drasko

---

### Post by Mute on 2005-02-10
This might sound stupid and maybe I am way off but have you tried dmesg?  Just curious.

-Mute

---

### Post by m4ng0 on 2005-02-10
[QUOTE=drasko]I cheked it, bootlogd script is already in /etc/init.d folder. How to start this deamon? Should it be start by editing /etc/inittab somehow?
[/QUOTE]

Edit:
/etc/default/bootlogd
and check if this works.

---

### Post by drasko on 2005-02-12
Trouble continues...
I enebled bootlogd in /etc/defaults, and rebooted machine. At the end of booting I noticed the massage bootlogd daemon stopped. It looked like evrything is ok, but there was no boot file in my /var/log. then I rebooted agai and noticed that at the beginning of bootin, when bootlogd is starting it is giving some kind of io ctl error message, and writig something about it can't open /dev/ttyzf. I guess this is some kin of pseudo console it has to listen during the boottime...

bootlogd: ioctl (/dev/ttyzf, TIOCCONS): Bad file descriptor 

There is no /dev/ttyzf on my system, I theink this console is relatet to hotplug or something. Also I found out that the problems might be related to udev, but my udev is latest version. The only chanche I have is degrading the version of udev... but that is a soot in the dark...

Any ideas?
Drasko

---

