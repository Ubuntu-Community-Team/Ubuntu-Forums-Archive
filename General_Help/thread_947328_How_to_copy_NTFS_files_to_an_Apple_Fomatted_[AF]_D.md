---
title: "How to copy NTFS files to an Apple Fomatted [AF] Drive?"
date: 2008-10-14
forum: General Help
---

### Post by vavalent on 2008-10-14
How to copy NTFS files to an Apple Fomatted [AF] Drive?
Is there any code for the terminal to copy the NTFS files to an AF Drive?
As if I drag and drop the file, it said "The Destination is Read-Only".
This is very urgent, please please help me immediately, thankyou!

---

### Post by justleen on 2008-10-14
you dont need any code, but you do need write permission on the drive..

the easiest way to do this is to give your user write permission to the disk
```
 sudo chown user:user /media/apple/disk 
```
where user is your username, and the path pointing to your mounted AF disk

---

### Post by vavalent on 2008-10-14
Thankyou for your reply, but sorry that I am a beginner of Ubuntu, I use the Ubuntu Live CD to boot Ubuntu (that means I didn't really install it), I don't really know the default name of the user account, can you tell me what's the name? thankyou

---

### Post by justleen on 2008-10-14
in a terminal, you can use the command "id" to find what user you are..

or "whoami"

---

### Post by vavalent on 2008-10-15
Woo! Thanks for your reply, really really thanks for your reply :)
I'll try it later (I'm not near my laptop)
Are you one of the members of Ubuntu Team? Cool!

---

### Post by vavalent on 2008-10-15
Hi justleen, I've tried it, but I still can't write files on the drive by using your method. Also I've tried another code which the Terminal taught me. Here are the codes:

```

ubuntu@ubuntu:~$ sudo chown ubuntu:ubuntu /media/LEOPARD
chown: changing ownership of `/media/LEOPARD': Read-only file system

```
```
ubuntu@ubuntu:~$ sudo chown -hR ubuntu:ubuntu /media/LEOPARD
chown: changing ownership of `/media/LEOPARD/.com.apple.timemachine.supported': Read-only file system
chown: changing ownership of `/media/LEOPARD/.HFS+ Private Directory Data\r': Read-only file system
chown: changing ownership of `/media/LEOPARD/.journal': Read-only file system
chown: changing ownership of `/media/LEOPARD/.journal_info_block': Read-only file system
chown: changing ownership of `/media/LEOPARD/.Trashes': Read-only file system
chown: changing ownership of `/media/LEOPARD': Read-only file system
```

Did I do anything wrong?

Let me repeat the problem: 
When I drag any file from any NTFS Drive to the Apple-Formatted Drive [LEOPARD], It said: "Error while copying to "LEOPARD". : The destination is read-only."

---

### Post by vavalent on 2008-10-16
Hey justleen, can you help me?

or for those people who are reading this post, please please help me to solve this problem! Thx!

---

