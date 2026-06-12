---
title: "help with sudo and path"
date: 2008-08-12
forum: General Help
---

### Post by SwampYankee on 2008-08-12
Hi,
I am trying to run nethack wizard mode but when I do so using sudo the path can not be found.  So, if I type nethack, no problem  However, I enter sudo -s, provide the password and type 'nethack' I get this:
[http://www.newsday.com/news/local/longisland/ny-liweat0812,0,4598052.story](http://www.newsday.com/news/local/longisland/ny-liweat0812,0,4598052.story)
What can I do to run this as sudo?
thanks

---

### Post by SwampYankee on 2008-08-12
sorry, bad clipbaord move.  the result of running nethack under sudo is actually:
Command 'nethack' is available in '/usr/games/nethack'
The command could not be located because '/usr/games' is not included in the PATH environment variable.

---

### Post by Mgiacchetti on 2008-08-12
[http://answers.yahoo.com/question/index?qid=20070414031028AApf6qf](http://answers.yahoo.com/question/index?qid=20070414031028AApf6qf)

---

### Post by sisco311 on 2008-08-12
You can set the PATH environment variable:
```
sudo env PATH=$PATH nethack
```

[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/50797](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/50797)

---

### Post by SwampYankee on 2008-08-12
tried to set the path to:
sudo env PATH=$PATH nethack  but was told :
env: /usr/games: Permission denied
  I am logged in as sudo  why is permission denied?
thanks

---

