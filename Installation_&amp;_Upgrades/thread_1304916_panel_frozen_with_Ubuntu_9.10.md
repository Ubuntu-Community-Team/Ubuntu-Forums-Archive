---
title: "panel frozen with Ubuntu 9.10"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by muldengold on 2009-10-29
Hi,

I've just upgraded to Ubuntu 9.10. After booting, the top panel (Applications, Places,.... etc.) is frozen. However, now and then, after re-booting it works perfectly. Any ideas? Thanks a lot! 

Regards,
Sandro

---

### Post by zalberico on 2009-10-29
Is it just the panel or the whole desktop?  
If it's just the panel and you don't want to reboot this might work in the short term.

If you can open a terminal:
$ ps ax | grep gnome-panel
$ kill -9 (id for gnome panel that shows up)
$ gnome-panel&

If you can't open a terminal you could ctrl alt f1, log in there and do the same thing.

Also try typing 
$top
in a terminal to see if anything is absorbing an unusual amount of resources.

Good luck.

---

### Post by muldengold on 2009-10-29
Thanks - yes it's just the panel. I can access the terminal. This came back:

sandro@sandro-laptop:~$ ps ax | grep gnome-panel
 2109 ?        S      0:00 gnome-panel
 2536 pts/0    R+     0:00 grep gnome-panel
sandro@sandro-laptop:~$ kill -9
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
sandro@sandro-laptop:~$ gnome-panel&
[1] 2538
sandro@sandro-laptop:~$ Cannot register the panel shell: there is already one running.


The top command didn't come up with anything suspicious. All programmes I have started work flawlessly.

Regards,
Sandro

---

### Post by zalberico on 2009-10-29
Alright, you didn't use kill correctly (no worries :-) )

See that 2109, it's the processor identification number (PID) for the gnome panel.

$sudo kill -9 2109 

Would have worked.

Next time the PID will be different so don't just use 2109.

---

### Post by muldengold on 2009-10-29
Thanks for your help. However it didn't work:

sandro@sandro-laptop:~$ ps ax | grep gnome-panel
 2446 ?        S      0:01 gnome-panel
 2484 pts/0    S+     0:00 grep gnome-panel
sandro@sandro-laptop:~$ sudo kill -9 2446
[sudo] password for sandro: 
sandro@sandro-laptop:~$ gnome-panel&
[1] 2514
sandro@sandro-laptop:~$ Cannot register the panel shell: there is already one running.

Any other thoughts???? Thanks

Sandro

---

### Post by tylerni7 on 2009-10-30
I'm having the same problem. I'm not sure what is causing this, but I can't kill it (kill -9 as root doesn't do it either).

I have had a couple similar problems since upgrading to 9.10 where I'll get zombie processes that I can't even kill as root. Anyone have any ideas? I'd really like to have gnome-panel :(

---

### Post by tylerni7 on 2009-10-31
Okay, I think it's fixed.. I followed the instructions for killing gnome-panel if it freezes (basically remove all the .gnome files/directories in your home directory (THIS WILL REMOVE ALL OF YOUR GNOME CONFIGURATIONS) and then reboot)
Good luck!

---

### Post by filu on 2009-11-01
Hello.

Got the same problem. Killing gnomepane solves the problem temporarily, but after a reboot the same thing happens again. How to fix it permanently?

Filip.

---

