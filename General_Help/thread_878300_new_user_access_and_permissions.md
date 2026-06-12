---
title: "new user access and permissions"
date: 2008-08-02
forum: General Help
---

### Post by stoppage on 2008-08-02
Hi, I've installed a new user in Feisty,belonging to the same group as original (installation) user. Problem is he doesn't have access to all of the apps of original user, although these were installed standard by Synaptec and not in home folder. What I need is to give the new user same access and permissions to all apps as original user. Can somebody please explain how?

---

### Post by pytheas22 on 2008-08-02
Could you give some examples of the programs that the new user needs to use but is unable to?  Also, does the new user have administrative privileges?

---

### Post by stoppage on 2008-08-03
New user is member of admin group. If there is no method/command to transfer ownership/permission from one user to another then I#ll leave new user as is

---

### Post by pytheas22 on 2008-08-03
You should definitely be able to transfer permissions.  But I'm wondering why the new user is unable to run certain applications in the first place.  You can change permissions on the executables in /usr/bin so that not everyone can use them, but by default everyone should be able to run those applications.  So please tell us exactly which programs the new user is not able to run--and if he tries to launch them from the command line, what is the error message that he gets (post it in German if you don't want to translate)?

---

### Post by mike2357 on 2008-08-03
Please clarify one point.  Are you sure your new user doesn't have permissions to run programs?  Or is it that the programs don't show up in the Applications menu when your new users logs in?

Depending on which it is, the solutions would be very different.

---

### Post by stoppage on 2008-08-05
Problem applies only to apps which I've added...the standard apps work. All apps appear on applications menu. As an example, when I try to open tvtime under "new user" I get permission denied message. Some text output...

:~$ cat /etc/group |grep adm

adm:x:4:tony,newuser

lpadmin:x:113:tony

admin:x:117:tony

t:~$ groups newuser

newuser : tony adm dialout fax cdrom floppy tape audio dip plugdev scanner fuse

---

### Post by pytheas22 on 2008-08-05
> t:~$ groups newuser

newuser : tony adm dialout fax cdrom floppy tape audio dip plugdev scanner fuse 

The new user doesn't seem to have all privileges.  When I type that command for my system-administrator user, I get:

```
$ groups chris
chris adm dialout cdrom floppy audio dip **video** plugdev fuse **lpadmin admin**

```

I think the groups in bold could be making a big difference.

You can add the new user to these groups by going to System>Administration>Users and Groups and clicking "Manage Groups" (see screenshot).  I think that will help.

---

### Post by stoppage on 2008-08-06
It gets better...the group "video" doesn't exist under Manage Groups. If this continues I can foresee new user installing his very own new linux...

$ groups newuser
newuser : tony adm dialout fax cdrom floppy tape audio dip plugdev scanner **lpadmin** **admin** fuse


makes no difference

---

### Post by geirha on 2008-08-06
You can do it from a terminal too, with ```
sudo adduser newuser video
``` to add newuser to the group video.

I also don't see the video group in the Users and Groups app. It should be listed there, but it isn't, so there must be a bug with that app.

---

### Post by stoppage on 2008-08-07
When I add newuser to video group my video apps work! To try your patience a little further, I want full r/w access to installed-users home file. When I bring all files over they're read-only, (good ol' Feisty)! and all owned by installation-user! Any ideas on howto please?

---

### Post by geirha on 2008-08-08
I don't quite understand what you mean by installation-user. Could you give an example of what you mean maybe?

---

### Post by stoppage on 2008-08-08
Sorry, I'm referring to the original user who comes with first installation

---

### Post by geirha on 2008-08-08
Ah, I think understand what you want. Let's call the users olduser and newuser. You can copy the files from your olduser's homedir, but you can't move them since newuser only has write access to newuser's homedir.

If that is the case, then the easiest solution I can think of is to make newuser the owner of olduser's homedir. That will make olduser unable to log in and function normally though.
```
sudo chown newuser:newuser ~olduser
```
Now move the files you need to move, and then do
```
sudo chown olduser:olduser ~olduser
```
To return the ownership back to normal. This should make olduser work as normal again.

---

