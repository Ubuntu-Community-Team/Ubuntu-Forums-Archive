---
title: "Smart selftest error, is this serious?"
date: 2006-09-26
forum: Hardware &amp; Laptops
---

### Post by nocturn on 2006-09-26
I ran a SMART long selftest on my drive, and it reports this:

```

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error

# 1  Extended offline    Completed: read failure       80%     14206         41606202

```

Do I need to worry (yet)?

---

### Post by kidders on 2006-09-26
Hi there,

If you have been using your hard disk's SMART feature for a long time, then perhaps not, because the death clock will probably be relatively accurate.

Self test failures often mark the beginning of the end for a hard disk though, so I wouldn't count on its future reliability. In terms of this specific error, if you know what it was that damaged the unreadable sector, you can probably safely ignore the problem.

---

### Post by nocturn on 2006-09-26
It fails nearly the same on consecutive tests.

I did have some power failures recently, maybe that's the cause...

Is there anything I can do to further test this drive or to clear the error (format?).

---

### Post by kidders on 2006-09-26
Omg you're a staff member ... I hadn't realised!

Afaik the specific test you quoted is an "extended" test which does a pass over your drive's surface. It's not uncommon for small damaged areas to develop over time. You *can* flag them as unusable by formatting the disk, if you want to. I've never actually done it, but it seems like mkfs's "-c" switch is the thing to use.

It worries me that you say your failures are "**_nearly_** the same" from test to test. I'd feel happier if they were identical.

---

### Post by nocturn on 2006-09-26
> **kidders said:**
> Omg you're a staff member ... I hadn't realised!

Afaik the specific test you quoted is an "extended" test which does a pass over your drive's surface. It's not uncommon for small damaged areas to develop over time. You *can* flag them as unusable by formatting the disk, if you want to. I've never actually done it, but it seems like mkfs's "-c" switch is the thing to use.

It worries me that you say your failures are "**_nearly_** the same" from test to test. I'd feel happier if they were identical.

Thanks for your help kidders.

Yes, the outcome varies a little:
# 3  Extended offline    Completed: read failure       80%     14206         41548111
# 4  Extended offline    Completed: read failure       80%     14206         41606202


the LBA is not identical and that worries me too.  This disk is in my server, and although I have backups of the data on a second disk, it worries me that it might be dying.

---

### Post by kidders on 2006-09-26
Hmm... when disks in my server begin to fail, I swap them out into my personal computer. I don't like taking risks with servers ... even little risks :-P

Although, if (like me) you're using RAID ... say RAID 5 maybe ... it *should* be theoretically safe to leave the drive there until it fouls up. Do you suppose it would be foolish to rely on RAID like that?

Anyhow, since you said the word "server", I'd swap the disk out ... just to be safe.

---

### Post by nocturn on 2006-09-26
> **kidders said:**
> Hmm... when disks in my server begin to fail, I swap them out into my personal computer. I don't like taking risks with servers ... even little risks :-P

Although, if (like me) you're using RAID ... say RAID 5 maybe ... it *should* be theoretically safe to leave the drive there until it fouls up. Do you suppose it would be foolish to rely on RAID like that?

Anyhow, since you said the word "server", I'd swap the disk out ... just to be safe.

If this was a corporate server, I'd do just that.  But it is my home server and I don't have any spare parts left.  Sigh, I'll guess I better budget a new drive, but that might take a while.

To rely on raid and to what degree depends on the purpose of your server and the means you have available.  I used to admin big expensive Solaris boxes and pre-emptive replacements made sense and the cost was no problem to the clients.
But when you use off-the-shelve PC hardware and money is thigh, well, things tend to be different :-(

---

