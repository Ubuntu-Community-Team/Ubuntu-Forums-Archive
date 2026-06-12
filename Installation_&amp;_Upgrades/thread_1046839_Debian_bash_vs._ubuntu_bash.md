---
title: "Debian bash vs. ubuntu bash"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by SkyLeach on 2009-01-21
I ran across this issue when I inherited a number of machines from a previous system administrator, and thought I would share what I have learned.

It appears that if one (either manually or through some misconfiguration of apt) installes the debian version of BASH then one might start running into strange issues.  bash-completion conflicts with the latest couple of versions of bash from debian repositories, and for some strange (at least to me it is strange) reason .profile has been used as the local environment configuration rather than the common and popular (and default) .bashrc.

So, here is how one detects the cause of these strange shell issues, and deals with them.

First, check your installed version of BASH.  Doing what I suggest in this posting will certainly cause no harm, but it is relatively pointless unless one has the debian bash binary instead of the Ubuntu version.  (also, when I say version I say it lightly because, as I have already said, I am new to Ubuntu and as such hardly familiar with the current official package versions ;) )

dpkg -s bash
```
web /home # dpkg -s bash
Package: bash
Essential: yes
Status: install ok installed
Priority: required
Section: shells
Installed-Size: 1848
Maintainer: Matthias Klose <doko@debian.org>
Architecture: i386
Version: 3.1dfsg-8
Replaces: bash-doc (<= 2.05-1), bash-completion
Depends: base-files (>= 2.1.12), debianutils (>= 2.15)
Pre-Depends: libc6 (>= 2.3.6-6), libncurses5 (>= 5.4-5)
Suggests: bash-doc
Conflicts: bash-completion
Conffiles:
 /etc/skel/.bashrc de2b922ef0623ba36dda5fb6f7f7d9ea
 /etc/skel/.bash_profile d1a8c44e7dd1bed2f3e75d1343b6e4e1
 /etc/skel/.bash_logout 22bfb8c1dd94b5f3813a2b25da67463f
 /etc/bash.bashrc 596642d7415ff5d9f013786028a39583
 /etc/bash_completion 9da8d1c95748865d516764fb9af82af9
Description: The GNU Bourne Again SHell
 Bash is an sh-compatible command language interpreter that executes
 commands read from the standard input or from a file.  Bash also
 incorporates useful features from the Korn and C shells (ksh and csh).
 .
 Bash is ultimately intended to be a conformant implementation of the
 IEEE POSIX Shell and Tools specification (IEEE Working Group 1003.2).
 .
 Included in the bash package is the Programmable Completion Code, by
 Ian Macdonald.

```

Right, so you can test that .bashrc doesn't work by doing the following (or something equivalent):
```
[ -f ~/.bashrc ] && cp -v ~/.bashrc ~/.bashrc_bkup
echo 'echo "O-wah, Tah-Gee, KaiYam"' > ~/.bashrc
```

check your file and permissions to make sure that everything is as it should be (and would work if our bash wasn't doing .profile instead):
```

mgregory@www:~$ ls -alh ~/.bashrc
-rw-r--r-- 1 mgregory mgregory 30 2009-01-21 13:06 /home/mgregory/.bashrc
mgregory@www:~$ cat ~/.bashrc
echo "O-wah, Tah-Gee, KaiYam"
mgregory@www:~$ source ~/.bashrc
O-wah, Tah-Gee, KaiYam
mgregory@www:~$ . ~/.bashrc
O-wah, Tah-Gee, KaiYam

```

very well, so now when we ssh to or log into this machine as this user, we should see the message "O-wah, Tah-Gee, KaiYam".  Let's try it...

```

mgregory@gregory-gentoo ~/src/ttv/trunk $ ssh www
Linux web.smartbirdie.tv 2.6.20-17-server #2 SMP Wed Aug 20 16:54:26 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Wed Jan 21 20:09:59 2009 from 10.0.5.83
mgregory@web:~$ 

```

Rats!  No dice.  Now as I have already said, this is because the debian version of bash looks for a file called ~/.profile rather than the ~/.bashrc file expected by the ubuntu version of bash.  We could of course go in and rename everyone's files to .profile, and there is nothing better about the way I do it here than that, but I elected to create a symlink instead (because I run many systems and don't want to have to look for different files on different systems, plus it's less likely to come back and bite me in the bum when I'm writing expect scripts later).

So, to update everyone really quickly:

switch to the root user with one of su or sudo su and then run a quick little bash scriptlet...
```

mgregory@web ~ $ sudo su
web /home/mgregory # cd ..
web /home # for x in `find . -mindepth 1 -maxdepth 1 -type d`; do cd $x; [ -f .bashrc ] && ln -sv .bashrc .profile; cd ..; done;
create symbolic link `.profile' to `.bashrc'
create symbolic link `.profile' to `.bashrc'
create symbolic link `.profile' to `.bashrc'
create symbolic link `.profile' to `.bashrc'
create symbolic link `.profile' to `.bashrc'
create symbolic link `.profile' to `.bashrc'
create symbolic link `.profile' to `.bashrc'
create symbolic link `.profile' to `.bashrc'
web /home # exit
mgregory@web:~$ source ~/.bashrc 
-sh: `_debconf-show': not a valid identifier

```

Oh wait!  What is this _debconf-show error?  Remember what I said about bash-completion being incompatable with the debian version of bash?  Gotta make sure that inclusion of bash-completion is disabled in the .bashrc file:
```

mgregory@web ~ $ vi .bashrc
mgregory@web ~ $ diff .bashrc .bashrc_old 
118,120c118,120
< #if [ -f /etc/bash_completion ]; then
< #    . /etc/bash_completion
< #fi
---
> if [ -f /etc/bash_completion ]; then
>     . /etc/bash_completion
> fi

```

I certainly hope that this helps anyone else that is scratching their head and wondering why their .bashrc files aren't loading.

Tune in next time where I show you how to do some fancy stuff with your .bashrc and /etc/DIR_COLORS and colorful (and meaningful) system wide colors!  :D

---

### Post by SkyLeach on 2009-01-21
ah yes, nearly forgot to point out that one should also do this in the /etc/skel directory so that new users have this set by default:
```

mgregory@web /etc/skel $ sudo ln -sf .bashrc .profile
Password:
mgregory@web /etc/skel $

```

---

