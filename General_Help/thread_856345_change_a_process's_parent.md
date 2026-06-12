---
title: "change a process's parent"
date: 2008-07-11
forum: General Help
---

### Post by rmccabe3701 on 2008-07-11
Hello,
I was wondering if there is any way to change a process's parent.  For example, if I am ssh-ed into my home computer and there is a process running on another terminal, is is possible to change the process parent to the ssh shell and then use something like the fg command? 
Thanks in advance.

---

### Post by MasterXandrex on 2008-07-11
I do not believe that this is possible. the PPID is set when the process is spawned. Are you trying to bring a process in another session to your session?


Xan

---

### Post by hal8000 on 2008-07-11
You can probably changing it by killing the process first and then starting it again. AFAIK PID's are allocated by the linux kernel, so you have no control on assigning the process id.

ps -aux

will list all processes
pidof  bash
will list process id of bash

so you could find your pid, kill it then restart it.

---

### Post by MasterXandrex on 2008-07-11
Also if you are trying to run something and not have to stay connected try nohup

like this:
```

nohup yes > output.txt 2>&1 &

```
This nohup to run a command and then log the output in output.txt the 2>&1 redirects error codes to that file and the final & leaves it in the background. You would replace yes with your command. This won't work for anything requiring input (without modification).


Xan

---

### Post by rmccabe3701 on 2008-07-11
Well I thought that if you kill a parent all of its children are inhereted by the parent's parent.  So I figured that this type of inheretance could take place without killing the parent.  
UbuntuUser3859:  
I am sitting at work right now ssh-ed into my computer.  I have firefox running on my ubuntu machine at home with a lot of tabs open.  
```

rob@rob-desktop:~ $ ps -Aef | grep firefox
rob      20557     1  3 Jul02 ?        06:29:40 /usr/lib/firefox-3.0/firefox 

```
I would like to get this process (20557) to be owned by my ssh shell and use X forwarding to view the firefox application.  If this is not possible, it is no big deal -- I was just interested. Thanks.

---

### Post by MasterXandrex on 2008-07-11
Well, I know a way to do that, but you won't get the tabs to come over. You can start an additional FF session by running firefox --no-remote. Though, it's usually slow over SSH.

But I really don't think you can change the PPID like that.

Xan

---

### Post by sibidiba on 2008-08-29
$ man setsid

(...)
setsid - run a program in a new session
(...)

---

### Post by inteluser on 2008-08-29
Moving X programs is tricky.  See [http://fixunix.com/xwindows/91803-xmove-ssh.html](http://fixunix.com/xwindows/91803-xmove-ssh.html) for some initial help.  
I don't see any reason why the parent process matters.  I can do 'xlogo --display=some:other.display' and the xlogo's pid will by my shell, not whatever owns some:other.display

---

