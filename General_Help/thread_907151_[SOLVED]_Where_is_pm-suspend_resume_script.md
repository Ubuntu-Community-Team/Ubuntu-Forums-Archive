---
title: "[SOLVED] Where is pm-suspend resume script?"
date: 2008-09-01
forum: General Help
---

### Post by SiHa on 2008-09-01
Hi,

I'm using Mythbuntu 8.04.1,  on a remote frontend.
System is an old IBM Netvista (8307) P4 2GHz

Trying to use pm-suspend & pm-hibernate.

I want to be able to suspend to ram. I can suspend and hibernate successfully. I can resume semi-successfully (system comes back up, and I get video).

*but* 

The frontend can no longer see the backend server.
The remote doesn't work.

Retarting LIRC then mythfrontend works.

I could probably play for ages adding modules to a whitelist or something, but I'm all for a dirty hack sometimes and I think this is one of those times.

There must be a script that is run on resume?

I'd like to kill mythfrontend and LIRC on suspend and restart on resume. I'm sure I can do the first part by editing pm-suspend, but I can't find a script that runs on resume.

I've tried adding to /etc/acpi/resume.d. but those scripts don't run (I've added a line that echoes to a logfile to check) after pm-suspend or -hibernate.

If anyone can point me in the direction of the elusive resume script, I'd be most grateful.

Either that, or tell me how to get acpi suspend to work, so that the resume.d scripts will run on resume.

Thanks all.

---

### Post by caljohnsmith on 2008-09-01
From the pm-suspend man page, I think this might be useful:
> **/etc/pm/sleep.d, /usr/lib/pm-utils/sleep.d**
Programs in these directories (we call them hooks) are combined and executed in C sort order before suspend and hibernate with as argument ´suspend´ or ´hibernate´. [COLOR="Blue"]Afterwards they are called in reverse order with argument ´resume´ and ´thaw´ respectively[/COLOR]. If both directories contain a similar named file, the one in /etc/pm/sleep.d will get preference. It is possible to disable a hook in the distribution directory by putting a non-executable file in /etc/pm/sleep.d.
[B]
/var/log/pm-suspend.log[/B]
[COLOR="Blue"]The log file showing what is done on suspend/hibernate and resume/thaw.[/COLOR]

**CONFIGURATION VARIABLES**
Configuration variables defined by pm-utils. These can be set in any file in /etc/pm-utils/config.d

       **SUSPEND_MODULES**
       [COLOR="Blue"]Modules to unload before suspend[/COLOR]

Let me know if you have any luck. :)

---

### Post by SiHa on 2008-09-01
[QUOTE=caljohnsmith;5705728]Afterwards they are called in reverse orderQUOTE]

Ah, I think that might be the clue I was looking for :idea:  I've been looking for a resume.sh or resume.d.

I'll have a play tonight and report back.

Thanks.

---

### Post by SiHa on 2008-09-01
Well success...
...sort of

I made a little script that kills mythfrontend at suspend and restarts LIRC followed by mythfrontend on resume.

```
#!/bin/bash

. /usr/lib/pm-utils/functions

RETVAL=0
case "$1" in
	suspend|hibernate)
		killall mythfrontend.real
		RETVAL=$?
		;;

	resume|thaw)
                /etc/init.d/lirc restart
                mythfrontend &
		RETVAL=$?
                ;;
esac

```

Please excuse any glaring errors (RETVAL lines??). My scripting was learnt at the school of MS-DOS batch file programming about 20 years ago. Linux is very new to me, bash scripting even newer.

Anway, all *seems* to work fine. /var/log/pm-suspend.log shows LIRC & Mythfrontend starting normally.

But Myth doesn't respond to the remote and irw doesn't rsepond.

PS shows an LIRC process running.

If I manually run the above script (called, imaginatively, 00test), after stopping mythfrontend.
```
$sudo bash 00test resume
```

Everything works normally, and Myth sees the remote.

So it seems that although LIRC appears to start properly when the script runs at resume, it doesn't. When run manually, everything is fine.

I tried inserting a 'sleep 10' line in between, in case myth was starting before LIRC was fully initialised, but it didn't help.

