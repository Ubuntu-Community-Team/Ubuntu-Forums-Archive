---
title: "Unable to create folder - problem with rights"
date: 2008-07-29
forum: General Help
---

### Post by BenFischer on 2008-07-29
For some reason I am unable to create folders anywhere in my file system except my home folder, I don't know whats wrong.  Any ideas?

---

### Post by rbc on 2008-07-29
That is how Ubuntu is set up. By default, you only have rights to add/edit your home directory, although there are ways around it. What are trying to accomplish that you need to create a directory outside your home directory?

---

### Post by northern lights on 2008-07-29
You'd have to be root to alter/create files and/or directories anywhere in the file system other than your /home.

That usually is not necessary anyways, though.

It's not meant to be an annoyance but rather one of the features that make Linux so much more secure than windows. In this case it's protecting sensible data mostly from the user (you & me) himself.

It might be a bit of a nuisance at first, since, if you switched from WIndows, you're used to being administrator all the time. But that's exactly why you can break things so easily if your OS is from Redmond.

---

### Post by hyper_ch on 2008-07-29
there is very little reason normally to create files/folders outside your home. What are you trying to accomplish?

---

### Post by dexter.deepak on 2008-07-29
this is possible only if you are in the sudoers list ...that is you can use 'sudo'
try :
```
sudo nautilus
```
if you know the password, you are through:)

---

### Post by northern lights on 2008-07-29
> **dexter.deepak said:**
> this is possible only if you are in the sudoers list ...that is you can use 'sudo'
try :
```
sudo nautilus
```
if you know the password, you are through:)
Please, _never_ open a graphical application with 'sudo'. If you must open a graphical application as root, use```
gksu GRAPHICAL APP
```  Refer to [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo") for references.

---

### Post by ilrudie on 2008-07-29
> **dexter.deepak said:**
> this is possible only if you are in the sudoers list ...that is you can use 'sudo'
try :
```
sudo nautilus
```if you know the password, you are through:)
Don't do this.  sudo is for command line programs.  gksudo is for gui programs.  the correct command is ```
gksudo nautilus
```

---

### Post by dexter.deepak on 2008-07-29
i have often read about gksu / gksudo  , i have used them both too. but i never found any advantage of gksu/gksudo over sudo ....can you clearify why i should avoid sudo for gui ??

---

### Post by ilrudie on 2008-07-29
> **dexter.deepak said:**
> i have often read about gksu / gksudo  , i have used them both too. but i never found any advantage of gksu/gksudo over sudo ....can you clearify why i should avoid sudo for gui ??
sudoing gui applications can break things.  gksudo is designed for this and is safe.

more info here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by BenFischer on 2008-07-29
Thanks to everyone for being so willing to help me out,  The reason I wanted to create a folder was because I was directed to [http://ubuntuforums.org/showthread.php?p=2384334&mode=linear#post2384334](http://ubuntuforums.org/showthread.php?p=2384334&mode=linear#post2384334) this thread by someone trying to help me fix a problem with a wireless 2Wire internet connection. Supposedly adding a etc/homename file will allow me to run a program that converts the windows driver into one compatible with Ubuntu.  Would you people recommend that I try creating this file in a root account?

[http://ubuntuforums.org/showthread.php?t=856581&page=2](http://ubuntuforums.org/showthread.php?t=856581&page=2) That is the original thread explaining what to do about 2Wire, just incase anyone knows an easier solution then the one provided there.

---

### Post by northern lights on 2008-07-29
> **dexter.deepak said:**
> i have often read about gksu / gksudo  , i have used them both too. but i never found any advantage of gksu/gksudo over sudo ....can you clearify why i should avoid sudo for gui ??
sudo' allows a normal user to gain root privileges to do administrative tasks. That's perfectly sufficient if you want to run a shell command that does not have a GUI. If however, you launch a graphical application with 'sudo' The application is launched with root rights but the user's preferences. Launching it with 'gksu' gives you the superuser's preferences also.

Launching graphical apps with 'sudo' may result in a mixup of rights and permissions which is not fun to fix


> **BenFischer said:**
> Thanks to everyone for being so willing to help me out,  The reason I wanted to create a folder was because I was directed to [http://ubuntuforums.org/showthread.php?p=2384334&mode=linear#post2384334](http://ubuntuforums.org/showthread.php?p=2384334&mode=linear#post2384334) this thread by someone trying to help me fix a problem with a wireless 2Wire internet connection. Supposedly adding a etc/homename file will allow me to run a program that converts the windows driver into one compatible with Ubuntu.  Would you people recommend that I try creating this file in a root account?

[http://ubuntuforums.org/showthread.php?t=856581&page=2](http://ubuntuforums.org/showthread.php?t=856581&page=2) That is the original thread explaining what to do about 2Wire, just incase anyone knows an easier solution then the one provided there.
To be fairly honest, I'm too tired (quarter after midnight here) to read both threads completely. One word of caution though: The first thread is from May 2007 and Feisty related. Often suggestions / practices from earlier releases work, but issues might also have drastically changed over a year. Linux is dynamic unlike certain other systems from Redmond, that are (nearly) as error prone three years post-release and that never get updated...

> **BenFischer said:**
> Would you people recommend that I try creating this file in a root account?You'd be crating a file _as_ root _in_ the same filesystem you normally see but don't have permission to alter.

---

