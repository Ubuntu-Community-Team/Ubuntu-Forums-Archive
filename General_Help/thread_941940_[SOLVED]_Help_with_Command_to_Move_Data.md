---
title: "[SOLVED] Help with Command to Move Data"
date: 2008-10-08
forum: General Help
---

### Post by strange_cathect on 2008-10-08
I had a hard drive failure and am now installing Ubuntu on the new hard drive. I have a backup of my /home data on an external disk and I want to move the data over.

So far I created a new /, /home, and SWAP partitions. I am currently installing Ubuntu on /. I've asked the installer to leave the /home partition alone.

How do I get the data from my external drive over to the new /home while I'm using the installer CD? Everything I've tried gives me permissions issues.

Help!

---

### Post by bodhi.zazen on 2008-10-08
sounds like a basic permissions problem.

You can either change the permissions of the mount point (how to do this is dependent on the file system) or use root.

```
sudo -i
```

Or 

```
gksu nautilus
```

Make sure you change ownership of the data to your user (you may not be able to do that without creating a user on the live CD, you may need to install and boot to recovery mode).

---

### Post by strange_cathect on 2008-10-08
How do I change ownership of the data?

On the new installation I've used the exact same computer name, user name, and password.

When I became the superuser of nautilus, as you suggested, and copied all the data from old /home over to new /home I ran into some problems. I didn't have permissions for certain folders. And my information in my Thunderbird, for example, didn't seem to work anymore. Many of the programs ceased working. I ended up chucking it and doing a fresh install. Back to square one. What is the best way to proceed?

---

### Post by bodhi.zazen on 2008-10-08
Once you have transferred the data,

```
sudo chown user.user -R /home/user
```

Where "user" is you user name.

The log off and back in.

---

