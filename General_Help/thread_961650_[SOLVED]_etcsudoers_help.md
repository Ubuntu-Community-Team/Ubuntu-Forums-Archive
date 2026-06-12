---
title: "[SOLVED] /etc/sudoers help"
date: 2008-10-28
forum: General Help
---

### Post by CharlieNixon on 2008-10-28
I'd like to setup a particular user with the ability to run all the scripts in a particular directory (which require sudo) without being prompted for their password. To test this I first attempted to setup this user to be able to run ANY sudo command without being prompted. Here's what I did:

sudo visudo -f /etc/sudoers

then, under the below comment, I added this line

# User privilege specification
<user>  localhost = NOPASSWD: ALL

(where <user> is my username)

I saved the file, but it didn't seem to work. I rebooted and tried again. Same result. Interestingly the file contains the following line as well:

# Uncomment to allow members of group sudo to not need a password
%sudo ALL=NOPASSWD: ALL

As you can see I uncommented the line. Then added the user account to the sudo group. But still no dice. 

Any ideas?

---

### Post by bodhi.zazen on 2008-10-28
See this link, examples at bottom :)

[http://linux.die.net/man/5/sudoers](http://linux.die.net/man/5/sudoers)

---

### Post by CharlieNixon on 2008-10-28
Thanks. Those examples helped. It seems my problem was the spaces. I used 

user  ALL = NOPASSWD: ALL

and that worked!

---

