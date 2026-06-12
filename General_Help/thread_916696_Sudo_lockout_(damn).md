---
title: "Sudo lockout (damn)"
date: 2008-09-11
forum: General Help
---

### Post by TeWeE on 2008-09-11
Hi,

I was trying to give my friend admin-access to a Ubuntu server, so I edited /etc/group by adding ":his-username" after mine. But after that, I realized that I should have separated the usernames with a comma ( , ), and not colon ( : ). Now I'm not able to change the /etc/group because I'm not a sudoer anymore.

Can anyone tell me how to change this back to what it was before, if I can't get to the machine physically? There is no backup because it was installed some days ago.

---

### Post by iaculallad on 2008-09-11
One simple solution if you edited the group file with gedit would be:

```
sudo cp /etc/group /etc/group.original
sudo rm /etc/group
sudo cp /etc/group~ /etc/group
```

---

### Post by ripps818 on 2008-09-11
Can you boot into Recovery Mode?
You should be able to access the file as the root user.

---

### Post by TeWeE on 2008-09-11
> **iaculallad said:**
> One simple solution if you edited the group file with gedit would be:

```
sudo cp /etc/group /etc/group.original
sudo rm /etc/group
sudo cp /etc/group~ /etc/group
```

But I'm not able to make a sudo-command at all ("Tewee is not in the sudoers file.  This incident will be reported.")

---

### Post by TeWeE on 2008-09-11
> **ripps818 said:**
> Can you boot into Recovery Mode?
You should be able to access the file as the root user.

No. The server is in a hosting center, so, I'm only able to reboot it from the command-line over SSH.

---

