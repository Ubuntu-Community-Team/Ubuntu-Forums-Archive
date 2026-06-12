---
title: "Waking up from &quot;suspend mode&quot; works only once between shutdowns"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by xp_newbie on 2006-08-28
waking up from "suspend mode" seems to work on my Lenovo 3000 N100 laptop - but only the first time after a machine restart...

That is, if I close my laptop's cover, let it suspend by itself and come back an hour later - it will wake up to exact previous state before it went to sleep. However, if I repeat the same thing again **without shutting the laptop**, it returns with a completely dead system (except that for some reason the power LED is on and I need to shut it down in order to reboot again).

For a while I thought that I can either live with this problem or that it will be soon fixed. But now it is becoming just too annoying. Any idea whether there is a workaround for this? Or better yet a fix in the horizon?

Thanks!
Alex

---

### Post by arijarot on 2006-09-06
i'm sorry to hear about your suspend mode problem...i am interested in the n100, what are the specs of your machine... could you give me an update as to your experiences with the n100, please. 

thanks :)

---

### Post by xp_newbie on 2006-09-06
> **arijarot said:**
> i am interested in the n100, what are the specs of your machine...See specs in attached PNG snapshot.  

> **arijarot said:**
> could you give me an update as to your experiences with the n100, please.Nothing special. Works OK, not too impressive. The only thing that "impressed" me was the amout of crapware that Lenovo crammed into the Windows XP pre-install in this poor laptop - most of it spyware. I removed all of it. I am mostly using Ubuntu on it.

---

### Post by jakster on 2006-10-16
I have exactly the same problem on my Nec Versa P550, using XGL. It worked once, had something to do with the screensaver. If anyone has an solution that will be awesome.

---

### Post by xyz on 2006-10-16
Don't know if this'll work you but it did for my Toshiba Satellite A 40!
See my sig!

---

### Post by jakster on 2006-10-16
Oke nothing to do with screensaver,the second time the Xgl server seems to crash (first time I see the KDE screen lock coming up first). I try the page you gave me as well.

---

### Post by jakster on 2006-10-16
Oke found an solution (should be a better solution but this works so I don't try anything else at the moment)

As root, make a file /etc/acpi.d/suspend.d/01-switch-console.sh 
```

#!/bin/sh
chvt 13

```

and a file /etc/acpi.d/resume.d/99-back-to-x.sh

```

#!/bin/sh
chvt 7

```

Then give them permissions ::

```

chmod 755 /etc/acpi.d/suspend.d/01-switch-console.sh
chmod 755 /etc/acpi.d/resume.d/99-back-to-x.sh

```

My consoles are now not pretty anymore, but he it works :-)

---

### Post by xp_newbie on 2006-10-17
Are you sure it now works 100% ?

I am asking because it seems that in my case the problem seems to have been solved without me doing anything (except for keeping installing the updates when notified by the update manager).

Well, not solved completely. I still get every once in a while a message saying that "there was a problem in returning from suspend mode", and then referes me to an article entitled: [GNOME Power Management]("http://www.gnome.org/projects/gnome-power-manager/faq.html").

The problem is... I have no idea what's going on and what really cause the problem, so I do... nothing. I must understand what I am doing before I do it.

I vaguely remember some reference to look at some log file, but I don't remember which one (there are so many of them!).

This problem is becoming weird, since I cannot reproduce it easily anymore.

---

### Post by xyz on 2006-10-18
> **jakster said:**
> Oke found an solution (should be a better solution but this works so I don't try anything else at the moment)

As root, make a file /etc/acpi.d/suspend.d/01-switch-console.sh 
```

#!/bin/sh
chvt 13

```

and a file /etc/acpi.d/resume.d/99-back-to-x.sh

```

#!/bin/sh
chvt 7

```

Then give them permissions ::

```

chmod 755 /etc/acpi.d/suspend.d/01-switch-console.sh
chmod 755 /etc/acpi.d/resume.d/99-back-to-x.sh

```

My consoles are now not pretty anymore, but he it works :-)

I don't get this! I created the file, saved it as but it doesn't show anywhere?

---

### Post by xp_newbie on 2006-10-27
jakster & xyz: why did you have to create these files, when some version of them is already there (i.e. with Ubuntu installed out-of-the-box with no special customization needed)?

I am referring to the following files:

**/etc/acpi/suspend.d/75-console-switch.sh** - which contains:

```
#!/bin/sh

# And remember which console we're on
CONSOLE=`fgconsole`

# Change away from X, otherwise it'll blow up when we POST the video interface
chvt 12

```
and /etc/acpi/resume.d/65-console.sh - which contains:

```
#!/bin/sh

# Some hardware needs another X/console switch in order to bring stuff back
chvt $CONSOLE;
if [ x$DOUBLE_CONSOLE_SWITCH = xtrue ]; then
  chvt 12;
  chvt $CONSOLE;
fi
```
Aren't these doing exactly as you described above?

BTW, I am still looking for some log file that details what exactly fails when my laptop returns from suspend mode.

Thanks,
Alex

---

