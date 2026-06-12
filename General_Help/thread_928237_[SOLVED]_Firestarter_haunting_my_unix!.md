---
title: "[SOLVED] Firestarter haunting my unix!"
date: 2008-09-23
forum: General Help
---

### Post by 22Ti on 2008-09-23
I'll cut to the chase. On boot up(log in) my PC asks me for password to "..allow urs/bins/firestarter to modify my system..." Only problem is, I have uninstalled it, erased all files, taken away the post in my session preference and still it insists. This is very irritating, and weird?!

I have searched for weeks now for a solution and none work! Should I call an exorcist?!:lolflag:

Please help!

---

### Post by Sef on 2008-09-23
How did you remove firestarter?  There could have been configuration files left behind.

---

### Post by 22Ti on 2008-09-23
Thats exactly what I was thinking. When I had the front end installed, if I canceled the password request it would persist for a while but now it doesn't. 

Back to the uninstallation; I first used synaptic to completely remove all, then I saw it didn't work (tried installing and removing a couple of hundred times like this) and I used "apt-get install" command to install it again and the "purge" + "autoclean" to remove it, still nothing. 

In some post among the hundreds I have read, I learned and successfully deleted both the firestarter file from God knows where and a entry from some config file, still nothing...

---

### Post by 22Ti on 2008-09-25
Bump!

---

### Post by cariboo on 2008-09-25
I don't use a firewall, but have you tried:

```
sudo update-rc.d -f firestater remove
```

This will remove firestarter from /etc/rc.d*, which is where all the startup scripts are located.

Jim

---

### Post by 22Ti on 2008-09-25
edit: sudo update-rc.d -f firestarter remove : (left out r between a and t)

This time even I thought it would work!...Still nothing :confused:

---

### Post by 22Ti on 2008-09-28
Bump!

---

### Post by 22Ti on 2008-10-04
Bump! ....Somebody?

---

### Post by lswb on 2008-10-04
Hey is your avatar the penguin from "The Wrong Trousers"? 

Anyway, it sure seems like somehow a script was left behind. Do you know if the firestarter executable itself is still on the system? Try these commands in a terminal and see if they give any info that might help:

locate firestarter

grep -r "firestarter" /etc

Also, from reading your 1st post, are you getting the password prompt when you log in? Maybe there is something going on in your home directory. In 
Main Menu/System/Preferences/Sessions did you look for anything referring to firestarter in both the Startup and Current Session tabs?

---

### Post by 22Ti on 2008-10-09
> **lswb said:**
> Hey is your avatar the penguin from "The Wrong Trousers"? 


Yes it is.:) Penguins rock! 
> **lswb said:**
> 
Anyway, it sure seems like somehow a script was left behind. Do you know if the firestarter executable itself is still on the system? Try these commands in a terminal and see if they give any info that might help:

locate firestarter

grep -r "firestarter" /etc


locate firestarter;

/usr/share/app-install/desktop/firestarter.desktop
/usr/share/app-install/icons/firestarter.png
/var/cache/apt/archives/firestarter_1.0.3-6ubuntu3_i386.deb

grep -r "firestarter" /etc;

grep: /etc/alternatives/epiphany-browser.1.gz: No such file or directory
grep: /etc/alternatives/strong-name-tool: No such file or directory
grep: /etc/alternatives/resource-file-generator: No such file or directory
grep: /etc/alternatives/gnome-www-browser.1.gz: No such file or directory
grep: /etc/alternatives/gnome-www-browser: No such file or directory
grep: /etc/alternatives/cli-sn.1.gz: No such file or directory
grep: /etc/alternatives/assembly-linker: No such file or directory
grep: /etc/alternatives/cli-al.1.gz: No such file or directory
grep: /etc/alternatives/cli-resgen.1.gz: No such file or directory
grep: /etc/alternatives/djview: No such file or directory
grep: /etc/rc0.d/K20festival: No such file or directory
grep: /etc/rc5.d/S20festival: No such file or directory
grep: /etc/rc6.d/K20festival: No such file or directory
grep: /etc/rc2.d/S20festival: No such file or directory
grep: /etc/rc3.d/S20festival: No such file or directory
grep: /etc/rc4.d/S20festival: No such file or directory
/etc/sudoers.tmp~:#Allowing firestarter = no password
/etc/sudoers.tmp~:%USERNAME ALL= NOPASSWD: /usr/sbin/firestarter
grep: /etc/rc1.d/K20festival: No such file or directory

> **lswb said:**
> Also, from reading your 1st post, are you getting the password prompt when you log in? Maybe there is something going on in your home directory. In
Main Menu/System/Preferences/Sessions did you look for anything referring to firestarter in both the Startup and Current Session tabs?


Getting the prompt directly after I log in. Nothing in either the "Startup" or "Current Session tabs".

---

### Post by lswb on 2008-10-09
> **22Ti said:**
> Yes it is.:) Penguins rock! 

Wallace and Grommet rock too.

I don't really see anything that might cause the password prompt. Try this in your home directory:

grep -r firestarter *


and see if there are any scripts referring to firestarter. Do you have any launchers or shortcuts on the desktop or on a panel referring to firestarter?

Also, it might work to reinstall firestarter, then disable it in Main Menu/System/Administration/Services. Check in System/Preferences/Sessions also. After it has been disabled, try uninstalling again. 

Looking at the firestarter web page, I see it has a configuration wizard that runs the 1st time. Maybe it has some other executables with names different than "firestarter" that are causing your problem, though a clean uninstall should remove all of them. You might check that site for more information 

[http://www.fs-security.com/](http://www.fs-security.com/)

Good Luck.

---

### Post by 22Ti on 2008-10-12
Fixed it!:)
Don't really get why the problem remained after the purge but when I again looked closer at the session/current/session and currently running programs I found gtsk /usr/sbin/firestarter which doesn't exist. Anyway, I closed it and saved the current session and it seamed to to the trick!:lolflag:

I would like to thank you all for your willingness to help!:popcorn:
This is what makes linux the superior operating system.

---

