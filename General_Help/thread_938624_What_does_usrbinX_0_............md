---
title: "What does /usr/bin/X :0 ........... ?"
date: 2008-10-05
forum: General Help
---

### Post by cherva on 2008-10-05
What does "/usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/ :0.Xauth -nolisten tcp vt7" ? It comes from time to time with 100% cpu usage and goes after some time.

---

### Post by p_quarles on 2008-10-05
That is the X server -- in basic terms, it's the program that controls the graphical interface. 

It's not uncommon for some setups to get CPU usage spikes with the X server. How often does this occur? What kinds of things is the computer doing when this happens? What kind of graphics card are you using?

---

### Post by cherva on 2008-10-05
- NVIDIA GeFORCE 6200 
- It comes from time to time ( when gamging,or tring compiz fusion .... )

---

### Post by dpologea on 2009-04-06
Also, I have noticed that this process (/usr/bin/X) is consuming 100% CPU time, sometimes when Firefox is running. Each time Firefox displays certain pages, this happens in 100% of the cases, so the problem is very reproducible to me.
Recently I have discovered that the problem was related to Flash player 10 (beta). I'm back to version 9, now and the problem is gone. So, the problems when X consumes 100% CPU time could be very various.

---

### Post by PCZahra on 2010-01-31
I'm getting this now, too. it seems to be triggered by certain web pages displayed in firefox, and sometimes coincides with the clock being 4 hours ahead (or displaying GMT - I'm not sure which). Also, the scroll lock light is turning on and off. Kind of annoying while I'm typing.

---

### Post by PCZahra on 2010-01-31
It's getting worse. Firefox no longer thinks it's the default browser, and is having trouble retrieving its own settings, and the terminal is unable to load up. I reboot, but then one by one the problems come back.

---

### Post by www.perro.si on 2010-03-31
First set the *visual effects* to "none" in System | Preferences | Appearance. That helps in 99% of cases. Cheers.

---

### Post by shettysid on 2010-05-13
I have Toshiba Tecra M9 laptop running Ubuntu 9.10. 

I have set 'visual effects' to none and have no application running and yet this /usr/bin/X process gets triggered (despite trying to kill it) and takes one of my CPU usages (have a dual core) to 100% constantly. The 100% usage keeps toggling between my 2 CPUs. 

Will try upgrading to 10.04 and see if this continues. 

sid

---

### Post by vinkic on 2011-02-20
I have the similiar problem,
process /*usr*/*bin*/*X* :*0* -br -audit 0 -auth  /var/lib/gdm/ :0.Xauth -nolisten tcp vt7 uses 30%-40% all the time, I  think that OpenGL is the problem - reinstall it, I reinstall NVidia  display driver and nothing then when I try to logout I notice that cpu  ussage whent to normal. Then I save all the running process

sudo ps axf > workingsys.log

and restart. 
When the system restarted I run htop and see that process *usr/bin/X :0 -br -verbose -auth"* usess 30%-40%

then I save process list 

sudo ps axf > badsys.log

and analyse two logs. Than I saw diffrence in openbox process. When I  remove it  sudo apt-get autoremove openbox all back to normall 

I'v install compiz, metacity and openbox maybe something is happened  when all that managers are installed and that makes xorg to load cpu all  the time. 

I'm a newbee to ubuntu because this post is little funny to someone but I think I could help

---

