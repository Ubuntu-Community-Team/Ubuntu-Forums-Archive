---
title: "[SOLVED] Can't get ACPI working in Hardy Heron"
date: 2008-05-16
forum: Hardware
---

### Post by malaTG on 2008-05-16
Hi everyone,

I am trying to get my ACPI working so that I can get automatic startup om my mythtv installation, however I can get it to work. I have looked in 

[http://www.mythtv.org/wiki/index.php/ACPI_Wakeup](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup)

and

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

I have tried to write a time to 

/proc/acpi/alarm 

but the computer wont start even after I have modified 

/etc/init.d/hwclock.sh 

then I discovered that my kernel is 2.6.24 and therefore I should use

/sys/class/rtc/rtc0/wakealarm

however I can't even find this file

I am unsure how to proceed and would really appreciate some help!!

/Marcus

---

### Post by malaTG on 2008-05-16
Is there no one that uses wakeup via ACPI in Hardy Heron?

---

### Post by becvert on 2008-05-25
hi there,

I'm trying to get this working as well on the kernel 2.6.24-17.
no chance so far.

Marcus have you got the following line in the startup messages? (dmesg | grep rtc)

```
/build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
```

I wonder if it's got something to do with the ACPI wakeup or not...

---

### Post by malaTG on 2008-05-26
Last weekend my motherboard burned which gave me an excuse to buy a new motherboard which works perfectly from a terminal :-)

However after a lot of attempts I still can't get wakeup function to work within mythtv :-(

When I from a terminal write to /proc/acpi/alarm 

with the command

> sudo sh -c 'echo "2008-05-26 17:58:00" > /proc/acpi/alarm'

the machine starts perfectly at the correct time. 

In the settings for the mythbackend I have written the time format

> yyyy-MM-dd hh:mm:ss

and the wakeup command

> sudo sh -c 'echo $time > /proc/acpi/alarm'

but the machine won't start and when I look in 

/var/log/mythtv/mythbackend.log

there is nothing about wakeup time etc.

Could someone plz point me in any direction. I don have a clue on what to do next....

---

### Post by majoridiot on 2008-06-02
> **malaTG said:**
> Last weekend my motherboard burned which gave me an excuse to buy a new motherboard which works perfectly from a terminal :-)

However after a lot of attempts I still can't get wakeup function to work within mythtv :-(

When I from a terminal write to /proc/acpi/alarm 

with the command



the machine starts perfectly at the correct time. 

In the settings for the mythbackend I have written the time format



and the wakeup command



but the machine won't start and when I look in 

/var/log/mythtv/mythbackend.log

there is nothing about wakeup time etc.

Could someone plz point me in any direction. I don have a clue on what to do next....

are there sudo prompts in your backend log?

---

### Post by malaTG on 2008-06-03
> **majoridiot said:**
> are there sudo prompts in your backend log?

No I have added my mythtvuser with visudo. However last night I managed to get it to work one time but I can't reproduce it. Now when I look in my mythbacken log I only get this at shutdown

2008-06-03 19:40:32.797 I'm idle now... shutdown will occur in 35 seconds.

I don't know how to proceed. I don't think it is a problem within visudo becuase I can write without using a password to /proc/acpi/alarm with my mythtv user

Could it be my settings within myth?

They are

------------------------

No start command

A "x" in the box for "block shutdown when client..."

seconds before shutdown at rest = 35 seconds

Max wait for recordings = 5 min

Start before recording = 200 s

Time format = yyyy-MM-dd hh:mm:ss

wake up command = sudo sh -c 'echo $time > /proc/acpi/alarm'

shutdown command = sudo /sbin/halt -p

No command before shutdown

--------------------------------

My visudo file looks like this

----------------------------------

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

%mythtv ALL = NOPASSWD: /sbin/shutdown, /sbin/halt, /bin/sh, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/mythshutdown

--------------------------------------

Do someone know what to do to hunt this problem down?

/Marcus

---

### Post by majoridiot on 2008-06-03
> **malaTG said:**
> 

Could it be my settings within myth?

They are

------------------------

No start command

A "x" in the box for "block shutdown when client..."



**uncheck** this box.  it will stop the backend from shutting down unless a frontend has connected.

also, you should not have a frontend open while testing this, as it will block shutdown, too.

this info was added to the ACPI wiki.  it was either overlooked or mistakenly removed at some point.

---

### Post by malaTG on 2008-06-03
Thank you for your help!

I think it is getting closer. When I did what you said and rebooted the system without having a mythtv frontend running it started writing something to /proc/acpi/alarm. 

2008-06-03 20:51:45.338 I'm idle now... shutdown will occur in 35 seconds.
2008-06-03 20:52:19.639 Running the command to set the next scheduled wakeup time :-
						sudo sh -c 'echo 2008-06-03 21:55:40 > /proc/acpi/alarm'
2008-06-03 20:52:19.763 Running the command to shutdown this computer :-
						sudo /sbin/halt -p


The problem was that the system started shutting down after 35 seconds since I had put this in the mythbackend settings. I changed the setting for shutdown when idle to 0 seconds but now nothing is written to /proc/acpi/alarm again?

/Marcus

---

### Post by majoridiot on 2008-06-03
> **malaTG said:**
> The problem was that the system started shutting down after 35 seconds since I had put this in the mythbackend settings. I changed the setting for shutdown when idle to 0 seconds but now nothing is written to /proc/acpi/alarm again?

/Marcus

setting to 0 will disable the shutdown function... it has to have something to start counting down from ;)

---

### Post by malaTG on 2008-06-04
Thank you again!

Just one follow up question...

So I can´t disable the count down function? My original idea was that mythtv doesn´t count down but just write to /proc/acpi/alarm when I shut the computer down manually. 

As I understand it I have to put a script that checks if a user has logged into my machine to stop the countdown function from shutting the computer down? And when the countdown function sees that a user is logged on it restarts the countdown?

/Marcus

---

### Post by majoridiot on 2008-06-04
> **malaTG said:**
> Thank you again!

Just one follow up question...

So I can´t disable the count down function? My original idea was that mythtv doesn´t count down but just write to /proc/acpi/alarm when I shut the computer down manually. 

this kind of subverts the intent of auto-shutdown, but could be possible using custom scripts.  
if you set a short enough duration (mine is 10 minutes), then the backend will time out and shut
down shortly after all sessions are logged off.  i find it works well on my system.

> **malaTG said:**
> As I understand it I have to put a script that checks if a user has logged into my machine to stop the countdown function from shutting the computer down? And when the countdown function sees that a user is logged on it restarts the countdown?

/Marcus

if you use this machine for things other than mythtv, then it is a good idea to use the MythShutdownCheck
script (or similar), to make sure that the system doesn't shut itself down while you are in the middle 
of doing something else.  if the script finds an active log-in, it resets the timer and starts the
countdown again.  it will continue doing this until it finds no active logins and will then shut down.

if you are trying to accomplish something different than the "standard" usage of shutdown/wake-up,
then be a little more specific about your intended goal and maybe we can help find a workable solution.

---

