---
title: "Why does gconftool --get /system/http_proxy/port run several times a day?"
date: 2008-09-19
forum: General Help
---

### Post by Wickedone on 2008-09-19
The following command shows up in my auth.log file at 07:35 everyday or on every reboot?

Sep 12 11:55:53 HOST sudo:     root : TTY=unknown ; PWD=/ ; USER=username ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port

What is this command for?  Is it needed?  Can it be disabled?

W

---

### Post by Wickedone on 2008-09-20
I searched through the cron jobs and can not find where the gconftool is running from.  

I am concerned about the security of the box since I can't find where this tool is running from and why it is running.

---

