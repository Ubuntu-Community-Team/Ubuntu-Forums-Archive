---
title: "[SOLVED] Root Problem"
date: 2008-10-06
forum: General Help
---

### Post by lucast on 2008-10-06
I am having trouble with doing any sort of Admin

My Ubuntu 8.04 is missing Add/Remove programs from the applications list.  When I go into Add new user and click on Unlock it comes up with Unable to Authenticicate, without even asking me for roots password.  When I try and use SU in terminal it says Unable to Authenticicate.  When I use SUDO it says something like Not in Sudoers list.

I tried edititing the Applications menu and adding Add/Remove Applications back to the list, but after I tick it, the tick just dissapears again.

The last thing that I did before all this started happening was to add a new user called Admin, but I forgot to add it to the Administrators group.  Could this be the problem? But now I don't know how to remove this user or make any changes or fix the problem

Please help :-(

---

### Post by justleen on 2008-10-06
can you still login with the old user? eg, not the newly created admin one?

---

### Post by lucast on 2008-10-06
I can still login with both, with no problems

---

### Post by davidryder on 2008-10-06
Login as the user used to create the new user, give it admin rights, logout and log back in as the new user.

---

### Post by lucast on 2008-10-06
That seems to be the problem.  I go to window where you can Add/Change users, and I can't unlock it to modify the users.

When I click the unlock button it says unable to authenticicate.  It dosent even give me a chance to type in my password.

---

### Post by justleen on 2008-10-06
and openening a "real" terminal with ctrl-alt-F2, then login as your first user, and sudo su? does that work?

---

### Post by davidryder on 2008-10-06
> **lucast said:**
> That seems to be the problem.  I go to window where you can Add/Change users, and I can't unlock it to modify the users.

When I click the unlock button it says unable to authenticicate.  It dosent even give me a chance to type in my password.

You have to do this with the user used to create the new account.

---

### Post by lucast on 2008-10-06
Im at work at the moment, so will have a go tonight.  But this is what I tried last night. (Also im quite new to Linux, so still trying to find my way and use the right terminology)

When I first installed Ubuntu 8.04 (2 months ago) I setup a user called 'tlucas' and gave it a password.  This password was also used for 'Su' and all admin type stuff (installing new programs etc).

Since then I created an account called admin whilst logged into 'tlucas' but didn't give it admin rights (by mistake).  I created an account by unlocking the Add User Screen and creating the Admin user.

I can still log into both accounts.

Last night I logged into 'tlucas' the original account to add the user Admin to the Admin group.  But I can't unlock the User screen to make changes, so I cant add Admin to the Admin Group.

---

### Post by davidryder on 2008-10-06
Ah... I understand now :)

When you get home go to System|Administration|System Log and check auth.log for any abnormalities. Aside from that, I wouldn't know where to start without more info. 

Good luck!

---

### Post by lucast on 2008-10-06
Will do.  Cheers for you help.  Will post back here later.

If all else fails I will re-install Ubuntu.  It will only take an hour or so, and I haven't really customised anything yet.

---

### Post by geirha on 2008-10-06
Have you changed the hostname lately? I've seen similar problems when trying to change hostname without changing it in all necessary files. What's the output of these commands in a terminal:
```

hostname
cat /etc/hosts

```
The output of hostname should match the last word of the line starting with **127.0.1.1** in /etc/hosts

Also, try running groups on the two users to compare their group membership:
```

groups *olduser*
groups *newuser*

```

---

### Post by lucast on 2008-10-06
Will be home in 5 hours.  Will look straight away.

---

### Post by lucast on 2008-10-06
Hi,

Here is the output of Auth.log when I try and SU in a terminal:

Oct  6 21:25:23 tlucas-desktop su[6743]: pam_unix(su:auth): authentication failure; logname=tlucas uid=1000 euid=0 tty=pts/1 ruser=tlucas rhost=  user=root
Oct  6 21:25:25 tlucas-desktop su[6743]: pam_authenticate: Authentication failure
Oct  6 21:25:25 tlucas-desktop su[6743]: FAILED su for root by tlucas
Oct  6 21:25:25 tlucas-desktop su[6743]: - pts/1 tlucas:root


Here is the output of Hosts and Groups:

tlucas@tlucas-desktop:~$ hostname
tlucas-desktop
tlucas@tlucas-desktop:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	tlucas-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
tlucas@tlucas-desktop:~$ groups tlucas
tlucas adm dialout fax cdrom floppy tape audio dip video plugdev scanner fuse lpadmin vboxusers
tlucas@tlucas-desktop:~$ groups admin
admin dialout cdrom audio dip video fuse



Any Ideas?

---

### Post by geirha on 2008-10-06
Ah, your trying to use su? You should use sudo in ubuntu. If you want a root shell, you can do ```
sudo -i
``` and supply your own password. 

If you just need to run one command as root, just prepend the command with sudo.

However, your user need to be a member of the admin group to use sudo. According to the groups command, your user is not a member. Use your old user, or boot into recovery mode and run ```
sudo adduser tlucas admin
``` to add your user to the admin group.

---

### Post by lucast on 2008-10-06
Hi again,

All I want to do is install some programs and delete the admin account I created.  (install programs via the applications menu in Gnome which has dissapeared)

I just tried sudo -i and got the message 'tlucas is not in the sudoers file.  This incident will be reported.'

Also how do I get into recovery mode please?

Many thanks for all your help!

---

### Post by geirha on 2008-10-06
During boot, when the grub menu shows up, select the second option, which should be recovery mode. If you don't see the menu during boot, it is probably hidden (I think that is default in Hardy) so look for a message saying something like hit Esc to see menu, and hit Esc.

---

### Post by lucast on 2008-10-06
:guitar::lolflag::popcorn:


Your a Star thank you :-)  It all works again now :-)

---

