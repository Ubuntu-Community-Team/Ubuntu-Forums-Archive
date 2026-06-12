---
title: "how to install updates after installing 9.0.4 ?"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by rutiezer on 2009-08-06
Just installed Ubuntu 9.0.4 and assigned my login a password.

Then tried to do updates from a terminal with

sudo apt-get update

and get the error that my user id is not in the sudoers file.


Did 
visudo

and get permission denied.

I run the update manager, try to install updates and get a message that starts with

    Failed to run /usr/sbin/synaptic

How do I get updates?
How do I install/remove software?

---

### Post by starcraft.man on 2009-08-06
[Link.]("http://www.psychocats.net/ubuntu/fixsudo") I assume something went wrong with install and you were supposed to have sudo privileges, if you weren't have admin add ya.

See my sig for complete explanation of installation and upgrade.

```
sudo apt-get update
``` merely retrieves new package information. ```
sudo apt-get upgrade 
```gets ya the new packages downloaded and installed. You can just use the update manager gui as well.

---

### Post by rutiezer on 2009-08-06
I installed 9.0.4 from a live disk.
There were no installation error messages.
I am the administrator.

I was able to add new users through 
system -> administation -> User and Groups

I clicked on the tab "Unlock" and added the users, 
some with system admin privs which I saw I had.

When I look at the properties of the user id I used
to install the system "administer the system" is no
longer checked. I had initially checked all possible
user privileges.

---

### Post by slakkie on 2009-08-06
When logged in could you do two things?

```

groups

sudo -l

```

Probably you are not in the admin group. To solve this, boot into single user mode, edit /etc/group and put your name in the admin group:

```

admin:x:112:yourusername

```

Reboot and you should be able to update your system.

---

### Post by rutiezer on 2009-08-07
Yes, thank you.
I was able to boot into single user mode, edit /etc/group and put my name in the admin group. 

I did not know how to do this so let me add details of what I did for those who may have a similar problem:

Restart the computer and when I the line:
  GRUB loading, please wait
Followed the instruction on the second line and pressed the ESC to enter the menu which appeared.
There are three lines on that menu:
  Ubunbu 9.04, kernel 2.6.28-11-generic
  Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
  Ubuntu 9.04, memtest86+

Select the second line, recovery mode, and after seeing some output saw the "Recovery Menu". Scrolled down to the line that says:
   root    Drop to root shell prompt
and selected it.

At the command prompt, choose the editor vi to edit /etc/group, looked for the line starting with "admin" and added my user id to the that line and saved the file.

Typed exit at the command prompt and got back to the recovery menu.

Selected the line
    resume    Resume normal boot



After login was able to update the newly installed 9.04 with the synaptic package manager.
   
Thanks again.

---

### Post by rutiezer on 2009-08-07
Still more questions.

When 9.04 initially installed was able to add new users through
system -> administation -> User and Groups

I clicked on the tab "Unlock" and added the users,
some with system admin privs and saw from that same dialog saw in user setting that they could administer the system.


Then I am not sure what happened.
I know that I did not uncheck "Administer the system".

The next time I rebooted the system I saw that "Administer the system" was longer checked. I actually had initially checked all possible user privileges.

Any ideas about the privs disappeared?

---

