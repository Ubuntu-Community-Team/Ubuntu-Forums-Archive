---
title: "Permission denied for root?!"
date: 2008-11-17
forum: General Help
---

### Post by khurtsiya on 2008-11-17
Typing as root

> root@michael-laptop:/home/michael#  chown -R michael:michael /home/michael/.*
chown: cannot access `/home/michael/./.gvfs': Permission denied
chown: cannot access `/home/michael/.gvfs': Permission denied
root@michael-laptop:/home/michael# 


What is the problem?

---

### Post by philinux on 2008-11-17
The .* is the problem I think.

---

### Post by cdenley on 2008-11-17
Recursive chown fails if root can't access the directory. You can't change ownership of a directory's contents if you can't list it's contents.
```

sudo ls -l ~/.gvfs

```
Be careful running commands like that, because .gvfs contains any mounted network drives.

---

### Post by Marius Derekus on 2008-11-17
You could try adding **sudo** in front of the command just in case.

---

### Post by chris09 on 2008-11-17
You need to add the user to the sudoers group,i had the same problem and fixed it but i forgot,lol sorry but im sure i messed around with the sudoers file.

---

### Post by cdenley on 2008-11-17
As you can see from his prompt, which starts **root@**, he already has his shell running as root, so it's not a problem with sudo. The "problem" is that root can't access directories unless it has permission to do so.

---

### Post by Marius Derekus on 2008-11-17
Sorry, just making sure. Then try using the```
gksudo nautilus
``` command. There will be a separate window with super permissions, with this window you can change any permissions you want on any file (It would be smart to change them back once you're done with whatever you're doing)

---

### Post by khurtsiya on 2008-11-18
Everybody thanks for answers. I am new in linux and typing this command to fix this problem [http://ubuntuforums.org/showthread.php?t=107269](http://ubuntuforums.org/showthread.php?t=107269)

and recomendation post is here [http://ubuntuforums.org/showpost.php?p=597583&postcount=2](http://ubuntuforums.org/showpost.php?p=597583&postcount=2)

May be this helps to understand my problem and what I ned to do to solve it.

TIA

Michael

---

### Post by khurtsiya on 2008-11-20
Any tips?

---

### Post by rampageoberon on 2008-11-20
surely just the following would work (using sudo or root if necessary)

```
chown -R michael:michael /home/michael/
```

I don't see any reason to have the ".*" in chown -R michael:michael /home/michael/**.***

---

### Post by khurtsiya on 2008-11-20
Thanks for your answer, but

> root@michael-laptop:/home/michael# chown -R michael:michael /home/michael/
chown: cannot access `/home/michael/.gvfs': Permission denied
root@michael-laptop:/home/michael# 


---

### Post by vanadium on 2008-11-20
Don't worry: it is normal that even root cannot change permissions of the gnome virtual file system.

---

### Post by khurtsiya on 2008-11-20
ehhmm... 

so how those guys in the thread mentioned above done that?!

---

### Post by cdenley on 2008-11-20
> **khurtsiya said:**
> ehhmm... 

so how those guys in the thread mentioned above done that?!

You won't be able to change the permission on any network mounts which appear in .gvfs. You can change the ownership of the .gvfs directory itself. You can also list the contents of the .gvfs directory, but root cannot with the directory's default permissions. If root can't list the contents, then any recursive function attempt will fail. The directory is probably empty, but root can't tell until it gets a directory listing. There is probably a good reason for the restricted permissions, but to make your error go away:
```

sudo chmod 755 /home/michael/.gvfs

```

---

### Post by vanadium on 2008-11-20
Two pages for a problem that is not a problem. The reported behavior is normal for a default Ubuntu install.

---

### Post by khurtsiya on 2008-11-21
> **cdenley said:**
> There is probably a good reason for the restricted permissions, but to make your error go away:
```

sudo chmod 755 /home/michael/.gvfs

```

Thanks for your answer, but it returned the same.

> michael@michael-laptop:~$ sudo chmod 755 /home/michael/.gvfs
chmod: cannot access `/home/michael/.gvfs': Permission denied
michael@michael-laptop:~$ 


Here is the [_link_]("http://ubuntuforums.org/showpost.php?p=597583&postcount=2") to post **where author suggests to run this command** to solve some problem and after it **there are many thanks-post (people saying that this command helps from what I conclude that it should work)**.

I cant ask just right there cuz it is archived thread.

Can anyone help with this?

TIA

---

### Post by cdenley on 2008-11-21
> **khurtsiya said:**
> Thanks for your answer, but it returned the same.



Here is the [_link_]("http://ubuntuforums.org/showpost.php?p=597583&postcount=2") to post **where author suggests to run this command** to solve some problem and after it **there are many thanks-post (people saying that this command helps from what I conclude that it should work)**.

I cant ask just right there cuz it is archived thread.

Can anyone help with this?

TIA

I guess the permissions on .gvfs are a little more complicated than I realized. The post you linked to said there were some directories in their home directory which ended up being owned by root. This isn't related to your .gvfs directory. Try running this command
```

ls -al ~|grep root

```
to see if this is even your problem.

---

### Post by khurtsiya on 2008-11-21
> **cdenley said:**
> I guess the permissions on .gvfs are a little more complicated than I realized. The post you linked to said there were some directories in their home directory which ended up being owned by root. This isn't related to your .gvfs directory. Try running this command
```

ls -al ~|grep root

```
to see if this is even your problem.

This is the answer

> michael@michael-laptop:~$ ls -al ~|grep root
michael@michael-laptop:~$ sudo ls -al ~|grep root
[sudo] password for michael: 
ls: cannot access /home/michael/.gvfs: Permission denied
michael@michael-laptop:~$ 


I do not understand what it means.

Can you explain?

---

### Post by cdenley on 2008-11-21
> **khurtsiya said:**
> This is the answer



I do not understand what it means.

Can you explain?

It means you do not have anything owned by root in your home directory. The post you linked to is not related to whatever your problem is.

---

### Post by bapoumba on 2008-11-21
[https://bugs.launchpad.net/gvfs/+bug/225361](https://bugs.launchpad.net/gvfs/+bug/225361)

For now, any mounted fs can only be accessed by the user who mounted it, not even root:
[http://bugzilla.gnome.org/show_bug.cgi?id=534284](http://bugzilla.gnome.org/show_bug.cgi?id=534284)
[http://bugzilla.gnome.org/show_bug.cgi?id=560658](http://bugzilla.gnome.org/show_bug.cgi?id=560658)

I know, it is not really an answer, but at least what you see is consistent with what was chosen.

---

### Post by ibuclaw on 2008-11-21
Leave gvfs alone ;)

As for the **chown ~/.*** ... I would advise against that.

Linux has two hardlinks
.  - The current directory
.. - The upper directory

so ~/.* may match both /home/foo/* and /home/*

use the ? glob match instead, it's much safer ;)

```

chown ~/.??*

```

[EDIT]
Proof:
```
find ~/.* -print | sort | less

```
Outputs (eventually):
```
/home/iain/../ellz
/home/iain/../ellz/.aptitude
/home/iain/../ellz/.bash_history
/home/iain/../ellz/.bash_logout
/home/iain/../ellz/.bashrc
/home/iain/../ellz/build
/home/iain/../ellz/build/bin

```

Regards
Iain

---

### Post by BrownieMan on 2008-12-07
was a solution ever found for the original problem using amarok. I have the same problem.

---

