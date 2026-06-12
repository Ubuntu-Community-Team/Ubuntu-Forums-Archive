---
title: "Default permissions"
date: 2008-08-31
forum: General Help
---

### Post by Dreamerman on 2008-08-31
Hi to all. What would be the default permission for /home & all its sub-folders ? There are 3 groups under permissions - owner, group & others.

Thanks

---

### Post by mike2357 on 2008-08-31
I don't want to assume that my system and yours use the same default permissions, so I'd recommend that you create a new user and then take a look at what permissions are set to for that user's home directory.

Permissions of new files and directories that a user creates are set according to a value called "umask".  You can read about it by typing "man bash" and searching on "umask" by typing "/umask" (without the quotes).  An example of it is in the file /etc/profile, which is, to answer your question, the default umask for all users unless overridden.  You can read more particulars by installing the the "manpages-dev" package with synaptic, and then typing "man umask".  It's for use in a compiled program, but the particulars are the same.

---

### Post by Vivaldi Gloria on 2008-08-31
1) Anything from 700 to 755 is suitable for your home folder. But there may be folders or files in your home folder which need spesific permissions. For example ~/.ssh needs to be 700 and any file in it needs to be 600. 


2) Note that I prefer using octal values, for example 755 for rwx,r-x,r-x. See the posts after post #14 here:

[http://ubuntuforums.org/showthread.php?t=851377](http://ubuntuforums.org/showthread.php?t=851377)

to learn more.


3) I wrote about umask yesterday:

[http://ubuntuforums.org/showthread.php?p=5699099](http://ubuntuforums.org/showthread.php?p=5699099)

Umask controls the permissions of new files & folders. You can see the current status by giving the command

```
umask
```

in a terminal. To change the value of umask system wide put the new umask value in /etc/profile. To change it for a user I guess setting it in ~/.bash_profile will do it (create if it doesn't exist). See also "Session-wide environment variables" and "System-wide environment variables" here:

[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

---

### Post by Dreamerman on 2008-08-31
Thanks guys. Will read up on your suggestions.

Cheers

---

