---
title: "[SOLVED] Notifying logged-on users of an auto shutdown"
date: 2008-09-08
forum: General Help
---

### Post by Scunge on 2008-09-08
I would like to ensure that the children log off from the computer at a decent time on schoolnights, a time they know in advance.

I've read that I could issue a ```
sudo shutdown -h 5
``` using cron at appropriate times on each day of the week, or something like that. While this sounds like a plan, I think a warning would be polite but this command gives no notification except in terminal wndows.

How can I make it so that a popup window appears on the desktop of any logged-in user, saying something like "The computer will switch off in 5 minutes", and issue a shutdown command, all without me even needing to be there?

---

### Post by Thingymebob on 2008-09-09
You can use zenity to issue gtk dialogs
eg```

zenity --warning --text "The computer will shutdown in 5 minutes" --title="Auto Shutdown"

```
Not sure if you could issue this from the su crontab or if you would have to add it to each users (which means you may need to add each user to the cron.allow file in /usr/lib/cron if it doesn't exist create it and add each user name on a separate line)

---

### Post by Scunge on 2008-09-10
Nearly there!

I did the following...

I created a new file as root, */usr/bin/switchoff-warning*, with the following contents: ```
#!/bin/sh

zenity --warning --text "`date +%k.%M`: The computer will shut down in 5 minutes." --title="Auto Shutdown"

```

I put the command in its own file so that I can edit it without having to adjust every user's crontab.

Then made it executable by anybody but changeable only by me (as root): ```
$ sudo chmod 755 /usr/bin/switchoff-warning
$ ls -l /usr/bin/switchoff-warning
-rwxr-xr-x 1 root root 120 2008-09-10 14:18 /usr/bin/switchoff-warning

```

Then, logging in as each child user: ```
$ sudo su - *username*
``` I set up a cron job using ```
$ crontab -e
``` for them to run that file five minutes before shutdown time (which is 9pm when there's school the next day, 11pm otherwise): ```
55 20 * * 0-4 export DISPLAY=:0 && /usr/bin/switchoff-warning
55 22 * * 5-6 export DISPLAY=:0 && /usr/bin/switchoff-warning

```

The "export" bits I found out about from [**[color=blue]this thread[/color]**](http://ubuntuforums.org/showthread.php?t=102626), which makes the command following it appear on their display. I didn't need to do anything with any *cron.allow* file - actually, I forgot, but it seems to work anyway. Perhaps if it's not there, all users can cron.

Finally, I set up the shutdown command itself using ```
$ sudo crontab -e
``` with the entry ```
55 20 * * 0-4 shutdown -h 5
55 22 * * 5-6 shutdown -h 5
```

But... that bit doesn't seem to work (I tried it with other times to test it). The dialog box is displaying fine (on my test account) but the computer is not shutting down.

What have I done wrong?

---

### Post by whitethorn on 2008-09-10
If I remember correctly, you have to set the full path to the executable. So 
```

00 21 * * 0-4 /sbin/halt
00 23 * * 5-6 /sbin/halt 

```
I don't think you need to have it wait for 5 min.  That's already taken care of.  I'm not sure if 0-4 and 5-6 works.  Someone with a little more knowledge will have to help there

---

### Post by Scunge on 2008-09-10
Thanks, I'll try that. The thread I linked to above says the format of crontab listings, "0-6" is the same as "every day of the week", "0" being Sunday.

I wait for 5 minutes in the shutdown command so that if I happen to be logged in via SSH, I'll get a warning as well!

Edit: That works! Sorted.

---

