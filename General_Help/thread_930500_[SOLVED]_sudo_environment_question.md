---
title: "[SOLVED] sudo environment question"
date: 2008-09-26
forum: General Help
---

### Post by TheR on 2008-09-26
I have set LD_LIBRARY_PATH="/usr/lib/oracle_client_10_2" in /etc/environment. Which works fine when I work as normal user.

But when I have to compile a program (as sudo) LD_LIBRARY_PATH is not set. Confirmed with "sudo printenv"

When I try to export variable:
~$ sudo export LD_LIBRARY_PATH=/usr/lib/oracle_client_10_2

I get this message.
sudo: export: command not found

Needless to say that exporting variable as normal user variable is not seen in sudo environment.

And here is where my knowledge is at the end.

Where can I set environment variable so it would be visible to sudo user?


by
TheR

---

### Post by siddhartha_at on 2008-09-26
I don't know if it helps but just set your global environment variables in f.e /etc/bash.bashrc

---

### Post by Nepherte on 2008-09-26
I believe using sudo -E should work. You don't have to sudo export anymore. It will use the environment variables from the user.

---

### Post by mxrten on 2008-09-26
I also had problems with environment variables disappearing when sudo'ing. I still don't know where to change this behaviour (tell me if you know), but this is what I did:

sudo env [environment variable]=$[environment variable] *command*

For example in my case:

sudo env PATH=$PATH *command*


If you use this often you can put the line:
alias sudo='sudo env [environment variable]=$[environment variable]'
in your ~/.profile, and you can use sudo just as before (sudo *command*)

---

### Post by TheR on 2008-09-26
This worked. 
> 
sudo env [environment variable]=$[environment variable] 


This doesn't work.
> 
I don't know if it helps but just set your global environment variables in f.e /etc/bash.bashrc


This doesn't work.
> 
sudo -E



by
TheR

---

