---
title: "Installation - home directories already exist problem"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by yvinogradov on 2009-10-27
I have more than one user on my Ubuntu system, each with it's own home directory, and /home resides on a separate partition, so that every time when I reinstall the system the home directories stay preserved. The problem (#1) is that the Ubuntu installation doesn't seem to prompt for more than just one username, and the rest have to be created manually later on (or am I missing a step in the installation process?). Problem (#2) is that when I create those other users manually later on I can't link them to their already existing home directories, the 'Add User' feature complains that the 'home directory already exists'. I have a workaround for that which is create a dummy directory first, click OK, then go into the properties of this newly created user and change the home directory from 'dummy' to the real one, this step repeated for every single user. Is there a meangful justfication for the utility refusing to create users with an already existing home directory?

Thanks!

---

### Post by fbugnon on 2009-10-27
> **yvinogradov said:**
> Is there a meangful justfication for the utility refusing to create users with an already existing home directory?

I guess the more obvious reason is to avoid data been overwriting and/or new users end up, *by mistake*, with files/preferences of old users. 

But of course it could have an option such as "ignore warning (I know what I'm doing)" or "create anyway (use previous user /home folder)" or something like this.

---

### Post by cwsnyder on 2009-10-28
You can specify the 'old' user directory when creating the new users, but you have to do this from the command line, not the GUI.  I have done this, but only with the help of a tutorial, which I don't have to hand.

---

### Post by albandy on 2009-10-28
You have some options.
For example, making a backup of the user and group configuration:
before reinstall make a backup of /etc/passwd, /etc/shadow, /etc/group
when installed replace the contents of each file with the backuped ones.

Or making an script like this:
#!/bin/bash
cd /home
for i in *
do
adduser $i (see the help of adduser to pass all you need by parameters)
done

---

### Post by apbsa on 2009-10-28
I had this problem too. I changed the name of original user's home directory to something else and created the new user, then changed the new users directory to another name, and the old home directory back to it's original. Did that make sense? Worked for me.

---

