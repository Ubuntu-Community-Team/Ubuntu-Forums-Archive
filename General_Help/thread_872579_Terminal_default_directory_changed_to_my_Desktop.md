---
title: "Terminal default directory changed to my Desktop"
date: 2008-07-28
forum: General Help
---

### Post by RuleMaker on 2008-07-28
Normally the terminal started with my home directory and now it starts on my desktop, like this:
```
rulemaker@ubuntu:~/Desktop$
```
Is it possible to change it back to it's old state?

---

### Post by northern lights on 2008-07-28
ould you post the output of ```
cat /home/USER/.profile
```where USER is your username?

Most likely the default working directory has been set to '~/Desktop/' somewheres in there.

---

### Post by justleen on 2008-07-28
do a ```
 echo $HOME 
```
that should be set to /home/user

this is defined in the /etc/passwd file. Check what it says in there for your account.
```
 cat /etc/passwd |grep leen
leen:x:1000:1000:leen,,,:**/home/leen**:/bin/bash 
```

---

### Post by RuleMaker on 2008-07-28
Thank you both for trying to help, but I solved this just by restarting my X server (ctrl+alt+backspace). I was dumb to ask and not to try the most obvious thing first.

---

### Post by stlsaint on 2009-12-07
Post removed.

---

### Post by Pushpalanka on 2011-03-23
How can we set the default directory to a preferred one of our choice?:)

---

