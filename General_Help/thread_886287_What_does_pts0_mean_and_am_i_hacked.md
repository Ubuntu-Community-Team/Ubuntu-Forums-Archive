---
title: "What does pts/0 mean and am i hacked"
date: 2008-08-11
forum: General Help
---

### Post by pooppoop on 2008-08-11
Hi, this is the output of my users:
pooppoop@Home:/bin$ users
pooppoop pooppoop

and this is the who command:
pooppoop@Home:/bin$ who -u
pooppoop    tty7         2008-08-10 21:55   .         12844 (:0)
pooppoop    pts/0        2008-08-11 07:08   .         14158 (:0.0)

what does it mean?

how can i see if someone has connected in the past to my box?
are there any logs?
i have nxserver running btw/

---

### Post by Vivaldi Gloria on 2008-08-11
> **pooppoop said:**
> and this is the who command:
pooppoop@Home:/bin$ who -u
pooppoop    tty7         2008-08-10 21:55   .         12844 (:0)
pooppoop    pts/0        2008-08-11 07:08   .         14158 (:0.0)


tty7 is the main terminal where your desktop is
pts/0 is the gnome-terminal

> how can i see if someone has connected in the past to my box?
are there any logs?

In general the who command is good for that moment. Try "watch who" for updating login info.

See /var/log/auth.log for loggin attempts.

---

### Post by mcduck on 2008-08-11
To put it more simply, every temianl you have open counts as you being logged in one more time. So logging in to desktop and then opening a terminal means that you are logged in twice.

---

### Post by pooppoop on 2008-08-11
Wow, thanks for the info.
looking at /var/log/auth.log file isn't very helpful since i can't see the IP used to connect to sshd.
what can i do, and what are suspicious line to look for in that file?

---

### Post by Vivaldi Gloria on 2008-08-11
> **pooppoop said:**
> looking at /var/log/auth.log file isn't very helpful since i can't see the IP used to connect to sshd.


??

It shows the IPs.

---

### Post by pooppoop on 2008-08-11
you are right it does.
does this log rotates or something?
because it's first dates are only august 6, and i installed the system months ago

---

### Post by Dougie187 on 2008-08-11
yes it does. if you do an ls /var/log you will see there is another one called auth.log.0 (possibly more) those are the old log files. Im not sure how many it keeps or how long they go back, but those are the logs. Also, you can simply type last to see who has logged in and information about it, like when they logged in, and if they are still logged in. I am also not sure if it tells you where they logged in from (i think so, but all mine are local so I couldn't tell you right now.)

---

### Post by pooppoop on 2008-08-11
I have nxserver installed.
i noticed that there are ip addresses that connected to my machine.
i am sure it is not my ip address that i use to connect remotely.

is there any other explanation to this expect being hacked into?

what steps can i take to insure this is the case.
and how can i check the changes made to my machine(rootkits, reverse shells and etc)?

thanks in advanced

---

### Post by cariboo on 2008-08-11
You can find out who connected to your computer by using whois for example:

```
whois <ip address>
```

Where <ip address> is the unknown ip address. This won't give an answer as to who it was, but it will give you the ip address of the bad guy. Most isp's have an abuse email address in the whois listing, if you note the date and time you could always try to contact the abuse email address and report what you see.

Jim

---

### Post by jerome1232 on 2008-08-11
> **cariboo907 said:**
> You can find out who connected to your computer by using whois for example:

```
whois <ip address>
```

Where <ip address> is the unknown ip address. This won't give an answer as to who it was, but it will give you the ip address of the bad guy. Most isp's have an abuse email address in the whois listing, if you note the date and time you could always try to contact the abuse email address and report what you see.

Jim

That is good info, I think will start doing that to the ip's That attempt multiple repeated logins to my ssh server.

---

### Post by pooppoop on 2008-08-11
> **cariboo907 said:**
> You can find out who connected to your computer by using whois for example:

```
whois <ip address>
```

Where <ip address> is the unknown ip address. This won't give an answer as to who it was, but it will give you the ip address of the bad guy. Most isp's have an abuse email address in the whois listing, if you note the date and time you could always try to contact the abuse email address and report what you see.

Jim

this doesn't help me at all, since most abusers use proxies.
besides, the hacker could have cleaned the log file from his ip

---

