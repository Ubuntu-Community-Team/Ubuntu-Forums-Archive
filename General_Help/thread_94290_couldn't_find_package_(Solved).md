---
title: "couldn't find package (Solved)"
date: 2005-11-23
forum: General Help
---

### Post by kmorsch on 2005-11-23
I just installed ubuntu. I have never used Linux before so this is the first time. When I try to install any package it says: couldn't find package

this  happens for everything. why won't it work? i'm trying to get flash and so on...

---

### Post by SavageBeginner on 2005-11-23
Please post the contents of /etc/apt/sources.list

---

### Post by kmorsch on 2005-11-23
E325: ATTENTION
Found a swap file by the name "/etc/apt/.sources.list.swp"
          owned by: root   dated: Wed Nov 23 14:43:06 2005
         file name: /etc/apt/sources.list
          modified: YES
         user name: root   host name: c-24-21-212-155buffygear
        process ID: 8208
While opening file "/etc/apt/sources.list"
             dated: Mon Nov 21 14:05:28 2005

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/apt/sources.list"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/apt/.sources.list.swp"
    to avoid this message.

Swap file "/etc/apt/.sources.list.swp" already exists!
[O]pen Read-Only, (E)dit anyway, (R)ecover, (Q)uit, (A)bort, (D)elete it:


it won't even show that...i dont know what is going on

---

### Post by aysiu on 2005-11-23
What's /etc/apt/.sources.list.swp?

You're looking for Flash? This is what you should do:

1. Follow the instructions in the first link in my signature **exactly**. Do not deviate from the instructions. Copy and paste if you don't trust the accuracy of your own typing.

2. Once you've finished that, type this in a terminal ```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by SilentCacophony on 2005-11-23
Sounds as if another application, perhaps an instance of vim, has crashed while editing or having a lock on your sources.list file. You'll find that you cannot install or update packages while another app has access to that file, if that's the case.

Being unsure as to what the application might be, you could run 'top' in a terminal to see if you can spot the offender and kill it (probably not.)

If the instructions in the message that you posted above don't help you, perhaps logging out of gnome, then back in, might clear the errant application.

Note the last line in **(2)** of the message that you posted above, if the problem persists. If need be you can delete the .swp file with:

```
sudo rm /etc/apt/.sources.list.swp
```

Make sure to heed **aysiu's** advice, as your sources.list may now be corrupt. There is a complete sources.list on the page linked to there.

---

### Post by kmorsch on 2005-11-24
[QUOTE=aysiu]What's /etc/apt/.sources.list.swp?

You're looking for Flash? This is what you should do:

1. Follow the instructions in the first link in my signature **exactly**. Do not deviate from the instructions. Copy and paste if you don't trust the accuracy of your own typing.

2. Once you've finished that, type this in a terminal ```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```[/QUOTE]
It seemed to work and then at the end of the "install" i got this message
Setting up ruby1.8 (1.8.2-9~hoary1) ...
Setting up ruby (1.8.2-1~hoary1) ...
Setting up libruby (1.8.2-1~hoary1) ...
Setting up flashplugin-nonfree (7.0.25-5) ...
Checking new upstream release...
I: checking [http://macromedia.rediris.es/tarball/debian/](http://macromedia.rediris.es/tarball/debian/)...
No new version is detected. ( = not installed)

---

### Post by kmorsch on 2005-11-24
actually i figured it out. thanks a bunch guys :D

---

### Post by aysiu on 2005-11-24
Does it work, though?
Open up Firefox or Epiphany (or whatever browser you use) and go to a site that has Flash on it.

---

### Post by kmorsch on 2005-11-25
Yes, the flash works. However, I still can't get Java to install and I'd like to have Limewire or some other p2p client and it requires Java. Most programs seem to install now, but Java is still having a hard time.

root@c-24-21-212-155buffygear:/home/kimberly # sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
root@c-24-21-212-155buffygear:/home/kimberly # java -version

---

### Post by dubz on 2005-11-25
[QUOTE=SilentCacophony]Sounds as if another application, perhaps an instance of vim, has crashed while editing or having a lock on your sources.list file. You'll find that you cannot install or update packages while another app has access to that file, if that's the case.

Being unsure as to what the application might be, you could run 'top' in a terminal to see if you can spot the offender and kill it (probably not.)

If the instructions in the message that you posted above don't help you, perhaps logging out of gnome, then back in, might clear the errant application.

Note the last line in **(2)** of the message that you posted above, if the problem persists. If need be you can delete the .swp file with:

```
sudo rm /etc/apt/.sources.list.swp
```

Make sure to heed **aysiu's** advice, as your sources.list may now be corrupt. There is a complete sources.list on the page linked to there.[/QUOTE]

Whats happened is that he has opened up 2 instances of thesame file at the same time.It hapens to me often in vi.

---

