---
title: "Smartmontools and disk lifetime question."
date: 2008-09-11
forum: General Help
---

### Post by jesushero on 2008-09-11
I am using smartmontools to monitor the "health" of my drives. Most of the results I'm getting with most of my drives are understandable and reasonable. However, with one (rather old) drive, this occured:

First test:

```
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         3         -

```

Second test:

```
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       474         -
# 2  Short offline       Completed without error       00%         3         -

```



Is the lifetime(hours) supposed to mean how much time the drive has got until it malfunctions? If so, the first test should mean that in 3 hours my drive would no longer be with us?

How come the second test increased the lifetime to 474 hours then? Or am I missing something here?

---

### Post by fsmithred on 2008-09-11
"Remaining" and "LifeTime" are separate columns. The test was completed, so there is 00% of the test remaining. I'm pretty sure that the hours refer to the age of the drive at the time of the test. If you run 'smartctl -a [device]' the output will list errors and tell when they happened, giving the age of the drive in hours. Here's an example:

```
Error 73 occurred at disk power-on lifetime: 6545 hours (272 days + 17 hours)

```

Note: That's an old error on an old hard drive. No new errors have been recorded in a couple of years (more than 6,000 power-on hours ago), so I don't worry about it. If I started seeing new ones, I'd get worried.

---

### Post by jesushero on 2008-09-11
> **fsmithred said:**
> "Remaining" and "LifeTime" are separate columns. The test was completed, so there is 00% of the test remaining. I'm pretty sure that the hours refer to the age of the drive at the time of the test. If you run 'smartctl -a [device]' the output will list errors and tell when they happened, giving the age of the drive in hours.

Thanks for replying..

There's definitely something wrong if that refers to the the age of the drive, since that particular drive is more than 5 years old, a good few of which running in a server 24/7!!! So the age should have been a BIG number in that case!!

---

