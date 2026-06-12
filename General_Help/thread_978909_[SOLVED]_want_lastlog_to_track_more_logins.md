---
title: "[SOLVED] want lastlog to track more logins"
date: 2008-11-11
forum: General Help
---

### Post by jlrubin on 2008-11-11
How do I make the lastlog command show more than one login?

```
lastlog -u myname -t 10
```

should show logins in the last 10 days (or however many are
stored).

Ubuntu 8.04

---

### Post by spibou on 2008-11-11
First, the man page says that the -t flag overrides the -u flag. Second, it's not clear from your post what you expected to see and what you actually see.

---

### Post by jlrubin on 2008-11-11
> **spibou said:**
> First, the man page says that the -t flag overrides the -u flag. Second, it's not clear from your post what you expected to see and what you actually see.
You're right - the man page says that lastlog -u requests "the lastlog record" for that user.

My man page, with the date 04/03/2008 within it, says nothing about what happens when -t and -u are used together. I hoped to see the last several logins by one user.

"-t" by itself doesn't work as expected. It always shows just one login.
The "-t" command option isn't useful unless there is a way to keep more than one record per user, so this can't be what the authors intended.

---

### Post by Sam on 2008-11-11
What about```
last $USERNAME
```?

---

### Post by jlrubin on 2008-11-11
Let's start over again. Maybe I'm wrong about the purpose of the lastlog commnad. Is there a record of the last few logins by a user? I am now using /var/log/auth.log but that requires filtering out logins by sudo, samba, cron, etc.

For the record, the box has no monitor attached. I only use SSH to login.

[edited: an earlier reply informed me of the 'last' command.]

---

### Post by jlrubin on 2008-11-11
Ah, thank you. I didn't know about the 'last' command.

---

### Post by spibou on 2008-11-11
> **jlrubin said:**
> You're right - the man page says that lastlog -u requests "the lastlog record" for that user.

My man page, with the date 04/03/2008 within it, says nothing about what happens when -t and -u are used together. I hoped to see the last several logins by one user.
I stand corrected then, yours is more recent than mine.

---

