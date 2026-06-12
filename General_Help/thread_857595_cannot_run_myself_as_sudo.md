---
title: "cannot run myself as sudo"
date: 2008-07-12
forum: General Help
---

### Post by diggs on 2008-07-12
Hi there, I have a fresh install of HHx86 here. I installed virtual box and it told me that I needed to be a member of the vboxusers group. so I went like this:

sudo usermod -G vboxusers derek

and now I cannot make any changes to the system. I am the only user on the installation.

Thanks!

---

### Post by sdennie on 2008-07-12
I think the command you ran removed you from all groups but the vboxusers group.  You'll need to boot into recovery mode (it's an option from the grub menu and you may have to hit escape while the machine is coming up).  From there, you can get a root shell and do this:

```

adduser derek derek
adduser derek admin
exit

```

That will allow you to have admin privileges again.  You may want to then go into System->Administration->Users & Groups and edit your user so that you have your owld permissions on the machine.

---

