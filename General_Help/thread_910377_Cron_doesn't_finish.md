---
title: "Cron doesn't finish"
date: 2008-09-04
forum: General Help
---

### Post by deepc2006 on 2008-09-04
Hello,
i have a ubuntu 8.04 as a Zimbra mailserver.
To fetch emails from different pop3 accounts i wrote a little bash script to trigger fetchmail:

```

users="/usr/local/server/fetchmail/fetchmail.userx15m /usr/local/server/fetchmail/fetchmail.usery15m /usr/local/server/fetchmail/fetchmail.userz15m"
fetch="/usr/bin/fetchmail -f "

for user in $users; do
        $fetch $user
done


```

When i start this script in command it works as it should, but startet with cron, only the first file (userx) is processed.

Can anybody help me and tell me why this happens?

Thx
DC

---

### Post by Peter09 on 2008-09-04
Not an expert on scripts but I would check that the first iteration is not exiting with an error, are you logging the output anywhere?

---

### Post by deepc2006 on 2008-09-04
No it doesn't terminat with an error. Nothing in the log.
I just tested running the job with gnome-scheduler (run task) and it worked as it should.
It seams as if cron terminates after the first loop if started by time.

---

