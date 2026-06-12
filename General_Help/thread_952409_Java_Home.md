---
title: "Java Home"
date: 2008-10-19
forum: General Help
---

### Post by charanpreethu on 2008-10-19
hi i insatlled jdk5.and executed these commands

$cd ~/Desktop
$ export JAVA_HOME="Java home"
$ export PATH=$PATH:$JAVA_HOME/bin


now how to check wheter that java home has been created.
and what does that   PATH=$PATH:$JAVA_HOME/bin do??

---

### Post by shawnrgr on 2008-10-21
your creating system variables, this might help explain...

```
shawn@freedom:~$ export boxee=/media/boxee
shawn@freedom:~$ echo $boxee
/media/boxee
shawn@freedom:~$ cd $boxee/storage
shawn@freedom:/media/boxee/storage$ ls
mini.iso  movies  TV
shawn@freedom:/media/boxee/storage$ pwd
/media/boxee/storage
```

the $PATH var points to all your locations that contain application launchers
```
shawn@freedom:/$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

---

### Post by Nepherte on 2008-10-21
When you simply type them in a terminal, they aren't persistent. They will not work when you start a new terminal or when you reboot your computer. To make them persistent, add them to .bashrc in your home directory.

---

