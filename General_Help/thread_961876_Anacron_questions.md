---
title: "Anacron questions"
date: 2008-10-28
forum: General Help
---

### Post by jambalaya on 2008-10-28
Long time no see, so hello everyone.
I wrote this simple backup script, and I had it configured to run in cron. However, as I turn my laptop off for each night, and sometimes during the day (I know, I know, lame ;-)), I decided to use anacron for the task. So I put the call to my script inside /etc/anacrontab to look like this:
```

HOME=/home/jamba
@weekly         5       jamba.backup    $HOME/Scripts/backup.sh
# leave the environment as it was before
HOME=

```
So, this script creates a bak.tar.gz file in my home dir. However, some things are not quite right. I edited the system-global anacron file - isn't there any file per user accout? I couldn't find it in man. The file is created with root:root ownership bacause of that. I can change ownership at the end of the script, but this doesn't seem nice.

Also, I have a question about the default Ubuntu configuration of cron / anacron - in /etc/cron.daily, cron.monthly etc. there is a 0anacron file, that runs anacron -u if anacron exists. What is that for? Aren't the timestamp files updated when anacron runs normally?
Thanks.

---

