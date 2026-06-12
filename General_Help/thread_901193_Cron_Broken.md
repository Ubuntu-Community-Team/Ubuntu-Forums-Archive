---
title: "Cron Broken?"
date: 2008-08-26
forum: General Help
---

### Post by ShinHadoken on 2008-08-26
For a while now, I've left my pc on at night to do a few cron jobs, but none of them get done. Afterwords, whenever I type (sudo) crontab -e, I get an empty crontab. However, I noticed that the filepath for the crontab is in /tmp/cron.(ramdom 6 letters)/crontab. Should this occur? I guess the question is where *should* the crontab be, and how do I get cron to read it? Should/Can I reinstall cron?
 
Thanks a TON for your help!
 
SH

---

### Post by ShinHadoken on 2008-08-26
Bump, please.

---

### Post by ibuclaw on 2008-08-26
What jobs are you trying to run?

Regards
Iain

---

### Post by Cheesehead on 2008-08-26
For many cron jobs, you don't need sudo.
For a *user*, simply use 'crontab -e' (no sudo)
If you really need to add an *admin or root* cron job, add it to the existing crontab at /etc/crontab or put a link to your script in the cron.hourly/daily/weekly/monthly folders

_COMMON ISSUES:_
- If you enter an invalid crontab entry, crontab will tell you upon exit but the warning message is easy to miss.
- A crontab entry with a truncated path (foo instead of /bin/foo) will fail.
- A crontab entry that is too complex, or requires shell commands that are not available to cron (but are available to you) will fail.

_HOW TO TEST CRON:_
Do a user-level 'crontab -e' and enter the following:
*Try it as a shell command to make sure it works!*
```
* * * * * DISPLAY=:0.0 /usr/bin/gnome-terminal -x top
```

Once each minute, a new window should spawn and run 'top'
If it does, your cron is working just fine.

_IF YOUR CRON IS WORKING:_
Try your crontab again as a user - but not for the middle of the night.
If it still doesn't work, post the crontab for us to see.

_IF YOUR CRONTAB IS NOT WORKING:_
Reinstall using:
```
sudo apt-get reinstall cron anacron
```

---

### Post by ShinHadoken on 2008-08-26
Thanks, I'll do some work on it!

---

### Post by ShinHadoken on 2008-08-27
Well, I did your little test and found that cron was NOT working. So, I decided I'd save myself some pain, and go ahead and reinstall cron and anacron. That appears to have fixed the problem. I don't know what the deal was, but I'm just glad it's fixed.

Thanks!

SH

---

