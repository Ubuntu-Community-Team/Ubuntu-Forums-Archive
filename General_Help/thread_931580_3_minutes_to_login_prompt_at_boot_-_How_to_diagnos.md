---
title: "3 minutes to login prompt at boot - How to diagnose?"
date: 2008-09-27
forum: General Help
---

### Post by uzd4ce on 2008-09-27
I've had this problem for several months now, but I don't reboot very often so it hasn't really bothered me.  My problem is that the boot process pauses for several minutes and I don't know how to tell what's going on.

It happens just after the screen switches from terminal-looking commands to the GUI (brown background).  I get a spinny cursor (which I can move around with the mouse) as if the system is thinking about something, and then it just sits like that for a good several minutes before finally showing me the username and password fields.  

Once I enter my login info, the rest of the boot process then proceeds normally.

I set that GRUB option to show me the terminal commands that are going on during boot, but that hasn't helped me since the problem occurs just after it switches to the GUI.

Can any one tell me in general what the system is trying to do just as the GUI kicks in, or how I can try to find out?

Thanks

---

### Post by dcstar on 2008-09-28
> **uzd4ce said:**
> I've had this problem for several months now, but I don't reboot very often so it hasn't really bothered me.  My problem is that the boot process pauses for several minutes and I don't know how to tell what's going on.

It happens just after the screen switches from terminal-looking commands to the GUI (brown background).  I get a spinny cursor (which I can move around with the mouse) as if the system is thinking about something, and then it just sits like that for a good several minutes before finally showing me the username and password fields.  

Once I enter my login info, the rest of the boot process then proceeds normally.

I set that GRUB option to show me the terminal commands that are going on during boot, but that hasn't helped me since the problem occurs just after it switches to the GUI.

Can any one tell me in general what the system is trying to do just as the GUI kicks in, or how I can try to find out?

Thanks

The boot process runs through all the scripts in /etc/rc2.d (in alphanumeric order), so you may be able to see what is stalling when S30gdm is kicked off.

Stalling can be due to network misconfiguration or hostname problems (among may things).

A forum search should provide many options.

---

### Post by uzd4ce on 2008-09-28
After some advice in another forum, I tried running sudo update-rc.d -f gdm remove to turn off the gdm. When I did that, it boots up to the shell login prompts as fast as I would expect it to. In fact I can login and then startx and get to a desktop much faster than I can if I boot normally with my problem.

So, does that mean that my issue is related to the gdm or the graphical elements of the bootup?

What other steps are ignored when you turn off gdm?

Thanks

ps In general, here's what I'm seeing when I boot
Dell screen
GRUB menu
Tons of terminal stuff flying by
The last terminal stuff I see references Bluetooth, then NetworkManager,
Screen flashes a bit then
Brown screen with active, spinning cursor. it sits there 2-3 minutes then
Username and password fields

---

### Post by starcannon on 2008-09-28
You could take a look at /var/log/syslog
```
gedit /var/log/syslog
```You could also run dmesg
```
dmesg > dmesgLog.txt && gedit dmesgLog.txt

```You should be able to see whats hanging up in one of those 2 outputs.

GL

---

### Post by uzd4ce on 2008-09-28
After all of that, I just changed my GDM theme, and everything seems to work normally now.  No more long pause before the login screen comes up.

Thanks for all the advice.

---

### Post by starcannon on 2008-09-28
> **uzd4ce said:**
> After all of that, I just changed my GDM theme, and everything seems to work normally now.  No more long pause before the login screen comes up.

Thanks for all the advice.

lol, gotta love that. GJ on solving!

---

### Post by physeetcosmo on 2009-01-19
> **uzd4ce said:**
> ...I can login and then startx and get to a desktop...

I am having X Server problems since I had to force power-off my system after it hung in Synaptic. Didn't know the command to start X Server, thanks!

---

