---
title: "automatic inherit file permissions ?"
date: 2008-10-09
forum: General Help
---

### Post by joeboentoe on 2008-10-09
My question is:

When I create a new file in a folder, why does it not get the file permissions of the "parent" folder? How does Linux decides which rights a new created file or folder gets by default?

Been googling quite some time, but I don't find a good and clear explanation about how Linux handles this.

Thanks in advance.

---

### Post by defishguy on 2008-10-09
AFAIK!

Windows permissions are first based on a security template that evolves gradually based on the permissions of the parent folder and any administrative changes made along the way.  The ACL (Access Control List) for a new folder is copied from the parent without much regard to the permissions (rights) of the user.

Linux permissions are at first based on the user and group context and continue to stay that way.  The only way that I know of to modify that behavior is to use the group id bit.  Setting the group id will only effect files within the parent not folders.  There might be a way to over ride this behavior but I do not know what it is.  To see what I mean, open a terminal,change the directory to ~/Desktop and type > sudo mkdir hello and you'll see a new folder that you can open but not write in because it is owned by root.  To take ownership of the new folder just type > sudo chown your.user.name:your.user.name nameofthefolderyoucreated and hit enter.  Now you'll be the owner of the folder and can delete it if you want.

If anyone else has insights or more knowledge than my basic understanding please post!  I'd love to learn more.

---

### Post by joeboentoe on 2008-10-10
Thanks for the reply, it makes things a little bit more clearer. But more detailed information is still welcome

---

### Post by hyper_ch on 2008-10-10
you can use umask to set different default permissions on the files.

---

### Post by suhaib1thariq on 2008-10-10
try
```
sudo chmod -R 755 <folder name>
```
to change permission to folder and all its content folders
this is i used to change permission to all its contents of a folder

---

### Post by joeboentoe on 2008-10-10
Ok thank you, I found some more information about umask:

UMASK is a Unix environment variable which automatically sets file permissions on newly created files.

The UMASK variable can be confusing to use, because it does work as a mask. In other words, you set the permissions that you do not want in the UMASK.

To calculate permissions which will result from specific UMASK values, subtract the UMASK from 666 for files and from 777 for directories.

If you want all files created with permissions of 666, set your UMASK to 000. Alternatively, if you want all files created with permissions of 000, set your UMASK to 666.

A reasonable value for UMASK is 022, which will cause files to be created with permissions of 644 (rw-r--r--) and directories to be created with permissions of 755 (rwxr-xr-x).

A more secure value for UMASK is 066, which will cause files to be created with permissions of 600 (rw-------) and directories to be created with permissions of 700 (rwx------).

UMASK is nomally defined in the .profile or .login user startup files.

---

### Post by stumac on 2008-10-10
The permissions applied to newly created file or folders is controlled by the variable umask. The umask variable is set in the startup scripts and by default is 022 but the user can change it if desired either by editing there start up or from the command line.
Being a mask the bits that are set to one mask out that particular permission.

For a fuller explanation try google umast.

Sorry I do not know the names of the scripts as I am an old UNIX user and have not yet come to grips with ubuntu's startup mechanisms which are different.

Have lots of fun learning all this.  It is well worth the effort.

Stumac

---

