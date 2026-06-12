---
title: "[SOLVED] No such file or directory problem"
date: 2008-10-10
forum: General Help
---

### Post by victor.zamanian on 2008-10-10
Hello!

I had emacs-nox installed by aptitude but decided to download the source tarball containing the latest version and install that instead. I removed emacs-nox using aptitude as usual, but now that I've installed the new emacs, I get an error when I try to run it in the terminal:
```
$ emacs
bash: /usr/bin/emacs: No such file or directory
```
I'm very frustrated because /usr/bin/ isn't where I've installed it; the new installation is at /usr/local/bin/!

It seems that bash is holding some old reference to the old installation. If it had no idea of what I was talking about, it would say:
```
$ emacs-nox
bash: emacs-nox: command not found
```
or perhaps
```
$ linuxdcpp
The program 'linuxdcpp' is currently not installed.  You can install it by typing:
sudo apt-get install linuxdcpp
```
I have now deleted all files I could find with the word "emacs" in them, and run a
```
sudo find / -name "*emacs*" | grep -v <myusername>
```
to see if there are any such files on the disk left (except for the source code in my home dir of course) and the command shows no output, as does
```
sudo updatedb && locate emacs | grep -v <myusername>
```
1. What could possibly be the issue here? o_o 

2. And how would I, after aptitude remove-ing a program, get that message back as I get when I try to run linuxdcpp, instead of getting the message I get when running emacs-nox?

Thanks for any help!

---

### Post by Titan8990 on 2008-10-10
When you removed Emacs with aptitude did you remember to purge the configuration files?


sudo apt-get remove --purge emacs

---

### Post by joe92865 on 2008-10-10
On the command line type echo $PATH to make sure /usr/local/bin is in your path.

If it isn't, you can add it to your .bashrc file with
"PATH=$PATH=":/usr/local/bin"

---

### Post by Titan8990 on 2008-10-10
The problem is not that /usr/local/bin is not in his $PATH it is the fact that it is specifically looking in /usr/bin which indicates that there is some type of configuration that has been left behind.


You might try making a symbolic link from /usr/local/bin/emacs to /usr/bin.

---

### Post by geirha on 2008-10-10
> **victor.zamanian said:**
> 
```
$ emacs
bash: /usr/bin/emacs: No such file or directory
```


Since bash is telling you it can't find emacs at that specific path, it sounds like you have an alias for emacs. Type **alias** in a terminal. If it lists emacs as an alias, type **unalias emacs**. It is probably being set in your ~/.bashrc or ~/.bash_profile.
```
grep alias ~/.bashrc ~/.bash_profile
```

---

### Post by victor.zamanian on 2008-10-10
Titan8990: Yes, I purged as well. I forgot to mention that.

joe92865: /usr/local/bin is in my path. I know this since I have other software I use in there (git), but I also double-checked to be sure. PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
Also, I wouldn't rather put a symbolic link in /usr/bin than find the solution for this if you know what I mean. =/

geirha:
```
$ alias
alias ls='ls --color=auto'
```
```
$ grep alias ~/.bashrc ~/.bash_profile ~/.bash_aliases
/home/victor/.bashrc:# ~/.bash_aliases, instead of adding them here directly.
/home/victor/.bashrc:#if [ -f ~/.bash_aliases ]; then
/home/victor/.bashrc:#    . ~/.bash_aliases
/home/victor/.bashrc:# enable color support of ls and also add handy aliases
/home/victor/.bashrc:    alias ls='ls --color=auto'
/home/victor/.bashrc:    #alias dir='ls --color=auto --format=vertical'
/home/victor/.bashrc:    #alias vdir='ls --color=auto --format=long'
/home/victor/.bashrc:    #alias grep='grep --color=auto'
/home/victor/.bashrc:    #alias fgrep='fgrep --color=auto'
/home/victor/.bashrc:    #alias egrep='egrep --color=auto'
/home/victor/.bashrc:# some more ls aliases
/home/victor/.bashrc:#alias ll='ls -l'
/home/victor/.bashrc:#alias la='ls -A'
/home/victor/.bashrc:#alias l='ls -CF'
grep: /home/victor/.bash_profile: No such file or directory
grep: /home/victor/.bash_aliases: No such file or directory
```
I don't see anything emacs-related in there. :-/
Also,
```
$ unalias emacs
bash: unalias: emacs: not found
$ emacs
bash: /usr/bin/emacs: No such file or directory
```
Still nothin'.

Keep at it boys! I know we can crack this one! By the way, any ideas about the second question? Just as a side quest though, question 1 has highest priority! :D

---

### Post by geirha on 2008-10-10
bash does make a hash table of where executables are located. I'm not sure when it recreates the hash-table, but you can disable it in the current shell by running ```
set +h
``` Try that, and run emacs again.

---

### Post by victor.zamanian on 2008-10-10
geirha:
Thanks for your post (and thank you to all of you). I'm glad to say this issue was resolved quite quickly. I reckon you (geirha) were closest. :-) Solution? Bash apparently held a reference to the old emacs within the current session or something. I'm recompiling emacs (because I'm getting some errors or whatever, not relevant here anyway), and so I opened a new terminal window and got:
```
$ emacs
The program 'emacs' can be found in the following packages:
 * emacs21-nox
 * emacs22
 * emacs-snapshot-nox
 * e3
 * emacs-snapshot
 * emacs22-gtk
 * emacs21
 * emacs22-nox
 * jove
Try: sudo apt-get install <selected package>
```
However, I don't get any suggestions when I type in "emacs-nox" because I already had that package and then purged/removed it (at least I think this is why). I even ran aptitude clean and autoclean. But that issue is... less important I guess. Feel free to holler if you know a solution to it though!

Long story short:
Issue 1 RESOLVED.
Issue 2 remains.

---

### Post by geirha on 2008-10-10
I get the same.
```
$ emacs-nox
bash: emacs-nox: command not found

```

The databases that the command-not-found script (see [https://wiki.ubuntu.com/CommandNotFoundMagic](https://wiki.ubuntu.com/CommandNotFoundMagic)) uses, simply doesn't have an entry for emacs-nox, it has for emacs though.

---

### Post by victor.zamanian on 2008-10-10
geirha: Oh alright. :-) Another thanks to all of you, and especially gerha.

Both issues resolved. Marking thread as solved!

---

