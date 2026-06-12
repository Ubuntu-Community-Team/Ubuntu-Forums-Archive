---
title: "User's $Home/.dmrc file is being ignored."
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by laeg_ on 2009-06-23
Everytime I log in to 9.04, although I had this problem on 8.10 I get the error message:
> 
User's $Home/.dmrc file is being ignored. This prevents the default session language from being saved. File should be owned by user and have 644 permissions. User's $home directory must be owned by user and not writable by other users.

I think the problem stems from when I imported files from my home dir on an old ubuntu install into my new one and then someone from #ubuntu had me run some permission command in terminal but I can't remember it.

How can I remedy this?

---

### Post by Brandon Williams on 2009-06-23
Run this command and check the output:
```
$ ls -ld $HOME $HOME/.dmrc
```
The first column tells you the permissions of the file/directory. The permissions for your home directory should be either 'drwxr-xr-x' or 'drwx------', and the permission for the .dmrc file should be either '-rw-r--r--' or '-rw-r--r--'. Notice that each set of permissions will only ever have one 'w'. Also, both the directory and the .dmrc file should be owned by you.

If the permissions are wrong, then run this command:
```
$ chmod og-w $HOME $HOME/.dmrc
```

If the ownership is wrong, then run this command:
```
$ sudo chown $USER $HOME $HOME/.dmrc
```

---

### Post by ricardisimo on 2009-06-23
This is directly from an identically titled thread. Hard to believe this hasn't been resolved or somehow bypassed already.
> ```
sudo chmod 644 /home/ricardimo/.dmrc
sudo chown ricardisimo /home/ricardisimo/.dmrc
sudo chmod -R 700 /home/ricardisimo
sudo chown -R ricardisimo /home/ricardisimo
```
You substitute your user name with mine, of course. Also, read up on the permissions. I saw quite a few recommendations for 755, 766 and 777, but I think for my purposes 700 was correct.

---

### Post by laeg_ on 2009-06-23
Someone from #ubuntu had me do a sudo chmod 644 ~/.dmrc after which I checked the permissions and ownership, the former was incorrect so I corrected it with the command recommended.

No more error on login.

Thanks!

---

### Post by drpiotrowski on 2009-10-16
Hey all,

I'm a rather new Ubuntu user and have been loving it so far. 

I've been having this problem, though, ever since I tried to install the Linux Z600 driver. Not only do I get this message, but once I click "OK" all that comes up is a black screen and mouse pointer.

I'm really at a loss for what to do (I have no idea how to work within from without), so any help here would be appreciated tremendously! Thank you so much

---

### Post by drpiotrowski on 2009-10-16
Nevermind! Problem solved with Ctrl+Alt+F1 and this fix. Thanks!

---

