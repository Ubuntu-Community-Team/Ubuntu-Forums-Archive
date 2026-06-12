---
title: "ssh remote read/write permissions"
date: 2008-08-12
forum: General Help
---

### Post by ele_mugv on 2008-08-12
Hi, i am using an ssh editor on a remote machine to update files on a server in a lan. The only problem is that i can't edit nd save the files on any other directory except the home directory..same applies with filezilla ssh sessions. How do i configure my ssh client to be able to write files to /var/www/... on the server box?

---

### Post by y@w on 2008-08-12
What are the permissions on the files you're trying to edit and what user are you logging in as?

---

### Post by ele_mugv on 2008-08-12
Wat's the command for checking file permissions? I'm logged on as a super user

---

### Post by iaculallad on 2008-08-12
> **ele_mugv said:**
> Wat's the command for checking file permissions? I'm logged on as a super user

On your terminal:

```
ls -l
```

---

### Post by ele_mugv on 2008-08-12
Thanks mate.
The containing directory-www has drwxr-xr-x permission nd belongs to root.
The html files all hav -rw-r--r-- permissions nd belong to root as well.

i guess it's worth mentioning that my ssh login is done by another user and not root

---

### Post by ilrudie on 2008-08-13
You will have to "become" root to edit these files.  You can prefix your edit command with sudo to gain root privileges or you can su - if sudo is not enabled on this box.  With sudo you need to be in the sudoers file and with su - you need to know the root password.  If you are sshed into an Ubuntu server sudo will be your only option as root is disabled by default.  These are the best options as changing the file permissions on those folders/files may make your website less secure.

---

### Post by y@w on 2008-08-13
A better practice would be to change the ownership of the files to something that's usable rather than logging in as root every time you want to change a file on your web server. You can use chown to change the ownership. I'm assuming your web server is going to run as www-data, so you'll want something like:

```
chown -R www-data:user /var/www
```

You can certainly sudo every time if you like, but it's generally not good practice to be forced to escalate your privileges to change non-system files..

Another option would be to just make the files writeable to everyone:

```
chmod -R go+w /var/www
```

Again, probably not best practice, but that's an option as well.

---

