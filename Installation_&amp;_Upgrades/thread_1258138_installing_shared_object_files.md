---
title: "installing shared object files"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by Clive McCarthy on 2009-09-04
I have what might be a simple problem. I'm trying to put a shared-object:
[INDENT][COLOR="DarkRed"]freeglut.so[/COLOR][/INDENT]
into \user\lib -- and my crude attempts all result in permission denied.

I'm doing this because I've installed freeglut and linked my code to the library etc. but the shared object can't be found by the executable. It seems that
[INDENT][COLOR="DarkRed"]sudo apt-get install freeglut3-dev[/COLOR][/INDENT]
doesn't put the freeglut.so in the library directory but does put freeglut.h freeglut_std.h & freeglut_ext.h headers in the \user\include directory.
It also emits a message about manual installation...

Ultimately, I will be deploying the executable and necessary libraries to a small number of Ubuntu machines on my network. These machines are embedded applications: almost no user interface, just an on/off power button and a screen. So I'll need write a bash script to do all the repetitive tasks.

For now, I'd be happy if I can figure out how to manually install the shared-object on my local system.

---

### Post by hal10000 on 2009-09-05
If you want to copy to the /usr/lib directory you have to copy it with the sudo command: [COLOR="Red"]sudo cp freeglut.so /usr/lib[/COLOR]
btw. this is a slash ( / ), not a backslash ( \ ) in the directory path.

---

### Post by Clive McCarthy on 2009-09-05
Curiously, I tried the super user route with sudo but Ubuntu still complained and denied permission. In desperation I did a chmod 777 on the lib directory, which worked -- I got a bigger hammer.:oops:

It makes me think that I'll chmod the entire disk of the 'interface-less' machines I put on my network just so that I can get at things...[-X

---

### Post by hal10000 on 2009-09-05
> It makes me think that I'll chmod the entire disk

**!!!!Don' do that!!!**, never change permissions on directories or files you didn't create yourself, unless you know exactly what you're  doing. It can mess up your whole system. And take away the 777 permission from the /usr/lib directory. It's nor a security hole, it's a security barn door.

---

### Post by hal10000 on 2009-09-05
The correct permissions for /usr/lib are drwxr-xr-x.

I'm not a programmer, so i'm sorry i can't help you too much here.

But i'm sure the gnu C-compiler has some options to find the shared ibraries you need.
It might be better to start a new thread in th programmer's corner of this forum, i guess you'll ge better help than here.

---

### Post by Clive McCarthy on 2009-09-05
Hal,
I know it freaks folks out that I'd chmod 777 the whole system but the computers are used embeded in an art works that ultimately are disconnected from the network and function as stand-alone systems.

They are temporarily slave systems that I wish to update from my main workstation as I edit my work. They do nothing but run one program and have absolutely no personal data on them. I guess they could become 'bots' but they do sit behind a network firewall and, since they have no user interface, don't ever surf the net!

It probably is possible to change the library search path environment variable to point at the directory that is exposed as a shared folder on my network.

Thanks for your advice.
Clive.

---