I would be grateful if anyone has any insight as to why this might be. My only thought is that it perhaps has something to do with the fact that the resume scripts are run as root, rather than mythtv?
I was prompted to think this because the first time the script ran I got a message telling me that I must be part of the 'mythtv' group, and offering to add me. As the 'frontend' user is already added, I assumed it must be referring to the root user.

I have no idea how to go about debugging that theory though. :???:

---

### Post by SiHa on 2008-09-02
I will change ```
/etc/init.d/lirc restart
``` to ```
sudo -u frontend /etc/init.d/lirc restart
```
Will sudo work from a script?
Do I need to edit sudoers to allow frontend to run LIRC without a password?

---

### Post by caljohnsmith on 2008-09-02
Instead of using sudo to change user, have you experimented with "su"? Try the following syntax:
```
su -l <username> -c <command>
```

---

### Post by sdennie on 2008-09-02
If mythfrontend is an X app, you'll need to use su and set the DISPLAY variable properly.  I use many things in /etc/pm/sleep.d that require X and use this form:

```

#!/bin/bash

XUSER=my_username

DISPLAY=:0.0 su ${XUSER} -c "some_command_that_requires_X"

```

---

### Post by caljohnsmith on 2008-09-02
> **vor said:**
> If mythfrontend is an X app, you'll need to use su and set the DISPLAY variable properly.  I use many things in /etc/pm/sleep.d that require X and use this form:

```

#!/bin/bash

XUSER=my_username

DISPLAY=:0.0 su ${XUSER} -c "some_command_that_requires_X"

```
Just wondering Vor, but when I run:
```
su <username> -c "env|grep -i display"
```
It returns "DISPLAY=:0.0" as I would expect for <username>. So just for my own understanding, why in your case do you have to specify the DISPLAY variable? Is ":0.0" not the default DISPLAY value for "my_username" in your situation?

---

### Post by sdennie on 2008-09-02
> **caljohnsmith said:**
> Just wondering Vor, but when I run:
```
su <username> -c "env|grep -i display"
```
It returns "DISPLAY=:0.0" as I would expect for <username>. So just for my own understanding, why in your case do you have to specify the DISPLAY variable? Is ":0.0" not the default DISPLAY value for "my_username" in your situation?

