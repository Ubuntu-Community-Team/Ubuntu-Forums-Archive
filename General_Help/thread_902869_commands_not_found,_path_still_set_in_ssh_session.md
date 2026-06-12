---
title: "commands not found, path still set in ssh session"
date: 2008-08-27
forum: General Help
---

### Post by sdrewert on 2008-08-27
Hi-

I am unable to run path-added commands in the path, after logging into my machine via an ssh session. This occurs in bash and tcsh. What I'd consider to be "standard" commands also work fine (e.g. ls, pwd, etc), and absolute paths work fine, but that gets very tedious after awhile. I've made path additions in /etc/profile and /etc/csh.cshrc. I have a similar problem using su, but adding su -m fixes it. It's particularly odd since `echo $PATH` presents the all path additions, and all environment variables show up - is there somewhere else I must set path additions for ssh logins? A simple login presents no problems, hence I tend to think it is not an error in /etc/profile or /etc/csh.cshrc. Any ideas? Pointing me to an article or post would be awesome, sorry to bother. Thanks in advance for any help!

-Scott

---

