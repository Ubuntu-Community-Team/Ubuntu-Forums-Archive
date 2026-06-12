---
title: "[SOLVED] Problem with a cron job"
date: 2008-11-10
forum: General Help
---

### Post by ierpe on 2008-11-10
Quick description of the case:

We are using a java application that manages bluetooth devices. We needed a feature not yet implemented, and as it will be implemented in 2 or 3 months, I wrote a short jsp script that does what we want.

This script needs to be run every night, so I created a shell script that calls the browser pointing to my jsp page, and added this script in the cron jobs.
The cron job is being fired (I have it in the logs), but the action are actually not exectued.

First, my script was calling: firefox [http://localhost:4040/daily/process.jsp](http://localhost:4040/daily/process.jsp)
I thought that it wasnt working because,as a cronjob, no serverX was started and so firefox couldnt probably run.
So I installed lynx (command line web browser), but it still doesnt work...

My script is basically this line:
lynx --accept_all_cookies [http://localhost:4040/daily/process.jsp](http://localhost:4040/daily/process.jsp)

If I call my script from a terminal, its working fine, so why is it not working in a cron job?

Please help!

---

### Post by justleen on 2008-11-10
are you using the full path in the cron? eg. /usr/sbin/lynx ?

---

### Post by geirha on 2008-11-10
It's -accept_all_cookies with one dash (-), not two (--). Also, this will run lynx interactively, so it will never exit. Use the -dump option which will render the html, dump it as plain text and exit.

Also if the cron command gets output, like errors and such, it will mail you about it. Read such mails with the mail command
```
mail
# or
sudo mail
```

---

### Post by ierpe on 2008-11-11
yeah with the dump option now its working, thanks very much!

@geirha: its working as well with --accept_all_cookies

---

### Post by geirha on 2008-11-11
> **ierpe said:**
> yeah with the dump option now its working, thanks very much!

@geirha: its working as well with --accept_all_cookies

Ah, the man-page lists the options with one dash, so I assumed it wouldn't work. I guess lynx secretly accepts both ways then :)

---

