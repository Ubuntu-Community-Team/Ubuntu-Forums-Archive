---
title: "[SOLVED] Start VNC with Cron"
date: 2008-11-13
forum: General Help
---

### Post by fluffman86 on 2008-11-13
For some unknown reason, I cannot get VNC to start a new open connection when it runs from cron, or when the computer starts up.  Does anyone know how to do this?

What I'm trying to do is write a script that will open a new VNC connection
```
vncserver :99
```
then open firefox to a web page on that VNC connection
```
firefox http://example.com --display=:99 &
```
take a screenshot with vncsnapshot and save it so folder "screenshots"
```
vncsnapshot -jpeg -nocursor -passwd /home/username/.vnc/passwd \
127.0.0.1:99 /home/username/screenshots/1.jpg
```
Then I kill firefox, open a new webpage with firefox, take another vncsnapshot, and repeat until I take all of the pictures I need, then kill vncserver.  

If I run my script from the command line, everything works perfectly.  But when I put this into a cron job, vncserver never starts.  I can watch the System Monitor and see cron running, and firefox opening and closing as expected, but it never starts the process Xtightvnc (from the vncserver command)...which it *does* if I run the script manually.

If it helps, I've tried creating the cron job by putting the commands into the cron.hourly folder and by creating a file called "cronshot" which contained the text:
```
*/5 * * * * /home/username/startscreenshots
```
and then running "crontab cronshot" to add the code to cron, and it shows up properly when I run crontab -l.

Let me know if you need more info, but that should be it.  Does anyone know either how to fix this or how to do it differently?

Solution is down this page a bit, post #7.

---

### Post by geirha on 2008-11-13
The vncserver probably needs to know which display to connect to. For the first user logged in, the display is typically :0, so try prepending the command with DISPLAY=:0

```
DISPLAY=:0 vncserver ...
```

---

### Post by fluffman86 on 2008-11-13
no dice.  I get the same thing whether I do DISPLAY=:99 or vncserver :99

---

### Post by fluffman86 on 2008-11-13
Oh, hmm...looks like cron shouldn't start *any* gui apps.  Is there a way around this?

---

### Post by unutbu on 2008-11-13
cron can launch graphical apps; I often give myself reminders this way.

Perhaps check that ~/.Xauthority is owned by $USER, not root. When it's owned by root, cron can't launch graphical apps (though it can still launch non-graphical ones).

Also, perhaps add some debugging info to the startscreenshots script:
```

vncserver :99 2>/home/fluffman86/cron.out
sleep 3  # may help, may not.
firefox http://example.com --display=:99 2>/home/fluffman86/cron.out &
vncsnapshot -jpeg -nocursor -passwd /home/username/.vnc/passwd \
127.0.0.1:99 /home/username/screenshots/1.jpg 2>/home/fluffman86/cron.out
```
Then look through ~/cron.out for clues.

When you run jobs through cron, the commands are run in a very stripped-down environment. 
It may help to add some of those environment variables back into your cron environment by adding stuff like this to the top of cronshot:

```
USER=fluffman86
HOME=/home/fluffman86
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/fluffman86/bin
DISPLAY=:99  # You shouldn't need to do this here, but it wouldn't hurt.
MAILTO=fluffman86
```

---

### Post by geirha on 2008-11-13
Oh I see, it starts its own X server. In that case it should work to run it from cron, but remember that cron's environment is fairly minimal, so it might lack the proper PATH or similar. If a cronjob fails, cron will mail you about it. Run ```
mail
``` to read such mails

---

### Post by fluffman86 on 2008-11-14
Thanks for your help, guys.  I ended up starting vnc at startup by changing /etc/rc.local to look like this:
```

echo 0 >/proc/sys/kernel/sysrq
su - username -c "/usr/bin/tightvncserver :99 > /tmp/vncserver.log 2>&1 &" &
exit 0

```

Everything works fine now.  :)

---

