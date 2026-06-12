---
title: "Dbus and HAL not starting, CD's not detected. Oh, and KDM dies too. :("
date: 2008-02-07
forum: Hardware &amp; Laptops
---

### Post by H4rm0ny on 2008-02-07
This may sound like lots of problems in one thread, but I suspect they may all be closely related.

I have a fresh Kubuntu Gutsy install on recently purchased hardware (so I can't confirm that it worked previously). For the most part, everything is fine. Better than fine, in fact. It's great. :)

But I've never been able to start the system properly. On startup, the system always freezes completely just as it's about to display the login page. I can only boot my machine by starting it in recovery mode so that I can come straight to a command prompt. HOWEVER, it then works if I start kdm manually - taking me to a normal login screen!

On logging in, dbus and HAL are never running. However, both run without complaint when I start them with "/etc/init.d/xxx start."

Finally, dvds and cds don't automount and are never mountable via Dolphin or any other file manager I've tried (this is after starting HAL and Dbus). However, I can manually mount discs from the command line and can also play them using a media player that accesses /dev/scd0 directly.

I don't know what logs or tests would be useful in sorting this out, but let me know and I'll post. As it came up in my searches on dbus and hal, I'll just say now that my /etc/init.d/rc file has CONCURRENT set to NONE.

Any help much appreciated.

-Harmony.

---

### Post by H4rm0ny on 2008-02-17
I don't like to bump, but I'm still unable to get dbus or hal to start automatically. Nor, I've discovered, does CUPS. All start without any problem at all when I explicitly start them from the command line from /etc/init.d/xxx start.

This is a pretty fresh install, but something is fundamentally wrong with my system and I've been unable to find an answer to this.

Any help would be greatly appreciated.

-H.

---

### Post by Yellow Pasque on 2008-02-17
Yeah, HAL depends on dbus and Ubuntu funks up when you set concurrency to shell and tries to load hal before dbus. You said you've set concurrency to none, but maybe hal is still trying to load before dbus?

Let's try this to eliminate that as the possible cause of the issue:
```
cd /etc/rc2.d
sudo mv S12hal S13hal
cd /etc/rc5.d
sudo mv S12hal S13hal
```

Also, see if there's anything in your dmesg log about hal
```
dmesg | grep hal
```

---

### Post by H4rm0ny on 2008-02-17
First off, thank you for replying and love the avatar. We've been calling it Hairy Hard-on in our office. :D

This hasn't resolved the issue but it's provided me with another clue. I had previously renamed the S12hal file in the rc2/ directory which I should have mentioned, but not in rc5. That's what comes of following How To's without actually knowing what you're doing. I've done some reading and I understand the issue with run levels now. 

However, I am currently in run level "S." :-/

```

h4rm0ny@mantis1:~$ who -r
         run-level S  Feb 17 17:37                   last=
h4rm0ny@mantis1:~$

```

Because kdm freezes on start-up, I always start in recovery mode and then start kdm from the command line which works. I have tried this again since making your suggested changes in case kdm was freezing due to lack of dbus or hal but it's still unable to start except from the command line in recovery mode.

I'm unsure where to go from here. I could presumably copy the S13hal and S12dbus scripts into the rcS/ directory which currently doesn't have any dbus or hal scripts. This would presumably then start them automatically even in recovery mode, but I (a) don't know if it's a good idea for recovery mode to be starting these in case they interefere with anything when I actually need recovery mode and (b) if I can fix the kdm freeze, I'll be able to start up in the normal run-level any way.

Thanks a lot for the suggestions, but I'm afraid I'm stuck again. dmesg had nothing about hal or dbus in it.

-Harmony.

---

### Post by deepclutch on 2008-02-18
reinstall upstart &Co,starup-services etc.

---

### Post by H4rm0ny on 2008-02-20
> **deepclutch said:**
> reinstall upstart &Co,starup-services etc.

No effect. KDM still crashes on startup except when run from the command line in recovery mode.

-H.

---

### Post by deepclutch on 2008-02-23
I am a wanna-be Kde user ;) not yet tried to stick with it!so not much idea about kwin window manager :p
but,u may like to try update-rc.d cmd to arrange the dbus and hal launch to some values may be dbus @12 and hal@20 ?


regarding your mounting problems,I suspect ur /bin/mount may not have suid bit not set.
u can check for this by :
```
ls -l  /bin/mount
```
the o/p should show similar to below:
-rw**[COLOR=Red]s[/COLOR]**r-xr-x 1 root root 64112 2008-01-19 21:21 /bin/mount
^see the "s" suid bit thingy.if it is not showing suid,try adding suid bit or do a  "sudo apt-get install --reinstall mount "

---

### Post by H4rm0ny on 2008-03-06
Thanks for the reply. I'm afraid that the suid bit was already set, at least when booting in recovery mode. I can't see if it's set when booting in normal mode as the system simply crashes when it reaches the point of starting KDM.

Any help with this would be really appreciated. I have had this installation for some time now and it has never worked.

-H.

---

### Post by H4rm0ny on 2008-03-22
I hate to bump and I wont keep doing this... but I've now had my system for over three months and I still can't get it to boot on its own. If I start in recovery mode and run "kdm start" from the command line as root, it works and I can login. If I just let it start on its own it crashes as soon as it tries to start kdm. All the other problems with services not starting stem from this.

Can anybody help?

-H.

---

