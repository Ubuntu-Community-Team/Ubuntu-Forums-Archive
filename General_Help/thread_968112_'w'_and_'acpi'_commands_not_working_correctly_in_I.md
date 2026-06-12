---
title: "'w' and 'acpi' commands not working correctly in Intrepid"
date: 2008-11-02
forum: General Help
---

### Post by Izkata on 2008-11-02
Take a look at wmii's idle time:

```
izkata@Izein:~$ w
 12:45:15 up 10:31, 13 users,  load average: 0.46, 0.25, 0.14
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
izkata   tty10    :0               11:05   15:31   2:18m  3.98s wmii
izkata   pts/11   :0.0             11:10    1:30   0.42s  0.12s bash
izkata   pts/18   :0.0             11:05    0.00s  0.34s  0.00s w
```

In Hardy, the idle time would only have been 1 or 0 seconds, as doing virtually anything will un-idle wmii.  This idle from of over 15 hours isn't even possible, as I only logged in a couple hours ago!

It was a good way to find out how long the user has been idle (one of my programs uses it), but now is completely broken.

Also newly-broken is "acpi" - my battery can last a good 4 hours, but the entire time it's discharging the new acpi command says only a couple minutes.

However, after letting it discharge to around 50%, I just noticed something that may be helpful in fixing this one:  Time is divided by 60; what should be hours is in the minutes column, and what should be minutes is in the seconds column.  Or very close to it.

EDIT:  I also suggest removing the limitation of 3+ characters on tags for a thread.  I couldn't add just plan w to the tags.

---

### Post by Izkata on 2009-05-02
acpi has now been corrected for me in Jaunty.

w still does not appear to work correctly.

I experimented more, and it looks like the IDLE column is the cumulative idle time for the tty, whereas in Gutsy, Hardy, and presumably before, it was the current idle time of the tty....

How can I get the current idle time for the tty?

---

