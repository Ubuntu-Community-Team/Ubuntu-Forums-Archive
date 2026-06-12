---
title: "[SOLVED] Cannot empty root trash"
date: 2008-11-04
forum: General Help
---

### Post by anuragji on 2008-11-04
Hello,

My disk space was filling up mysteriously and sure enough when I went to check root/.local/share/Trash/files the folder was filled with about 34GB of files.

But I can't seem to be able to get rid of them! When I open nautilus as root and try to delete the files, the simply reappear. When I run ```
sudo rm -rf ~/root/.local/share/Trash/*
``` in a terminal window nothing happens.

I did some searching but could not find any solution.

Does have anybody an idea how ??

Thanks!

Anurag

---

### Post by drs305 on 2008-11-04
In nautilus as root, SHIFT-DELETE the Trash folder, otherwise it may simply be deleted to..... Trash.
```

gksudo nautilus /root/.local/share/

```

The Trash folder will be regenerated the next time root deletes something.

I have a link in my signature line about finding and deleting trash from your system.

---

### Post by anuragji on 2008-11-04
Gee Thanks!!! That totally worked!

---

### Post by cesarsalles on 2010-05-21
thanks a lot. I had File Systems 92% full; after reading your tip it is only 38% full.

---

### Post by jerome1232 on 2010-05-21
Just wanted to point out the reason your command was failing is in red.

```
sudo rm -rf [COLOR="Red"]~[/COLOR]/root/.local/share/Trash/*
```

When you use sudo, you are still your own user, just with root privileges. So what your saying right there is

Delete everything at /home/myuser/root/.local/share/Trash/

when root trash is at /root/.local/share/Trash/

You get what I'm saying?

---

### Post by cybernet on 2010-09-17
i don't know your ubuntu version
but in lucid
it's not like that
check screenshot

---

### Post by jerome1232 on 2010-09-17
> **cybernet said:**
> i don't know your ubuntu version
but in lucid
it's not like that
check screenshot

Yes it is. You are also not using Ubuntu or you unlocked the root account because in Ubuntu the root account is locked by default and cannot be logged into which is what you do in your example.


See how in the cat of /etc/shadow that root has an * in it? That means the account is locked and cannot be logged into.

```
jeremy@main:~$ su root
Password: 
su: Authentication failure
jeremy@main:~$ sudo echo $HOME
[sudo] password for jeremy: 
/home/jeremy
jeremy@main:~$ sudo -i
root@main:~# echo $HOME
/root
root@main:~# exit
logout
jeremy@main:~$ sudo -s
root@main:~# echo $HOME
/home/jeremy
root@main:~# exit
exit
jeremy@main:~$ sudo cat /etc/shadow | grep root
root:*:14732:0:99999:7:::

excerpt from man shadow
       encrypted password
           Refer to crypt(3) for details on how this string is interpreted.

           If the password field contains some string that is not a valid
           result of crypt(3), for instance ! or *, the user will not be able
           to use a unix password to log in (but the user may log in the
           system by other means).

           This field may be empty, in which case no passwords are required to
           authenticate as the specified login name. However, some
           applications which read the /etc/shadow file may decide not to
           permit any access at all if the password field is empty.

           A password field which starts with a exclamation mark means that
           the password is locked. The remaining characters on the line
           represent the password field before the password was locked.


```

---

### Post by mahlerchiro on 2012-04-28
> **drs305 said:**
> In nautilus as root, SHIFT-DELETE the Trash folder, otherwise it may simply be deleted to..... Trash.
```

gksudo nautilus /root/.local/share/

```

The Trash folder will be regenerated the next time root deletes something.

I have a link in my signature line about finding and deleting trash from your system.

this worked it is from 
drs305
:guitar:

---

### Post by overdrank on 2012-04-28
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

