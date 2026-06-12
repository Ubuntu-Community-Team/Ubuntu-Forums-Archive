---
title: "upgrade 8.10 -&gt; 9.04 broke my terminal"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by willc0de4food on 2009-04-06
so today i decided i wanted to upgrade my work computer running 8.10 to 9.04. i ran update-manager -d and let it do its thing and everything was fine and dandy. upon reboot, when trying to open gnome-terminal i got the error "There was an error creating the child process for this terminal". i tried booting a different kernel, but the error is persistent. upon trying to run xterm, nothing happens. when opening konsole, it just sits there, i never get a prompt. there's a cursor but i can't type anything. i'm running the 2.6.28-11 kernel and gnome 2.26.0
i tried reinstall the gnome-terminal package as well as libvte9 but that does nothing. the error remains. i also tried asking in the irc channel but got no response. googling didn't help either as everything that turned up either didn't apply or didn't work for fixing it. any help would be greatly appreciated..

Thanks.

---

### Post by willc0de4food on 2009-04-08
[http://www.linuxquestions.org/questions/slackware-14/cant-start-a-terminal-200544/](http://www.linuxquestions.org/questions/slackware-14/cant-start-a-terminal-200544/)

i didn't read down far enough the first time i looked over that post, but i had the devpts problem (the line was missing from my fstab).
so adding the line ```
devpts          /dev/pts        devpts          gid=5,mode=620  0       0
``` to my /etc/fstab file and doing a mount -a solved my problem.

---

### Post by scott29 on 2009-05-05
> **willc0de4food said:**
> [http://www.linuxquestions.org/questions/slackware-14/cant-start-a-terminal-200544/](http://www.linuxquestions.org/questions/slackware-14/cant-start-a-terminal-200544/)

i didn't read down far enough the first time i looked over that post, but i had the devpts problem (the line was missing from my fstab).
so adding the line ```
devpts          /dev/pts        devpts          gid=5,mode=620  0       0
``` to my /etc/fstab file and doing a mount -a solved my problem.


This fixes the issue, but you have to do a mount -a after each reboot.  Is there a more "permanent" fix to this problem, or is an update in the works to fix this?

---

### Post by gpmiii on 2009-05-05
Ok - so I have the same problem.  I opened the file, added the line, but when trying to save, it states I don't have admin privileges to save.

---

### Post by parktownprawn on 2009-05-06
> **gpmiii said:**
> Ok - so I have the same problem.  I opened the file, added the line, but when trying to save, it states I don't have admin privileges to save.

try editing with admin privileges
 ```
gksudo gedit /etc/fstab
```

---

### Post by scott29 on 2009-05-06
Is there any way to fix the Terminal issue in 9.04 that doesn't require a mount -a after each reboot?

I have had nothing but issues after upgrading, and I'm restarting frequently.  Having to do a mount -a at every startup is a pain.

Thanks.

---

### Post by arnold.pietersen on 2009-05-06
> **parktownprawn said:**
> try editing with admin privileges
 ```
gksudo gedit /etc/fstab
```

Just checking.  How do you edit with admin privileges if you are not able to start the terminal to type the above command?

Thanks

---

### Post by parktownprawn on 2009-05-08
> **arnold.pietersen said:**
> Just checking.  How do you edit with admin privileges if you are not able to start the terminal to type the above command?

Thanks

press alt+F2 and then type in the command

---

### Post by scott29 on 2009-05-08
Does anybody know when this is going to be fixed?  This issue is a complete pain...

---

### Post by willc0de4food on 2009-05-10
i agree, it is a pain.
having to do the mount command is annoying, but thats the only thing i know of to fix this problem :/
if anyone has any more suggestions they would be appreciated..

---

### Post by Hatuey on 2009-05-19
Hello,

I had the same problem and I solved doing:

chkconfig mountdevsubfs.sh 1

in the /etc/init.d folder under root

From: [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/360160]("https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/360160")

Good luck,

[]s,

Hatuey

---

### Post by v1nsai on 2009-05-20
You can specify the system to run a command every startup by going to System->Preferences->Startup Applications (used to be Sessions) and adding a new command.  You can just type in the command to be run at startup by typing 'sudo mount -a' in there, giving it a name, and clicking the checkbox next to it to make it run.

However, I solved by using a different solution in the bug report that someone linked earlier.  It was recommended for people who have modified mountdevsubfs.sh (virtualbox was mentioned as a reason, thats why I tried this first).  Just run

```
# sudo cp /etc/init.d/mountdevsubfs.sh.dpkg-dist /etc/init.d/mountdevsubfs.sh
```

Reboot, and all was well for me.

There are a few different fixes mentioned in the bug report, I recommend reading it to find what specific holdup you may be experiencing.

---

### Post by jacontrerasv on 2009-11-03
Hi, I think this is my really first post to try to help, I'm new but I been reading and searching a lot. I was having problems whit VLC after upgrade to 9.10 and after fixing the VLC issue i got the infamous 
*** VTE ***: Failed to load terminal capabilities from '/etc/termcap'

What I did to solve this was:
 Reinstall:
libvte9 and the libvte-common as well as the gnome-terminal 
From:
System> Administration> Synaptic Package Manager

That fix my issue hope this helps.

*Linux converted* ;)

---

### Post by treaki on 2010-10-26
thanks from me to!! i had the same problem after my harddisk get manny bad blocks

[SIZE=7]THX!!![/SIZE]

---

