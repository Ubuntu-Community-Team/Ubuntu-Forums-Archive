---
title: "Need help with the Alias command"
date: 2008-11-24
forum: General Help
---

### Post by ajmannen on 2008-11-24
Hello! I found about a command called Alias, but it said that I have to go into .bashrc so I did (/usr/share/doc/adduser/examples/adduser.local.conf.examples/skel/dot.bash_profile) Now I am in there ..but really, I'm kinda new to terminal. In .bashrc was it written 

"# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package."

So to the question, ~/.bash_aliases is empty, how do I put aliases into it, how do I write them inn, and after writing them inn there will they remain?

---

### Post by philinux on 2008-11-24
The file in question is ~/.bashrc

example


#```
 enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
   ** alias aptupdate='sudo apt-get update && sudo apt-get upgrade'**
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

```

---

### Post by ajmannen on 2008-11-24
So what you are telling me is just to add aliases to that file and not a seperate file as recomended in the text. Like
    alias gief='sudo aptitude' and does the && mean that it will perform one more command?

---

### Post by whitethorn on 2008-11-24
Hi,

Usually you edit the .bashrc have in you home directory.  Usually every user has their own bashrc.  

~/.bashrc = /home/"username"/.bashrc  (username is the name of your user)  an alias is a shortcut for certain command/commands as in the example a couple posts above. 

```
command1 && command2
```  

the && means finish the first command and then do the second command. 

In your home folder you have certain files that have a . in front of them which means they are hidden folders/files.  You can see them with (from terminal) with

```
ls -a 
```

Or from nautilus by navigating to your home folder and pressing crtl + h

:)

---

### Post by philinux on 2008-11-24
> **ajmannen said:**
> So what you are telling me is just to add aliases to that file and not a seperate file as recomended in the text. Like
    alias gief='sudo aptitude' and does the && mean that it will perform one more command?

Yes.
Yes.:)

---

