---
title: "Run application as another user"
date: 2008-08-03
forum: General Help
---

### Post by YonyonJohn on 2008-08-03
Hi, I'm making a rhythmbox remote so that I can control playback from my cellphone, the problem is php and rhythmbox are running as different users, so I need a way to execute a command as a different user (not root) without prompting for a password. I've looked around the forums but I cant find a solution. any help would be greatly appreciated.

---

### Post by deadowl on 2008-08-03
I came across this thread looking for something. Don't know how useful it will be, but it looks like the right direction.

[http://www.linuxquestions.org/questions/programming-9/run-a-script-as-a-different-user-112795/](http://www.linuxquestions.org/questions/programming-9/run-a-script-as-a-different-user-112795/)

In any case:
su - user -c "/path/to/script"

There's also this page that might help:
[http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html#s7](http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html#s7)

---

### Post by YonyonJohn on 2008-08-03
It doesn't seem to work for what I need, su and sudo both don't allow passwords to be included in the command line, instead you need to enter them after you execute the command. I need something like "su -u john -p password -c "echo hello" the important thing is that it is a one line command.

---

### Post by web4d on 2009-08-19
What you may do is something like
```
FILE=/tmp/tmp.pass.file && echo "mypassword" > $FILE && sudo -S su - myusername -c "mycommand" < $FILE && rm $FILE
```

replace mypassword, myusername and mycommand accordingly.

This comes a bit late, but probably some googlers come along this thread and find this command useful.. ;)

---

### Post by karatedog on 2009-12-28
> **web4d said:**
> What you may do is something like
```
FILE=/tmp/tmp.pass.file && echo "mypassword" > $FILE && sudo -S su - myusername -c "mycommand" < $FILE && rm $FILE
```

replace mypassword, myusername and mycommand accordingly.

This comes a bit late, but probably some googlers come along this thread and find this command useful.. ;)

A better alternative would be:
```
$ echo "<password>" | sudo -S ls 
``` that way you won't write password to a file. I'm not a security geek, but this is not a secure way do it, eventually you will store the password somewhere.

---

### Post by scales on 2010-01-23
Hi all.  Just so i am clear, i would like to run firefox as a different user (so others using the computer do not need to log me out and each have their own settings for firefox) what command would i use to run firefox as a user named USER with a password of PASSWORD ?

PS.  I want to make this a shortcur....ie. command

---

### Post by slyisarenko-ilya on 2011-12-18
Maybe firefox plugin  "profileswitcher"  can help you?

[http://freeshell.de/~kaosmos/profileswitcher-en.html](http://freeshell.de/~kaosmos/profileswitcher-en.html)

Download addon file, go to firefox 'addons' and install from file.

Plugin allows create profiles and use approriate.
But I don't find password policy. And users can login with another account.

---

### Post by lisati on 2011-12-18
May the thread sleep soundly.

---

### Post by howefield on 2011-12-18
Thread closed.

---

