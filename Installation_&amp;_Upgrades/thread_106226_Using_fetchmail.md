---
title: "Using fetchmail"
date: 2005-12-20
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-12-20
I have installed fetchmail. If I start it with this command I get:

mos@ubuntu:~$ fetchmail -c
464 messages (464 seen) for tulsoba at pop.mail.yahoo.com (4805311 octets).
mos@ubuntu:~$

But nothing happens. How do I make it put all the messages somewhere?

---

### Post by PMO6022 on 2005-12-20
I don't think you need the -c option.  From the man page:> -c | --check
              Return  a  status  code  to indicate whether there is mail waiting, without actually fetching or deleting mail (see EXIT  CODES  below)... 
I always just run fetchmail without any options.  The mail goes to /var/mail/<username>, and I read it with mutt.  Here is a link I used to get fetchamil working with my gmail account, which should be similar to a yahoo account: [http://freshmeat.net/articles/view/1673/]("http://freshmeat.net/articles/view/1673/")

---

### Post by bigblop on 2005-12-20
nothing goes to /var/mail/<username>

actually my username is not even a folder in /var/mail/ so I have tried to make it myself, but that still does not help

---

### Post by PMO6022 on 2005-12-20
Hmm.  What happens if you type "mail" (without quotes) at the command line?  See if this is any help: [http://www.ubuntuforums.org/showthread.php?t=102941]("http://www.ubuntuforums.org/showthread.php?t=102941")  

Fetchmail just worked for me out of the box, so I may not be so much help...
Good luck

---

