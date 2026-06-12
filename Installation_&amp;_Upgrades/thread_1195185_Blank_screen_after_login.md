---
title: "Blank screen after login"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by pallbearerx on 2009-06-23
I performed a new installation of Ubuntu 6.0.6 on a Toshiba Tecra 550CDT laptop (I know, it's a dinosaur).  Afterwards, when I log in I am presented with just a blank screen -- the Gnome desktop doesn't load.

I checked the .xsession-errors file and found the following, which told me nothing.

> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "username"
/etc/gdm/Xsession: Beginning session setup...

I then checked the /var/log/gdm/:0.log files, which showed the following error.

> (EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : No such file or directory


So I opened the /etc/X11/xorg.conf file and proceeded to remove all references to the wacom device (e.g. InputDevice and ServerLayout entries).  Rebooted, but same symptom.

I check the :0.log file again and the wacom device errors were gone.  Now there was this error.

> error opening security policy file /etc/X11/xserver/SecurityPolicy

Sure enough the xserver folder was not present in the /etc/X11 directory.  So I created one (mkdir /etc/X11/xserver) and then copied the SecurityPolicy file from the /usr/share/doc/examples folder.  Rebooted, but same symptom.

Now the :0.log file shows no errors.  I'm stumped.  Any suggestions on what I can check next to determine why the gnome desktop session won't start?

TIA,
PallbearerX

---

### Post by overdrank on 2009-06-23
Hi and welcome, it has been awhile since Dapper but what is the amount of memory for the system?
Are you able to reach the command line with the ctrl, alt, F1 keys?
You may try and reconfigure your xorg
```
sudo dpkg-reconfigure xserver-xorg
```
But it may just be not enough memory.

---

### Post by pallbearerx on 2009-06-23
Could this be an issue trying to load Compiz?  If so, how can I find out without any addt'l messages in the :0.log file?

I know I can run the following to remove Compiz, but I don't want to do that if it's not the problem.

sudo apt-get remove compiz-core
Regards,
PallbearerX

---

### Post by overdrank on 2009-06-23
> **pallbearerx said:**
> Could this be an issue trying to load Compiz?  If so, how can I find out without any addt'l messages in the :0.log file?

I know I can run the following to remove Compiz, but I don't want to do that if it's not the problem.

sudo apt-get remove compiz-core
Regards,
PallbearerX

If memory serves me correct, dapper did not support compiz. If you did not install compiz then it is not a issue as it was not included with 6.06

---

### Post by pallbearerx on 2009-06-23
@overdrank

Thanks for the reply.  I did try to reconfigure xorg first (guess I should have included that in my original post).  And that did fix an initial issue where the desktop was in 800x600, and afterwards put it correctly in 1024x768.

Regarding the memory, the machine only has 92Mb.  It's crappy, I know -- but I'm trying to salvage this machine for some usable purpose rather than just scrapping it.

Top output shows the following.

> Mem: 94100k total, 90884 used, 3216k free, 25700k buffers
Swap: 266232k total, 18756k used, 247476k free, 16340k cached


I had previously run WinXP on this box (VERY SLOW - but it worked), so I figured Linux would perform slightly better than MicroCrack's product.

Regards,
PallbearerX

---

### Post by overdrank on 2009-06-23
With that low of memory I would maybe suggest Puppy or DSL. Some also say that CrunchBang is good. Good luck.

---

### Post by pallbearerx on 2009-06-23
I will give them a shot!  Many thanks!

---

### Post by pallbearerx on 2009-06-23
For the record - CrunchBang Linux is the winner.

Thanks again, OverDrank.

---

### Post by petebarchetta on 2009-09-11
what version of crunchbang did you use in the end, i couldnt get it to play nicely on my 550 and i had a full compliment of ram (160mb)
for your xorg
try this (my config)
[http://ubuntuforums.org/showthread.php?t=1085579&highlight=550cdt+xorg]("http://ubuntuforums.org/showthread.php?t=1085579&highlight=550cdt+xorg")
works well :)
i also have a 520, but thats a DSL only beast, dapper is too painful and alternate only install is the way to get it running

---

