---
title: "Laptop not shutting down completely lately w/ Ubuntu 14.04"
date: 2016-04-30
forum: Hardware
---

### Post by Oinos on 2016-04-30
It started a week or two ago. I always turn it off the way it's supposed to, by clicking on the very top-right corner > Shut down... > Shut Down. However, 5 or so times it appears that the last or one of the last steps of the shutting down does not execute or the system freezes during its execution. Everything goes normal, but then it just stays with display off, unresponsive anything. just 'laptop on' LED notification working. The only way to shut it down then is by the turn on button.
Why this could be the case? What procedure or inspection should I do the next time it happens or in advance of it?

I'm on a DELL laptop, Latitude D430, [full specs](http://i.imgur.com/x5RpHQ8.png).

---

### Post by kenneth-fechter on 2016-05-02
What kernel are you running? 

post the output of uname -r. 

I have been having shutdown issues with my W530 on 16.04 LTS, and upgrading the kernel to 4.5.2 seemed to fix the issue. Not sure if it will help in your case, but it is worth a shot.

---

### Post by Oinos on 2016-05-03
> **kenneth-fechter said:**
> What kernel are you running? 

post the output of uname -r. 

I have been having shutdown issues with my W530 on 16.04 LTS, and upgrading the kernel to 4.5.2 seemed to fix the issue. Not sure if it will help in your case, but it is worth a shot.

I got 3.19.0-33-generic, don't know what that means.

---

