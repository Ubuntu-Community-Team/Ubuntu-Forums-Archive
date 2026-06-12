---
title: "Making Ubuntu ask Me for password everytime I use sudo or open a program as root?"
date: 2008-07-26
forum: General Help
---

### Post by Exsecrabilus on 2008-07-26
By default, when you open a program as root, it asks you for your password, and for 15 minutes, it doesn't if you open another root program.

But I read somewhere (a long time ago) there was some way to make your system ask you for your password *every time* you opened an application as root or you use sudo in Terminal. How can I do it?

---

### Post by firebadger on 2008-07-26
You need to edit your /etc/sudoers file and add a timestamp_timeout setting.  See the man page for sudoer for more info.

Cheers!

---

### Post by Exsecrabilus on 2008-07-26
> **firebadger said:**
> You need to edit your /etc/sudoers file and add a timestamp_timeout setting.  See the man page for sudoer for more info.

Cheers!
What?

---

### Post by spiderbatdad on 2008-07-26
```
man sudoers
```

look at the /etc/sudoers file:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

``` Something like that, is the default. I you edit the "Defaults" line to include ,timestamp_timeout=0,insults, that should do it. So you get:```
!lecture,tty_tickets,timestamp_timeout=0,insults,!fqdn
```insults are very important.

---

### Post by Brando569 on 2008-08-04
i forgot about the insults part :D another reason why i love linux

---

### Post by cat2005 on 2009-08-19
> **spiderbatdad said:**
> ```
man sudoers
```look at the /etc/sudoers file:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults    !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

``` Something like that, is the default. I you edit the "Defaults" line to include ,timestamp_timeout=0,insults, that should do it. So you get:```
!lecture,tty_tickets,timestamp_timeout=0,insults,!fqdn
```insults are very important.



How about that?  

Just a little over a year later and I have the exact same question!  Of course, I still need a little more help.

If I understood this thread correctly, then I must input:

**!lecture,tty_tickets,timestamp_timeout=0,insults,!fqdn **

But exactly where?  At the bottom?  Top?  I am using version 9.04 so would this method still apply?

Relatedly, I know I am supposed to use "visudo" to do so but all the literature (including the visudo man page) is confusing.  Do I just type:

**sudo visudo**

into a terminal?  Then what?

Thanks in advance.

---

### Post by rbc on 2009-08-19
cat2005, 
Type this in terminal:
sudo vim /etc/sudoers

Unless you have made prior changes to it, the sudoers file will look just like the example spiderbatdad gave, with this line already in it:
Defaults	!lecture,tty_tickets,!fqdn

You need to insert what spiderbatdad said, so that the line looks like this:
!lecture,tty_tickets,timestamp_timeout=0,insults,!fqdn

I have never taken the time to learn vi or vim well, but they are supposed to be really powerful editors. If you have never used either, you ought to do some reading first:

[http://www.yolinux.com/TUTORIALS/LinuxTutorialAdvanced_vi.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAdvanced_vi.html)

---

### Post by drs305 on 2009-08-19
If you want to use a more familiar editor, such as gedit, you can do it by running this command before invoking visudo:
```

export EDITOR=gedit
sudo -E visudo

```

---

### Post by cat2005 on 2009-08-19
> **drs305 said:**
> If you want to use a more familiar editor, such as gedit, you can do it by running this command before invoking visudo:
```

export EDITOR=gedit
sudo -E visudo

```


Doing so will still make use of "visudo", correct?  Everything I read stated I should use visudo.

---

### Post by drs305 on 2009-08-19
> **cat2005 said:**
> Doing so will still make use of "visudo", correct?  Everything I read stated I should use visudo.

Yes it will.

---

### Post by cat2005 on 2009-08-20
drs305, et al:

Did I do something wrongly?  Here is my terminal input and output.  Yes, I got all of this.  I have not done anything since.



hltprime@linuxcpu:~$ export EDITOR=gedit
hltprime@linuxcpu:~$ sudo -E visudo
[sudo] password for hltprime: 
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)



It repeated this at least 10 times.  What does it mean?

---

### Post by drs305 on 2009-08-20
> **cat2005 said:**
> Did I do something wrongly?  Here is my terminal input and output.  Yes, I got all of this.  I have not done anything since.


No, you didn't do anything wrong with those commands. They merely allow you to use a more familiar editor. Even though you may receive a large number of those messages, a gedit window should open and allow you to edit the sudoers file. Just leave the terminal window open and go to the gedit window to make the changes. Once you close gedit after saving your revised sudoers file, you can close the terminal window with the error messages.

Can you use the standard command: **sudo visudo** and use the default editor?

---

### Post by cat2005 on 2009-08-22
> **drs305 said:**
> No, you didn't do anything wrong with those commands. They merely allow you to use a more familiar editor. Even though you may receive a large number of those messages, a gedit window should open and allow you to edit the sudoers file. Just leave the terminal window open and go to the gedit window to make the changes. Once you close gedit after saving your revised sudoers file, you can close the terminal window with the error messages.

Can you use the standard command: **sudo visudo** and use the default editor?


I think I got it.  Thanks!

---

### Post by jerome1232 on 2009-08-22
> **spiderbatdad said:**
> insults are very important.

My favorite feature of sudo :)

---

