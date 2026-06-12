---
title: "Restarts-shutdowns"
date: 2008-09-26
forum: General Help
---

### Post by elbow rub on 2008-09-26
Recently,

whether I'm restarting or shutting down, the PC will freeze while showing the progress bar, which progressed all the way. This is not everytime, rather it seems random, which forces me to power it down. I haven't experienced anything out of the ordinary, except that. Does anyone know anything about this and can give me some things to try?

Thanks
Elbow Rub

---

### Post by mikewhatever on 2008-09-26
Next time it does that, hit ctrl+alt+backspace and look for errors. If there are any, copy them (or whatever is says last) and post here.

Update: The way proposed above, apparently, doesn't work, because nothing happens when you hit the key combination. ctrl+alt+backspace restarts xserver, which under, normal circumstances, brings one back to the gdm login screen. The question now is, how can you get to the errors that might show when the computer freezes. One way is to look through or search for the logs, but then you have to know what to search for.

---

### Post by elbow rub on 2008-09-26
Thank you, I will do that. I assume I can do a print screen? Or how would I copy it?

TY

ER

---

### Post by mikewhatever on 2008-09-27
> **elbow rub said:**
> Thank you, I will do that. I assume I can do a print screen? Or how would I copy it?

No, you can't. There is no GUI in where you are going.

Edit: Please see post #2 undate.

---

### Post by elbow rub on 2008-10-23
***mikewhatever***,

sorry I haven't replied to this until now, I hadn't experienced what I originally stated until now.

Tonight, I installed guild wars through wine and enabled my video card, I was prompted to reboot, which it did not, it stuck at the point where it was suppose to restart. At which point I CTRL+ALT+BACKSPACE and nothing happened, except everything locked, which forced me to power off. Once I booted again, the enable didn't take effect and it prompted me again to restart. Same thing happened.

Thank you
ER

---

### Post by cyfur01 on 2008-10-23
Try sifting through /var/log/syslog* and see if it mentions any errors/etc when shutting down.

---

### Post by cyfur01 on 2008-10-23
> **cyfur01 said:**
> Try sifting through /var/log/syslog* and see if it mentions any errors/etc when shutting down.

Or better yet, you can browse all the usual logs in System->Administration->System Log

---

### Post by elbow rub on 2008-10-24
***CYFUR01***,

I checked the system log and seen nothing error related. After checking, out of curiosity I restarted and the same happened and it still wouldn't allow me to cltr+alt+backspace. Any other suggestions I could try?

Thanks

---

### Post by cicatrix1 on 2008-10-24
control + alt + f1 (through control + alt + f6) will drop you into a VT where you can log in.

I would check /var/log/Xorg.0.log, /var/log/messages/, ~/.xsession-errors

---

### Post by cyfur01 on 2008-10-26
> control + alt + f1 (through control + alt + f6) will drop you into a VT where you can log in.
If the computer is freezing part way through shutting down, there's no way to drop to a virtual terminal since it will have stopped most services, including the ones for the virtual terminals. You'll have to stick to *a posteriori* (after the fact) error analysis.

> I would check /var/log/Xorg.0.log, /var/log/messages/, ~/.xsession-errors
I would also check /var/log/kern.log as this is generally quite a verbose error log. The best way to check this would be to repeat the error, take note of the time, and then hold the power button until your computer is off. Wait a few minutes, turn it back on and then sift through these logs, checking for events that happened near the time that your computer tanked (The pause will help you to distinguish the error from all the messages that come up when starting your computer). If you're really stumped, post your kern.log and syslog files and the time the error occurred and I can try to look and see if anything is amiss... no guarantees I'll find anything you won't though.

(If you're paranoid about posting the logs in a public forum, you can send them to me in a private message and I'll try to do what I can if you wish.)

---

### Post by elbow rub on 2008-10-31
***cyfur01***,

unfortunately I didn't read your last post before I had to power off due to it locking up. So far, it has happened every time I chose to update then reboot when prompted, although it has happened randomly as well. Checking those log in those directories I can only do via GUI (sad huh?), does that make a difference?

Sorry for the noobism

thanks for your patience

elbow rub :)

---

