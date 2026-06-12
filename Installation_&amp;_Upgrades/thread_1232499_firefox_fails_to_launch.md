---
title: "firefox fails to launch"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by gregh7470 on 2009-08-05
Earlier this morning I received an update notification and upon launching the update manager there was a couple of updates for firefox:
firefox-3.0 and firefox-3.0-branding
I didn't really think anyhting about it, approved the updates and now firefox will not launch. I tried launching it from a terminal and got an error message dealing with the xul library...I can't really remember what the error was, and so trying to fix the error myself (big mistake) I used synaptic to install xulrunner-1.9.1...which did not help and infact made matters worse.  I tried to purge the xul library and get this:

```
gregh7470@computer007:~$ sudo apt-get purge xulrunner-1.9.1
[sudo] password for gregh7470: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xulrunner-1.9.1*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 24.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 132176 files and directories currently installed.)
Removing xulrunner-1.9.1 ...
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/xulrunner for update_mode ()
dpkg: error processing xulrunner-1.9.1 (--purge):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 xulrunner-1.9.1
E: Sub-process /usr/bin/dpkg returned an error code (1)

```and when I try and launch firefox from the terminal I get this:

```
gregh7470@computer007:~$ firefox
Could not find compatible GRE between version 1.9.0.1 and 1.9.0.*.
gregh7470@computer007:~$ 
```I'm stuck...I want firefox back and working and the extra library that's stuck needs to come out as well.  I'm using Galeon 2.0.6 right now and it seems to be working ok.
I am using a standard install of ubuntu.  I have not enabled any extra repositories or installed any outside packages.  I just installed it and updated it and added some extra packages that were available in the repositories like some plugins for pidgin, like liferea, vlc...nothing fancy so to speak....
Any help would be greatly appreciated
Thanks

---

### Post by bruzzel on 2009-08-05
Have a look at:
[http://blog.mymediasystem.net/uncategorized/solved-firefox-could-not-find-compatible-gre-after-ubuntu-810-upgrade/](http://blog.mymediasystem.net/uncategorized/solved-firefox-could-not-find-compatible-gre-after-ubuntu-810-upgrade/)

---

### Post by gregh7470 on 2009-08-05
That worked!! I have Firefox back, but when I try to remove Galeon I'm getting this error:

E: xulrunner-1.9: subprocess post-installation script returned error exit status 2
E: xulrunner-1.9.1: subprocess post-installation script returned error exit status 2


It appears as a pop-up in synaptic after I removed Galeon...when I closed the pop-up the console in synaptic showed still showed errors concerning both xulrunner-1.9 and xulrunner-1.9.1...
It seems I am a victim of this particular bug:

[https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/370093](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/370093)

---

### Post by gregh7470 on 2009-08-05
Problem resolved:
bruzell's solution to get firefox back up and running worked:

> bruzzel              **Re: firefox fails to launch**
         Have a look at:
[http://blog.mymediasystem.net/uncate...u-810-upgrade/]("http://blog.mymediasystem.net/uncategorized/solved-firefox-could-not-find-compatible-gre-after-ubuntu-810-upgrade/")The problem/fix was, in a nutshell:

> Could not find compatible GRE between version 1.9.0.1 and 1.9.0.*.
 The solution for the problem was quite simple. This line made Firefox work again:[INDENT]sudo xulrunner-1.9 --register-global
[/INDENT]However there was another problem I had to deal with:
[https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/370093](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/370093)
as the xulrunner 1.9.1 library was somewhat stuck and would give me errors anytime I used apt-get or synaptic...the fix was somewhat tedious but worked:

> For me removing the file (/var/lib/dpkg/alternatives/xulrunner) was what I finally needed to do to complete the install, so to summarize:

Delete the files listed here: [http://packages.ubuntu.com/jaunty/i386/xulrunner-1.9/filelist](http://packages.ubuntu.com/jaunty/i386/xulrunner-1.9/filelist)
Delete /var/lib/dpkg/alternatives/xulrunner
resinstall manually by downloading xulrunner from: [http://packages.ubuntu.com/jaunty/i386/xulrunner-1.9/download](http://packages.ubuntu.com/jaunty/i386/xulrunner-1.9/download)after following these instructions and then testing by installing a documentation package with synaptic - no more errors  :D

Thank You bruzzel for your help

attn: admin   
please mark thread as solved
ty

---