Well, remember that /etc/pm/*.d stuff is run as root and without any knowledge of the the user or display it should be using.  On the command line, I don't doubt that DISPLAY is set properly unless you go into a "sudo -i" but, for a process completely outside the realm of userspace like pm-utils, it won't be set.

---

### Post by SiHa on 2008-09-03
caljohnsmith:
Well, I tried both ```
su -l frontend -c /etc/init.d/lirc restart
``` and ```
su frontend -c /etc/init.d/lirc restart
```

Both prompted for a password, and both returned
```
USAGE: /etc/init.d/lircd options {stop|start|restart|reload|force-reload}
``` but didn't actually do anything. I'm assuming the LIRC**D** reference is a typo, as /etc/init.d/lircd doesn't exist

vor:
Thanks for the advice. LIRC is not an X app AFAIK, so I didn't try your suggestion, but for completeness, I will do tonight. 

Anyway. I think I need to move this to another thread, my problem as stated is fixed - I know where to put stuff to run at resume. I think the running as root thing was a red herring - 'lirc restart' has to be run as root anyway.

All I've got to do know is get it to run correctly!  :confused:

Thanks both for your help - I'm heading over to the Mythbuntu forum, as that's where most of the LIRC activity seems to be.

---

### Post by caljohnsmith on 2008-09-03
> **SiHa said:**
> caljohnsmith:
Well, I tried both ```
su -l frontend -c /etc/init.d/lirc restart
``` and ```
su frontend -c /etc/init.d/lirc restart
```

Both prompted for a password, and both returned
```
USAGE: /etc/init.d/lircd options {stop|start|restart|reload|force-reload}
```
I believe you are getting that error because you need to put the whole su command argument in quotes, otherwise lirc does not see the "restart" argument and gives you the error you got. Try this:
```
su frontend -c "/etc/init.d/lirc restart"
```
Give it a try and let me know how it goes.

---

### Post by SiHa on 2008-09-03
funny - I nearly tried that, but thought 'Nah-you don't usually need quotes'.
What do I know?
Anywho - it's probably academic now. When I do 'sudo -u frontend...' it runs, but I get permission denied. LIRC needs to be restarted as root.
Whatever, I'll try.

---

### Post by SiHa on 2008-09-04
Well, it runs but I still get permission denied. Like I said - LIRC restart needs to be done as root. I'm marking this thread as solved.

---

### Post by gsfjim on 2008-09-09
First, If IRW is responding, you shouldn't need to restart LIRC, the issue is probably with mythfrontend.

As far as restarting mythfrontend, I would use sudo instead of su. Using su in a script is usually not a great idea because it requires the target users qualifications to be entered, whereas sudo uses the issuing users qualifications.  In this case, with pm-utils the issuing user is root who is already qualified to run anything as any user without having to make changes to the sudoers file. This simplifies the issue because a password won't be asked for. If your hook just calls your script, the script will run as root, your killall statement should be fine as is and your mythfrontend statement would be something like:

DISPLAY=:0.0 sudo -u frontend /usr/bin/mythfrontend

assuming that the username is frontend and mythfrontend is located in /usr/bin/

hope this helps
-Jim

---

### Post by SiHa on 2008-09-10
> **gsfjim said:**
> First, If IRW is responding, you shouldn't need to restart LIRC, the issue is probably with mythfrontend.


Hi Jim,

Thanks, but IRW wasn't responding, that's why LIRC needed to be restarted. ```
MODE2 -d /dev/lirc0
``` also gave nothing. Anyway, I've solved that problemn now - see this thread: [http://ubuntuforums.org/showthread.php?t=909195](http://ubuntuforums.org/showthread.php?t=909195)


> As far as restarting mythfrontend, I would use sudo instead of su. Using su in a script is usually not a great idea because it requires the target users qualifications to be entered, whereas sudo uses the issuing users qualifications. In this case, with pm-utils the issuing user is root who is already qualified to run anything as any user without having to make changes to the sudoers file. This simplifies the issue because a password won't be asked for. If your hook just calls your script, the script will run as root, your killall statement should be fine as is and your mythfrontend statement would be something like:

DISPLAY=:0.0 sudo -u frontend /usr/bin/mythfrontend


Well, my script siply calls:
```
mytfhrontend &
``` and it seems to work OK.

I hadn't considered until now, that this means it is running as root, rather than 'frontend'. The first time I ran it, I got the popup asking if I (root) wanted to be added to the mythtv group, so I OK'ed that and everything has been fine since.

I guess it's bad practice to run stuff as root that doesn't need to? I'll try changing the statement to the one you suggest - thanks.

I'll try that in the next couple of days - the box is in bits at the moment. I'm going to try a hardware fix :shock: to stop the box displaying to VGA (instead of DVI) if the TV isn't switched on at boot.

---

### Post by Eldis on 2009-02-11
I'm curious did you ever get this to work ?

Could you show me the script you ended up with ?

My resume works fine remote works but mythfrotnend does not restart.

---

### Post by SiHa on 2009-03-17
It's been working flawlessley for about six months now. The machine actually gets rebooted about once a month by accident, but is quite happy simply being endlessley suspended & resumed.

Here's what I've got.

**/usr/lib/pm-utils/sleep.d/00test** (never got round to giving it a sensible name!)

```
#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
	suspend|hibernate)
		echo "Suspending..." > /home/frontend/suspend.log
		killall mythfrontend.real
		modunload lirc_serial lirc_dev
		;;

	resume|thaw)
		echo "Resuming..." > /home/frontend/resume.log
		modreload lirc_serial lirc_dev
		mythfrontend &
                ;;
esac
```

With the following line at the end of **/etc/sudoers** (edited with visudo)
```
frontend ALL=NOPASSWD: /usr/sbin/pm-suspend, /usr/sbin/Mythrestart
```

And the following in my irexec lircrc:```
begin
    remote = lircd.conf
    prog = irexec
    button = Power
    config = sudo /usr/sbin/pm-suspend
    repeat = 0
    delay = 0
end

```

HTH, Simon

---

