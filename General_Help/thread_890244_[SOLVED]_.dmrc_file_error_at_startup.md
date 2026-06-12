---
title: "[SOLVED] .dmrc file error at startup"
date: 2008-08-14
forum: General Help
---

### Post by Sam324 on 2008-08-14
Hi.  When I press Enter after entering my password, I get an error saying "User's $HOME/.dmrc file will be ignored".  It says that it's read-only or something.  I confirmed that I was the owner and that every group had full access read/write permissions to the file and the home folder.  It still gave the error.  I tried deleting the file, in hopes that it would be automatically re-created for me.  It still gave the error.  No worries, I restored it from the trash bin.  How do I fix this?

---

### Post by darco on 2008-08-14
restart to a recovery console (select the recovery mode option from the grub menu) then enter:

chmod 700 /home/<yourusername>
chmod 644 /home/<yourusername>/.dmrc
reboot now

good luck 
darco

---

### Post by drs305 on 2008-08-14
> **Sam324 said:**
> I get an error saying "User's $HOME/.dmrc file will be ignored".  ... I confirmed that I was the owner and that every group had full access read/write permissions to the file and the home folder. 

How do I fix this?

Permissions are the problem in this case. The permissions for .dmrc should be 644, which means you do not want every group to have full read/write access.

The message probably says that HOME has to be owned by you and .dmrc needs 644 permissions. As long as you still have the ability to use 'sudo', you can run the following commands without going to recovery mode. If you can't 'sudo', then boot to the recovery mode as mentioned earlier.

The last command reboots the system:
```
sudo chmod 644 $HOME/.dmrc
sudo chmod 755 $HOME
sudo chown *username* /home/*username*
sudo shutdown -r now

```

The permissions for home of 755 are fairly loose. You could use 750 or 700, allowing fewer privileges for groups and others.

---

### Post by Sam324 on 2008-08-15
> **darco said:**
> restart to a recovery console (select the recovery mode option from the grub menu) then enter:

chmod 700 /home/<yourusername>
chmod 644 /home/<yourusername>/.dmrc
reboot now

good luck 
darco
Hey, I logged in today, and I just realized that it didn't show the message!  Thanks!

---

### Post by RATM_Owns on 2008-08-15
I still get that error. Next time I do, I'll try that.

---

