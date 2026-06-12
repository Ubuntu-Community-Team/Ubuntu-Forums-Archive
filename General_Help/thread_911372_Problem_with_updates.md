---
title: "Problem with updates"
date: 2008-09-05
forum: General Help
---

### Post by M4rotku on 2008-09-05
Hello all,

A few days back, I started to recieve a notification saying that the update info is out of date (the ! triangle).  Well, checked for updates, it came up with a bunch of errors about not being able to retrieve this or that, but it always came up.  Now, I tried the command "sudo apt-get update" and recieved the following error:

> E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory


This normally occurs if I also have synaptic up or something, but I didn't.  Then, The triangle appeared again and when I clicked "Check," I recieved the same error message about not getting a lock on the directory.

This message about the lock only appeared after I edited my sources.list to include the repository for the cairo dock that I was trying to install.

Can anyone help me get rid of this error?

Much thanks,
M4rotku

---

### Post by Nepherte on 2008-09-05
It means that another process has a lock on that file. Does it happen all the time? Mostly if you wait a little, the lock has been released. You can always relogin, that always helps.

---

### Post by M4rotku on 2008-09-06
It happens all the time now.  I even turned off my computer and tried again the next day and got the same error message.

---

### Post by drs305 on 2008-09-06
If this is a non-recurring problem (in that you haven't repeatedly solved it and then come across it again), and rebooting didn't help, try running these commands to physically remove the lock file. Replace *username* with your username:
```

sudo chown *username* /var/lib/apt/lists/lock
rm /var/lib/apt/lists/lock

```

---

### Post by M4rotku on 2008-09-06
joey@joey-laptop:~$ sudo chown joey /var/lib/apt/lists/lock
[sudo] password for joey: 
joey@joey-laptop:~$ rm /var/lib/apt/lists/lock
rm: cannot remove `/var/lib/apt/lists/lock': Permission denied
joey@joey-laptop:~$


Permission is still denied

---

### Post by drs305 on 2008-09-06
> **M4rotku said:**
> 
Permission is still denied

Well, you could try to delete it this way. Note this is still a guess on my part as to whether deleting it will solve your dilemma:
```

gksu nautilus /var/lib/apt/lists

```

When it opens you should see the 'lock' file and be able to delete it.

---

### Post by M4rotku on 2008-09-06
I opened the file using the text editor and it was blank.  I didn't try to delete it, I am thinking that that would be a bad idea unless someone can confirm.  I am thinking that this is definitely caused by another problem and if I were to override it, I would be allowing multiple apps to access the lock at the same time, which could be bad, hence the reason for the lock.

Any other ideas?

---

