---
title: "[SOLVED] File in /home named .directory, cannot be deleted."
date: 2008-10-07
forum: General Help
---

### Post by Soupcan on 2008-10-07
As the title says, there is a file in my /home directory that cannot be deleted or moved. I've used sudo, but it still says "permission denied". How is that possible?

---

### Post by Steve1961 on 2008-10-07
> **Soupcan said:**
> As the title says, there is a file in my /home directory that cannot be deleted or moved. I've used sudo, but it still says "permission denied". How is that possible?

Post a "ls -la filename" here

---

### Post by Fixman on 2008-10-07
> **Soupcan said:**
> As the title says, there is a file in my /home directory that cannot be deleted or moved. I've used sudo, but it still says "permission denied". How is that possible?

This file is a bug in Ubuntu that comes in at random times (for some reason, GNOME sometimes treats root as a normal user and assigns a home "folder" called .directory). Its harmless to delete anyway (throught you can only do it from the terminal).

---

### Post by jerome1232 on 2008-10-07
> **Steve1961 said:**
> Post a ls -la filename here

make it ls -lad .directory

> **Soupcan said:**
> As the title says, there is a file in my /home directory that cannot be deleted or moved. I've used sudo, but it still says "permission denied". How is that possible?

it you indeed determine you don't want this folder sometimes you have to force it to be removed
```
rm -rfv .directory
# or if it's not owned by your user
sudo rm -rfvI .directory
```

I add the -I switch so you can double check your typing before you hit enter, that command can bite you in the butt hard if it is misstyped!

---

### Post by Soupcan on 2008-10-07
Output of ls -lad .directory:
lrwxrwxrwx 1 root root 44 2008-09-15 19:36 .directory -> /etc/kubuntu-default-settings/directory-home

I've never installed Kubuntu or KDE. I'm slightly confused.

sudo rm -rfvI .directory- if I copy and paste that, will it work correctly?

---

### Post by Soupcan on 2008-10-07
Should I try to delete it by using gksudo nautilus?

---

### Post by jerome1232 on 2008-10-07
Well it looks like it's just a symlink to /etc/kubuntu-default-settings/directory-home, you can easily re-create it.

Someone mentioned it was a bug in Gnome and that simply deleting it is fine.

---

### Post by Soupcan on 2008-10-07
sudo rm -rfvI .directory failed. Permission denied again. However, I restarted and used sudoed nautilus to remove the file. Strange that sudo commands didn't work... But it's gone now. Thanks for your help everyone!

---

