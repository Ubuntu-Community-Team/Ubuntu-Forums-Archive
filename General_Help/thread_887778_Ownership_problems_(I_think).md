---
title: "Ownership problems (I think)"
date: 2008-08-12
forum: General Help
---

### Post by MartinvDK on 2008-08-12
Hi all.
I have installed netbeans. The thing is, it's installed on an ntfs (windows) partition (to save space on the linux partition). Now, when I try to build a project in netbeans, it comes up with an exception (in netbeans, not in my program), telling me it has not got the permissions to run the file stdouterr.sh in the netbeans directory (on the ntfs drive). So it looks like I have to give netbeans permissions to run that file - or what? The file has got rwxrwxrwx and is owned by root - what is wrong then?

Martin

---

### Post by theyranos on 2008-08-12
Is the "exec" option set on that partition in /etc/fstab?

---

### Post by MartinvDK on 2008-08-12
The entry in fstab for my ntfs drive looks like this:
/dev/sda1       /media/Storage          ntfs    user 0 0
I remember fighting with this entry to make it work, using all those options, and it never worked. But I can try to put in exec after user (right?), and see what will happen...
Thanks for the quick answer :)

Martin

---

### Post by theyranos on 2008-08-12
Don't thank me unless I'm actually right about this being the problem :P

Yes, you should just be able to put it after user, as
```

/dev/sda1 /media/Storage ntfs user,exec 0 0

```

---

### Post by MartinvDK on 2008-08-12
Thanks man, it worked. Great!

---

