---
title: "Restricting a guest user's directories"
date: 2008-08-05
forum: General Help
---

### Post by nzk on 2008-08-05
I made a guest user so that other people can use my computer. Everything is fine, except it can access other home directories and the file system without any boundaries, and it can see sensitive information. This is both in nautilus and in the command line.

How would I fix this problem? I basically want to make the guest account be no different than if I just bought a computer and loaded Ubuntu on it. By that I mean I'd want it to be completely spotless and brand new.

---

### Post by nzk on 2008-08-05
Bump?

---

### Post by bingoUV on 2008-08-05
By sensitive information if you mean stuff in other home directories, you can change their permissions to be not visible to strangers (in this case, the guest user is a stranger). Open nautilus, and right click on the sensitive directory that is visible to guest. Change the permission of others to be nil. Click "Apply permissions to enclosed files".

If command line is your thing, do
```

chmod -R o-rwx <directory path>

```

Attach sudo to the above command if there is trouble.


BUT, be very cautious in changing permissions of files outside the home directories. Most of it will work fine, but for some files, it might break the system so that it may not even boot. You will then have to painfully recover the system. Confirm before changing the permissions of files outside home.

---

### Post by nzk on 2008-08-05
> **bingoUV said:**
> By sensitive information if you mean stuff in other home directories, you can change their permissions to be not visible to strangers (in this case, the guest user is a stranger). Open nautilus, and right click on the sensitive directory that is visible to guest. Change the permission of others to be nil. Click "Apply permissions to enclosed files".

If command line is your thing, do
```

chmod -R o-rwx <directory path>

```

Attach sudo to the above command if there is trouble.


BUT, be very cautious in changing permissions of files outside the home directories. Most of it will work fine, but for some files, it might break the system so that it may not even boot. You will then have to painfully recover the system. Confirm before changing the permissions of files outside home.

Alright, so I just set folder access of "Others" to "None".

Edit: I logged into the guest account and the folders are still visible, but they are not accessible. That's acceptable, but I'd prefer if they were invisible. Is there any way to do that?

---

### Post by bingoUV on 2008-08-05
To make a folder invisible, you have to make its parent folder have no permissions for others. If there is a directory structure 
/1/2/3/4

```

chmod o-rwx /1/2

```

will make /1/2 visible, but /1/2/3 will be invisible. /1/2/3/4 will also be invisible.

---

### Post by nzk on 2008-08-05
> **bingoUV said:**
> To make a folder invisible, you have to make its parent folder have no permissions for others. If there is a directory structure 
/1/2/3/4

```

chmod o-rwx /1/2

```

will make /1/2 visible, but /1/2/3 will be invisible. /1/2/3/4 will also be invisible.

Well, I guess that would make it impossible, seeing as access to the guest's home folder is required. That would mean I'd need to make /home/ restricted for others.

---

### Post by bingoUV on 2008-08-05
The "others" here means users other than the owner/group of the file/directory. Since root owns /home, others mean everybody except root. So restricting others on /home will make you unable to login. 

In short, don't tinker outside /home/<user> directories if you are not sure what you are doing. Outside /home/<user> includes /home itself.

---

### Post by nzk on 2008-08-05
> **bingoUV said:**
> The "others" here means users other than the owner/group of the file/directory. Since root owns /home, others mean everybody except root. So restricting others on /home will make you unable to login. 

In short, don't tinker outside /home/<user> directories if you are not sure what you are doing. Outside /home/<user> includes /home itself.

I changed it so that I am the owner of /home/. Well, I tried restricting access to the guest before I saw your message, and you can guess what happened.

I guess I'll have to keep it like this, then.

---

