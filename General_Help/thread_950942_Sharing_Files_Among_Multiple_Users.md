---
title: "Sharing Files Among Multiple Users"
date: 2008-10-17
forum: General Help
---

### Post by leehach on 2008-10-17
I want to share files on a home computer, primarily music and photos.  Using Google, I found the following two web pages describing how to share files among multiple users:

[http://linuxhelp.blogspot.com/2005/05/sharing-directories-among-several.html](http://linuxhelp.blogspot.com/2005/05/sharing-directories-among-several.html)
[http://mandrivausers.org/index.php?showtopic=36426&st=0&p=273358&#entry273358](http://mandrivausers.org/index.php?showtopic=36426&st=0&p=273358&#entry273358)

I followed the instructions which means I created a share group, added my users to the group, made the group the owner of the shared Pictures directory, and set the sticky bit so that all new files are also owned by the share group.

The problem is, even though the new files have share as the owning group, group privileges are set to read-only.  I would like them to be set to read-write so that any user in the share group could edit or delete the files.

Questions:
1) Is there any way to do have group get read-write for new files? or
2) Is there a better way to share files among users so that different non-owners (group and other) have full control?

Thanks for your input,
--Lee

---

### Post by bodhi.zazen on 2008-10-17
There is no simple solution. Your options are to change the "umask" in .bashrc, but this will affect all files you create and not just the shares.

Probably the easiest is to write a cron job that changes the permissions with some regularity. You can give your users the ability to run at script if needed via sudo.

---

### Post by seeker5528 on 2008-10-17
If they are not new files, but were instead copied from another directory, they may not get all the permissions automatically and may not even get set to the shared group when copied or moved into the shared directory.

Usually my solution is to open a terminal window and type:

sudo chmod -R g+rw */some/shared/directory*

: not exactly clear on this deletion flag (t option). I believe when it is set group members other than the owner can make changes to a file, but not delete it. Not sure how this shows up if you view the properties in the file manage either, if you wanted to clear that just to be sure then the command would look similar to:

sudo chmod -R g+rw,u-t */some/shared/directory*

: If the ownership needs to be changed use chown like so:

sudo chown -R :*shared_group /some/shared/directory* 

: be sure to note the ':' character before the group, the format is '*user:group*', if you leave the colon out it will change the user ownership instead of group ownership.

Oops forgot the path to the directory, corrected.

Later, Seeker

---

### Post by bodhi.zazen on 2008-10-17
> **seeker5528 said:**
> If they are not new files, but were instead copied from another directory, they may not get all the permissions automatically and may not even get set to the shared group when copied or moved into the shared directory.

Usually my solution is to open a terminal window and type:

sudo chmod -R g+rw */some/shared/directory*

: not exactly clear on this deletion flag (t option). I believe when it is set group members other than the owner can make changes to a file, but not delete it. Not sure how this shows up if you view the properties in the file manage either, if you wanted to clear that just to be sure then the command would look similar to:

sudo chmod -R g+rw,u-t */some/shared/directory*

: If the ownership needs to be changed use chown like so:

sudo chown -R :*shared_group*

: be sure to note the ':' character before the group, the format is '*user:group*', if you leave the colon out it will change the user ownership instead of group ownership.

Later, Seeker

. works as well and is easier to type, check it out :

```
sudo chown root.root test_file
```

---

### Post by seeker5528 on 2008-10-17
> **bodhi.zazen said:**
> . works as well and is easier to type, check it out :

```
sudo chown root.root test_file
```

If you only want root to be able to access the file. You're not logging on as ro-o-o-ot, a-a-are you? :razz:

I had to google for the 'root.root', and find something that says that usage is deprecated and will fail if the user or group name have an '.' character in them.

Later, Seeker

---

### Post by leehach on 2008-10-17
Thanks for the replies.  Bodhi.zazen (or anyone else), can you point me to more information on umask?  I found the man pages somewhat...opaque.  (Whereas chown, chmod, man pages were quite helpful.)

What would be the strategy for using umask?  Would it apply to all files for a user, or all files in a directory?  How would you implement it?

If I can't get this going with some combination of group permissions and umask, I'll probably fall back on the chmod -R cron job strategy.

Thanks,
--Lee

---

### Post by bodhi.zazen on 2008-10-17
> **leehach said:**
> Thanks for the replies.  Bodhi.zazen (or anyone else), can you point me to more information on umask?  I found the man pages somewhat...opaque.  (Whereas chown, chmod, man pages were quite helpful.)

What would be the strategy for using umask?  Would it apply to all files for a user, or all files in a directory?  How would you implement it?

If I can't get this going with some combination of group permissions and umask, I'll probably fall back on the chmod -R cron job strategy.

Thanks,
--Lee

Sure

[http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)

You have to set it per user and as I said it affects all files, so IMO it is easier to write a short script.

```
#!/bini/bash

chmod -R user.group /directory
```

Run it from chon (once an hour ?) and give any users that need access via sudo.

[http://kevin.vanzonneveld.net/techblog/article/schedule_tasks_on_linux_using_crontab/](http://kevin.vanzonneveld.net/techblog/article/schedule_tasks_on_linux_using_crontab/)

---

### Post by abrahamsmith on 2009-02-18
You need acls:
```
setfacl -m default:group:groupname:rwx dirname
```

---

