---
title: "can't 'unlock' any admin functions in 8.04"
date: 2008-08-09
forum: General Help
---

### Post by JettRink on 2008-08-09
I can't 'unlock' any admin functions such as user management, services etc. I get a 'could not authenticate' error message.

In addition, the synaptic package manager menu item is now missing from system -> administration menu ???

What permissions/files are screwed up to cause this ?

---

### Post by linux_tech on 2008-08-09
Can you execute any sudo commands?
Try sudo adduser username  (this will add a new user)
To unlock a user account try 
sudo passwd -u username
To verify your current users home directory permissions, use the following syntax: 
ls -ld /home/username

To easily view the current status of a user account, use the following syntax: 
sudo chage -l username

To set any of these values, simply use the following syntax, and follow the interactive prompts: 
sudo chage username

---

### Post by JettRink on 2008-08-09
thanks for your reply, the command line works fine, but that doesn't help me solve why the window interface isn't working properly...

---

### Post by linux_tech on 2008-08-09
There is also a bug associated with  [users-admin] Unlock -> "Could not authenticate. An unexpected error has occurred."
[https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/194496](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/194496)

suggests issue may be caused by using the 8.04 Release Candidate version

Common thread here seems to be -
1. Ensure /etc/hosts file is correct
2. Ensure appropriate users are added to the "polkituser" group in /etc/group

modify hosts file 
/etc/hosts
from 
127.0.0.1 localhost
127.0.1.1 aaa.bbb.com

to
127.0.0.1 localhost <machinename>
127.0.1.1 <machinename> 

also running updates when able to do so

---

### Post by JettRink on 2008-08-11
did all that thanx, problem still there ???

---

### Post by AfefTech on 2010-04-27
I have 70 machines, all experiencing this exact same problem.  When i installed Ubuntu (fresh install on each individual machine...not imaged), the problem did not exist as i was able to add additional users and packages without an issue.  I then loaded the machines into a sea crate and shipped them to Africa, they now are experiencing this issue of unlocking as well as no Synaptic in the Admin dropbox!

I have searched for 3 months to a solution and all I have found is workarounds (not an option for new users).  Any help would be much appreciated!

---

