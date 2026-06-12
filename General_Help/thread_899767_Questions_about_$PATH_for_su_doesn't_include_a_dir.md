---
title: "Questions about $PATH for su doesn't include a directory the user has in their $PATH"
date: 2008-08-24
forum: General Help
---

### Post by maxbaroi on 2008-08-24
I want to add a certain directory to the $PATH for a certain user, so I add

```
export PATH=/var/lib/gems/1.8/bin:$PATH
```

at the end of /home/[user]/.bashrc, and everything works fine until I try to
enter a command that resides in /var/lib/gems/... as root. This makes sense since /var/lib/gems/... isn't in the $PATH for root. 

I added the same exact line to the end of /etc/profile, and deleted it from /home/[user]/.bashrc and everything works fine, but it feels like a kludge. 

Now every user has that in their $PATH, even the ones that don't need it. It doesn't seem right. And if I had a lot of users with their own specific needs it seems that /etc/profile would soon become a jumbled mess of "export PATH..." commands.

Is there any way that I can get su to "take on" the $PATH of the user. 
That is, if user bob has /usr/someapp/ in his $PATH that's not present in the $PATH of root, then if I do somethingt as root while bob is logged in, then /usr/someapp is listed when I type
```
bob&desktop:#echo $PATH
```

Any help would be appreciated

---

### Post by maxbaroi on 2008-08-24
SCrath that, what I did DIDN'T work. So can anyone help me on that front too?

---

### Post by unutbu on 2008-08-24
It would be a great big security hole if you configured root to take on a normal user's PATH. For example, suppose a malicious user wrote a program called "ls", which was the same as /bin/ls, except that it gave the normal user a setuid root shell?

A safer alternative is to edit /root/.profile and add the path to root's PATH. Then eliminate the edit from /etc/profile so it does not affect other users.

---

### Post by maxbaroi on 2008-08-24
Thanks for the reply, that makes  alot of sense, but I'm still having the same problem. 

Here's my /root/.profile. I removed "export PATH=/var..." from every other file it was in.

```
# ~/.profile: executed by Bourne-compatible login shells.

if [ -f ~/.bashrc ]; then
  . ~/.bashrc
fi

mesg n

export PATH=/var/lib/gems/1.8/bin:$PATH
```

But when I enter echo $PATH in the shell, the directory doesn't show up.

---

### Post by bodhi.zazen on 2008-08-24
If you have an application you wish multiple users to access, best if :

1. The executable is owned by root.root (root is the owner and group)

2. Permissions 755.

3. make a link in a directory in the path.

```
sudo chown root.root /home/bob/bin/application
chmod 755 /home/bob/bin/application
sudo ln -s /home/bob/bin/application /usr/local/bin/application
```

The only draw back is /home/bob/bin must also have permissions of 755

---

### Post by pauper on 2008-08-24
.profile is being read at login time only. Read "man bash", search for
/INVOCATION paragraph.

```
$USER@$HOSTNAME:~$ sudo -i
root@$HOSTNAME:~# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
root@$HOSTNAME:~# echo "
> export PATH=/usr/local/Trolltech/Qt-4.3.4/bin:$PATH" >>/root/.profile
root@$HOSTNAME:~# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
root@$HOSTNAME:~# logout
$USER@$HOSTNAME:~$ sudo -i
root@$HOSTNAME:~# echo $PATH
/usr/local/Trolltech/Qt-4.3.4/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
root@$HOSTNAME:~# logout
$USER@$HOSTNAME:~$ 
```

---

### Post by mssever on 2008-08-24
You can use su - instead of plain su. Better yet, just use sudo; it's more secure and there really isn't much reason to log in as root anymore.

---

