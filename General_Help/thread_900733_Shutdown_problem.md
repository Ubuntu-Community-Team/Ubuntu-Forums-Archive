---
title: "Shutdown problem"
date: 2008-08-25
forum: General Help
---

### Post by reffu on 2008-08-25
OK before anyone says anything i know there are a lot of posts about this. However none of them cover the problem i have exactly or don't give a good fix. I have hardy and when I click shutdown or restart everything disappears but my wallpaper. If i leave it nothing happens. When i hit the shutdown button on my computer the terminal pops up with info about different things such as dhutting down (whatever) [OK]
After about 10-20 seconds  i see something like nmsbusnotifier shutdown etc.. I can never get a good look at these (there are 4-5 lines) because they disappear after like 4 seconds. they look as if they error messages and none of them have [OK] after them. after this everything dissapears to be replaced by the shutdown bar which is about 95% done. then it shuts down and there seem to be no problems on reboot. can anyone tell me why this happens and  a possible workaround.
 I have samba enabled and an nvidia graphics cardd if that helps.

I'm not a newbie at ubuntu but 'm not an advanced user so please don't give me complicated terminal codes to enter.

Thanks,

reffu

---

### Post by prince_niceguy on 2008-08-25
I think the problem are with the samba mounts. Try unmounting them and doing a shutdown. The system would suspend/shutdown perfectly this way.

---

### Post by mssever on 2008-08-25
Can you logout normally?

--------------

Regarding prince_niceguy's suggestion: I have NFS shares mounted which prevent shutdown normally. The problem is caused by the network being disabled before the shares are unmounted. There's been a bug report open on this for several years. I think it might finally be fixed in Intrepid. In the meantime, my workaround is to add a script to unmount my NFS shares early in the shutdown process, before the network is deconfigured.

---

### Post by reffu on 2008-08-25
After unsharing any of my shared folders irie gain and the same problem happened. I then uninsstalled the samba mount/ unmount package. Now it still hags at shutdown but when i press the power buttn it says nmdbus no reply received (or something similar to that) Do i have to edit the shutdown file (not sure what its called) to tell it not to look for samba? 

Thanks,

Reffu

---

### Post by mssever on 2008-08-25
> **reffu said:**
> I haven't tried dismounting samba a no i cant logout.
Still, try unmounting the samba shares. But the fact that you can't logout suggests that one of your programs is hanging. Try this:

[LIST=1]
[*]Log out and wait for the blank wallpaper.
[*]Hit <Ctrl><Alt>F1 to drop to a console and log in.
[*]Check for processes owned by you that are still running. ```
htop -u youruser
``` is a great tool for this.
[*]Start killing off running processes and see if it makes a difference.
[*]Post the results of your research.
[/LIST]

---

### Post by reffu on 2008-08-25
OK i killed several processes which didnt help. I then looked at running processes the only 2 were htop and /usr/bin/keytouchd-launch x-session-manager killing the second one made everything suddenly end and it shut down normally with the bar starting from full with no error messages. I am not sure if this is because i ended the x-session-manager or if it was because there was an error with x-session manager

---

### Post by mssever on 2008-08-25
Is "/usr/bin/keytouchd-launch x-session-manager" one process or two? At any rate, you might have identified the offending program. Try killing that process before shutting down (from a terminal window), and see if everything works fine.

(By the way, I forgot to ask which signal you used to kill the process. SIGTERM is the default, and you should try it first. Only send SIGKILL when all other methods have failed, since SIGKILL brings the program down in the hardest way possible.)

---

### Post by reffu on 2008-08-25
Never mind its fixed. Apparently one of my programs, Keytouch, integrated itself with the x-session manager and was causing problems. It shuts down and reboots fine but i have to find a good alternative or learn to live without some of my keyboards shortcuts.

Thanks for all the help

reffu

---

