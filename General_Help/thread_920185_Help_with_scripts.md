---
title: "Help with scripts"
date: 2008-09-15
forum: General Help
---

### Post by Jeenyus on 2008-09-15
I want to create something (I'm assuming a script would be easiest) to create a "sleep" function like the one found on most TVs.  I would like the be able to enter the time that I want my computer to stay on, then after that time I would like it to safely.  I don't have much experience with scripts so I was wondering if anyone has any website suggestions for some info on script commands or some suggestions it would be greatly appreciated.

Thanks,
Jeenyus

---

### Post by rraj.be on 2008-09-15
> **Jeenyus said:**
> I want to create something (I'm assuming a script would be easiest) to create a "sleep" function like the one found on most TVs.  I would like the be able to enter the time that I want my computer to stay on, then after that time I would like it to safely.  I don't have much experience with scripts so I was wondering if anyone has any website suggestions for some info on script commands or some suggestions it would be greatly appreciated.

Thanks,
Jeenyus

You can use shutdown command with options to do this.

Example```
shutdown 10
```

this will shudown the system in 10 minutes

other options

> shutdown [OPTION]... TIME [MESSAGE]

OPTIONS
       -r     Requests  that  the system be rebooted after it has been brought
              down.

       -h     Requests that the system be either halted or powered  off  after
              it has been brought down, with the choice as to which left up to
              the system.

       -H     Requests that the system be halted after  it  has  been  brought
              down.

       -P     Requests  that  the  system  be  powered  off  after it has been
              brought down.

       -c     Cancels a running shutdown.  TIME is  not  specified  with  this
              option, the first argument is MESSAGE.

       -k     Only  send  out  the warning messages and disable logins, do not
              actually bring the system down.



       TIME  may  have  different  formats, the most common is simply the word
       ’now’ which will bring the system down immediately.  Other  valid  for&#8208;
       mats  are  +m,  where m is the number of minutes to wait until shutting
       down and hh:mm which specifies the time on the 24hr clock.


---

### Post by iaculallad on 2008-09-15
You can use at or cron job:

```
at 10pm
at> halt
```

(Press CTRL+D)

---

### Post by aloshbennett on 2008-09-15
> at 9:55pm: sudo fire-hadron -type proton -direction clockwise
at 9:57pm: sudo fire-hadron -type proton -direction anticlockwise
at 10:00pm: find 'higgs-boson' -exec "sudo IMPLODE"

If its just a music player you want to shutdown, you could write a script like "killall xmms" and add it to a cron job:-)
(ie, if xmms is your music player)

---

