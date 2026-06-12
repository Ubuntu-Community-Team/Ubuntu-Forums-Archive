---
title: "visudo + /etc/init.d/fail2ban status"
date: 2008-08-07
forum: General Help
---

### Post by jolly79 on 2008-08-07
Hi guys

I want to use this command /etc/init.d/fail2ban status in my conky, so i can se the status there.

I have triede visudo, but cant get it to work, do enybody know what i should write i sudo visudo??

Hope somebody can help me, this is driveing me crazy!

Cheers

-Gustav

---

### Post by DagMan on 2008-08-07
make it easy on yourself if you want an easier editor
```
sudo -i
EDITOR=nano visudo
```


and as for what to add
```
%admin  ALL=NOPASSWD: /etc/init.d/fail2ban
```
for people in the admin group 
or 
```
ALL  ALL=NOPASSWD: /etc/init.d/fail2ban
```
for everyone
but you still have to call it with sudo like this, you just wont have to provide a password, so have conky call it with sudo still.

---

### Post by jolly79 on 2008-08-07
Hi...

It´s still not vorking:

Here is my visudo, dosent it look right??

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_keep = "EDITOR VISUAL"
Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
%admin  ALL=NOPASSWD: /etc/init.d/fail2ban
ALL  ALL=NOPASSWD: /etc/init.d/fail2ban

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by jolly79 on 2008-08-07
Enybody know why visudo dsent work for me??

---

### Post by mdsharp24 on 2008-08-07
Remove everything you have added and add this example at the VERY BOTTOM, as in the last line of /etc/sudoers:

ray    rushmore = NOPASSWD: /bin/kill, /bin/ls, /usr/bin/lprm

This allows the username ray, on the host rushmore, to execute kill, ls, and lprm with NO PASSWORD.

Substitute ray, rushmore, and the commands you want as needed.

---

### Post by bodhi.zazen on 2008-08-07
syntax is very obscure but critical in sudoers (visudo).

You have groups under user specification. Move it to the groups section.

Also, in the event of multiple rules, in the event of any conflict, first one applies (not last).

---

### Post by jolly79 on 2008-08-07
Guys none of this is working for me..

Cant some one spoon feed this to me..

I need to be able to run eighter conky or /etc/init.d/fail2ban status with sudo with out a password prompt.

Maybe if some one could write a sudoers and paste it in here.

Thanx guys

---

### Post by jolly79 on 2008-08-07
Man this is killing me.-..

If i add this:

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL
%jolly79 ALL=NOPASSWD: ALL

I still get a pass prompt when i use sudo...

_The best would be if this workede:_

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL
%jolly79 ALL=NOPASSWD: /usr/bin/conky

Am i all wrong here...

i have also tried this with no luck..

# User privilege specification
root ALL=(ALL) ALL
ALL ALL=NOPASSWD: /etc/init.d/fail2ban, /usr/bin/conky

---

### Post by bodhi.zazen on 2008-08-07
can you post the entire contents of the file ?

From your post it appears you have multiple listings now, and as I indicated earlier, that causes conflicts.

---

### Post by jolly79 on 2008-08-07
Hi mate thanx for a quick reply..
I dont have a lot off diffrent listings on the file, i just mess around and try to put new stuff in buut only after i delete what i have put in.

for now it looks like this:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
ALL  ALL=NOPASSWD: /etc/init.d/fail2ban

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by bodhi.zazen on 2008-08-07
change :

ALL  ALL=NOPASSWD: /etc/init.d/fail2ban

to

jolly79 ALL = NOPASSWD: /etc/init.d/fail2ban

Then run 

sudo /etc/init.d/fail2ban

in a terminal

---

### Post by DagMan on 2008-08-07
```
ALL ALL=NOPASSWD: /etc/init.d/fail2ban, /usr/bin/conky
```

try those as 2 separate entries, removing whatever else you added, and sticking them at the bottom of the file:

```
ALL ALL=NOPASSWD: /etc/init.d/fail2ban
ALL ALL=NOPASSWD: /usr/bin/conky
```



Here is my sudoers file for Hardy.
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

ALL  ALL=NOPASSWD: /usr/local/bin/access
```

the bottom line there is what allows me to run the script at /usr/local/bin/access without a password.  I'm by no means an expert but I'm sort of wondering if the Default option at the top of your file was appended correctly.  I've never just added an extra one on a separate line unless I used + or some such but it's been a really long time to remember.
As an example though, what I pasted above was the original file as it would look with the change, and as for the line begining with Default, I added to it like this, separating with a comma.
Defaults	env_reset,timestamp_timeout=0

---

### Post by jolly79 on 2008-08-07
Hi dagman

When i do enything in the end of the file i get:

jolly79@jolly79-laptop:~$ sudo /etc/init.d/fail2ban
>>> sudoers file: syntax error, line 25 <<<
sudo: parse error in /etc/sudoers near line 25


So that is a no go...

A good thing that i had /etc/sudoers already open in kate also

---

### Post by jolly79 on 2008-08-07
bodhi.zazen what you said still gives me: 
jolly79@jolly79-laptop:~$ sudo /etc/init.d/fail2ban status
[sudo] password for jolly79:


with this sudoers file:
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
jolly79 ALL = NOPASSWD: /etc/init.d/fail2ban

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by bodhi.zazen on 2008-08-07
You need to add in any commands called by /etc/init.d/fail2ban 

My best guess is /etc/init.d/fail2ban is a script, not a command.

---

### Post by jolly79 on 2008-08-07
Ok i understand that...

Do you know what to do if i only want to run conky as root then, that would still do the job.

---

### Post by DagMan on 2008-08-07
You'de think that the script running as root would launch everything as root and so on. It would be the same thing as running the init script with sudo and using a password, just that it isn't prompted for one. My soders file only has one entry which is a script that takes arguments that launch other scripts and binaries all as root.  I've done it like that with various levels of child processes calling other processes and running init scripts, so I'm still thinking that there's something wrong with the syntax of his file.  That said, I unfortunately can't help with it any more than I have.

---

### Post by mdsharp24 on 2008-08-07
First of all, why are you running conky as root?  Conky is meant to be run as a user as a system monitor for the desktop.

I can see where you need conky to access a priviledged command or script to pull into the "monitoring" but conky is made to run as a user using the .conkyrc file.

As for the sudo issue, what is your login name?  And what is your hostname?  lets say it is jolly79, and hostname is darkstar (you can get your hostname simply by typing    hostname   in a terminal

at the very end of your /etc/sudoers file , using visudo you put

```
jolly darkstar = NOPASSWD: /path/to/executable
```

---

### Post by bodhi.zazen on 2008-08-07
You would think, but not always ...

for example , mounting samba shares w/o a password requires more then the mount command ... I do not recall the exact syntax, but I think I had to add 4 commands.

---

