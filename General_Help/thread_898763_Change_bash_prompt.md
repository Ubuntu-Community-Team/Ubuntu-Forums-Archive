---
title: "Change bash prompt"
date: 2008-08-23
forum: General Help
---

### Post by im_an_alien on 2008-08-23
I already changed my bash prompt in .bashrc, but aparantly that's only "executed by bash(1) for non-login shells."  So when I log in, I get my old (default) prompt.  To get mine, I have to run bash again.  What do I need to change to make it the new one on login? 90% of my logins are through ssh, so it gets rather annoying...

---

### Post by LateNiteTV on 2008-08-23
```
export PS1="ps1options"
```
then logout and back in.
this will put in your .profile or your .bash_profile.

---

### Post by im_an_alien on 2008-08-23
Thanks, that worked, sort of.  It fixed it:
```
phider@jupiter:~$ export PS1="[${debian_chroot:+($debian_chroot)}\u@\h]\$"
[phider@jupiter]$
```
But when I log back in, I get
```
phider@jupiter:~$
```
again.

Also, the colors (eg. in ls w/ blue for directories/green for exe's) don't show up when I log in.  After I run bash again, and .bashrc is exec'd, the colors come back.

---

### Post by LateNiteTV on 2008-08-23
do u have a .profile or a .bash_profile in your home dir?

if so, post the contents of it along with the contents of .bashrc

---

### Post by im_an_alien on 2008-08-23
```
ls: cannot access .profile: No such file or directory
ls: cannot access .bash_profile: No such file or directory
```

[.bashrc](http://phider.us.to/bashrc)

---

### Post by LateNiteTV on 2008-08-23
try this:
```
touch .bash_profile
```
then edit it and put your PS1 in there.

---

### Post by im_an_alien on 2008-08-23
That worked, but I still don't have color until I run bash.

---

### Post by LateNiteTV on 2008-08-23
i dont know what to tell u about the color... ive never even tried using color codes.

---

### Post by nitro_n2o on 2008-08-23
This document will tell you a lot about how to customize bash prompts and have nice color prompts with many examples [http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)

make sure that you shell is set to bash not sh 
echo $SHELL 
should say /bin/bash 

if not, then do 
sudo chsh /bin/bash 

this will give you a permanent bash shell. 

good luck

---

### Post by im_an_alien on 2008-08-23
I already have the colors, like this:

[phider@jupiter]$ ls -l
total 52
-rw-r--r-- 1 root root 10614 2008-07-29 11:04 apache2.conf
drwxr-xr-x 2 root root  4096 2008-06-28 22:08 [COLOR="Blue"]conf.d[/COLOR]
-rw-r--r-- 1 root root   378 2008-05-29 04:38 envvars
-rw-r--r-- 1 root root    33 2008-07-10 16:26 httpd.conf
drwxr-xr-x 2 root root 12288 2008-07-24 18:18 [COLOR="Blue"]mods-available[/COLOR]
drwxr-xr-x 2 root root  4096 2008-06-07 17:01 [COLOR="Blue"]mods-enabled[/COLOR]
-rw-r--r-- 1 root root    59 2008-02-04 15:26 ports.conf
drwxr-xr-x 2 root root  4096 2008-08-09 19:32 [COLOR="Blue"]sites-available[/COLOR]
drwxr-xr-x 2 root root  4096 2008-08-09 19:32 [COLOR="Blue"]sites-enabled[/COLOR]

But it only works if I'm using a non-login shell.  If I'm using the login shell, I don't get colors.  This would lead me to believe it's something in my .bashrc that's making the colors come up?

---

### Post by xarquid on 2008-08-23
In a terminal type this:

[COLOR="DarkRed"]echo $TERM[/COLOR]

The result will be what type of terminal window you are in.

I think this is your problem, if it is not something else of note above (such as editing colors, etc.).

When editing your .bashrc file notice the line(s):
# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
[COLOR="DarkRed"]    xterm-color) color_prompt=yes;;[/COLOR]

If you terminal is for example "xterm"

Which your .bashrc does not have by default (and thus your xterm does not have a colorful [COLOR="DarkRed"]user[/COLOR][COLOR="DarkGreen"]@[/COLOR][COLOR="DarkRed"]host[/COLOR])

So you will need to add the line:
[COLOR="DarkRed"]    xterm) color_prompt=yes;;[/COLOR]

Be careful to notice exact sytax of those lines including the ) = ;;

Bam. Colorful [COLOR="DarkRed"]user[/COLOR][COLOR="DarkGreen"]@[/COLOR][COLOR="DarkRed"]host[/COLOR]

Same concept for if the command in the said terminal:
echo $TERM yield "coolterm"
[COLOR="DarkRed"]    coolterm) color_prompt=yes;;[/COLOR]

This may fix your issue. But maybe I just have wishful thinking...

Good luck.

Sincerely,

Craig Huffstetler

---

