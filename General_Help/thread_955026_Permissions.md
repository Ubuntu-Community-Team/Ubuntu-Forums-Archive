---
title: "Permissions"
date: 2008-10-21
forum: General Help
---

### Post by Silenus on 2008-10-21
I'm using samba from 8.04 to windows xp, on the xp box it shows my shared folders, but it says does not have privileges to access or permission to open the shared folders on the windows machines.

I can't figure out how to get around this as I've done everything in every guide I have found.

---

### Post by bodhi.zazen on 2008-10-21
On the server your usere has to have permissions on the share. Normally you share a directory in your home directory for example.

You then right click on the directory -> share -> allow others to read and write.

You will not be able to share say system files when your user does not have permission ro rw.

If you recently installed samba, you need to log off and back in the server.

---

### Post by Silenus on 2008-10-21
I don't have the option most guides talk about (share, instead I have sharing options).
 I set it to allow read and write, and it still says no permission.


Just tried again and it says does not  have privelages contact system admin. And at the bottom "path was not found".

---

### Post by spiderbatdad on 2008-10-21
try setting this sharing after launching the file browser as root:```
gksu nautilus
```then browse to the folder you wish to share, and right click...etc

---

### Post by Silenus on 2008-10-21
No changes, still says no permission.

---

### Post by sea_monkey987 on 2008-10-21
please post the output of
```
cat /etc/samba/smb.conf | grep guest
```
and
```
cat /var/lib/samba/usershares/Georgedocuments
```

---

### Post by Silenus on 2008-10-21
> george@george-desktop:~$ cat /etc/samba/smb.conf | grep guest
;   guest account = nobody
map to guest = bad user
   usershare allow guests = yes
   guest ok = yes
   guest ok = yes
   guest ok = yes
   guest ok = yes
;   guest ok = yes
guest = ok
guest = yes
george@george-desktop:~$ 

.

---

### Post by eldragon on 2008-10-21
modify the line
**;guest account = nobody**
to
**guest account = your_username**
save, restart samba with
```

$ sudo /etc/init.d/samba restart

```

and you should be done (remember to uncomment, aka: remove the semi colon)

---

### Post by Silenus on 2008-10-21
It worked, thanks. :D

---

### Post by sea_monkey987 on 2008-10-21
actually, you want to just uncomment the line.  change it to
```

guest account = nobody

```

EDIT: i see that it has worked for you anyway.  so disregard this post.  i'll leave it here for others' reference.

---

### Post by Silenus on 2008-10-21
It worked with or with what he had said, so I guess either way.

---

### Post by bodhi.zazen on 2008-10-21
Solved: 
 
Woot ... :guitar: 
 
Please mark this thread as solved, it saves the time of many volunteers looking to help  
[indent]... and users looking for solutions.[/indent] 
 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by sea_monkey987 on 2008-10-21
yeah.  but i just want to point out that making your own username as the guest account means that whenever you share a folder in your home directory, everyone will be able to write to it, regardless of whether or not you check the box "Allow other people to write to this folder" in Share Options.

---

### Post by eldragon on 2008-10-21
> **sea_monkey987 said:**
> yeah.  but i just want to point out that making your own username as the guest account means that whenever you share a folder in your home directory, everyone will be able to write to it, regardless of whether or not you check the box "Allow other people to write to this folder" in Share Options.

i thought thats what he was going for.

---

### Post by sea_monkey987 on 2008-10-21
> **eldragon said:**
> i thought thats what he was going for.
he wanted his xp box to write to it, yes.  however, since he had checked the box "Allow other people to write to this folder," nautilus had changed his folder's permissions to 777 so any user on his local ubuntu machine could write to the folder, including the user named "nobody."

---

