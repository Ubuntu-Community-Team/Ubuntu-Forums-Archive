---
title: "[SOLVED] gksudo or sudo that's the question ?"
date: 2008-10-06
forum: General Help
---

### Post by Kevbert on 2008-10-06
Up to now I've been using sudo whenever I've needed root privileges.
When should I use gksudo and when sudo ?  For example I've reported a bug and its been suggested that I should use gksudo for this command:
```
gksudo gedit /boot/grub/menu.lst
```
Yet sudo works fine. I've looked at the man pages and they don't help.
Can anyone shed some light on this ?

---

### Post by snowpine on 2008-10-06
You should use sudo if it's a terminal application: 'sudo nano /boot/grub/menu.lst' or 'sudo apt-get install conky'

And gksu if it's a graphical application: 'gksu gedit /boot/grub/menu.lst' or 'gksu synaptic'

I am not 100% sure the reason why. :) Like you, I've successfully used sudo for graphical applications sometimes when I forget gksu.

---

### Post by issih on 2008-10-06
its about the environment the application runs in, and which configuration file it loads when it is launched. Most of the time you get away with using sudo, but sometimes you don't, and then it can get messy....so don't do it!!:)

See here for more info:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Hope that helps

---

### Post by Kevbert on 2008-10-07
> **issih said:**
> its about the environment the application runs in, and which configuration file it loads when it is launched. Most of the time you get away with using sudo, but sometimes you don't, and then it can get messy....so don't do it!!:)

See here for more info:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Hope that helps

Thanks for the reply.  Clear it isn't, but there is one thing in the article that is really useful: ***These errors occur because sometimes when sudo launches an application, it launches with root privileges but uses the user's configuration file. ***  So if I want something to be set globally (for all users) I should use gksudo and sudo only for personal settings.

---

### Post by issih on 2008-10-07
> **Kevbert said:**
> Thanks for the reply.  Clear it isn't, but there is one thing in the article that is really useful: ***These errors occur because sometimes when sudo launches an application, it launches with root privileges but uses the user's configuration file. ***  So if I want something to be set globally (for all users) I should use gksudo and sudo only for personal settings.

Not really no, root isn't an "all users" kind of thing, its just another user, but one who has the right to do whatever they want to the system. In the same way as every user has its own set of configuration files for each application, so does root.

In ubuntu the root user is hidden slightly, as ubuntu's security model stops you running directly as the root user. therefore the root user doesn't have a home directory, but in most other ways it is literally just another user, but one with administrative capabilities.

To give an example of the kind of problems that can occur, if you run the file manager (nautilus) as root using sudo, it is launched using your users configuration file for nautilus.

Consequently the application knows where your home directory is, where any shortcuts you've dropped in the sidebar are and where your trash directory is.

now imagine you delete something owned by root (which because you used sudo you can do). Because nautilus is configured for your user it puts deleted files in your trash directory.

You now have a file owned by root in your trash directory (which is of course owned by you). At a later date when you try and empty your trash, you can't because you don't have permission to delete the file owned by root.

Its not really to do with global and local settings at all, it just can mess up the system.

In the end though, just use gksudo with graphical apps, and don't worry about it :)

Hope that helps

---

### Post by Kevbert on 2008-10-07
Thanks. That explains why I had some deleted files in the trash with root permissions a while back and had to use the dangerous
```
sudo rm -rf *directory*
sudo rm -f *file*
```
commands for my trash folder.

---

### Post by Sef on 2008-10-07
From [Root/Sudo]("https://help.ubuntu.com/community/RootSudo"):

> You should **never** use normal sudo to start graphical applications as root. You should use gksudo (kdesudo on *Kubuntu*) to run such programs.  gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by root. (AFAICT, this is all that's special about the environment of the started process with gksudo vs. sudo). 

---

### Post by jerome1232 on 2008-10-07
That clears it up for me, I've been using the graphical method only because I knew sudo didn't play well with a few graphical apps, now I know why.


Is there a separate graphical launcher for xfce?

---

### Post by Sef on 2008-10-07
for xubuntu and Ubuntu, use gksudo.   For kubuntu, use kdesu.

---

