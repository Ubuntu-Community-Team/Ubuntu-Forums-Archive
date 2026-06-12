---
title: "Changing ownership in Bulk"
date: 2005-12-03
forum: General Help
---

### Post by BabaFree on 2005-12-03
I copied several directories of files and they are now locked, which I'm assuming they were copied under root (Not sure why though...)  Is there a quick way to change ownership of an entire directory including subfolders and files?  Alternately, is there a way to copy them so that normal write access is not denied?
Thanks,
Baba

---

### Post by kosmic on 2005-12-03
in a terminal just do as root :
 
chown username:usergroup -R /directory
 
 
where :
 
username - The user that you want to be the owner
usergroup - The group you want the files belong
/directory - the directory where the files are
 
:)

---

### Post by BabaFree on 2005-12-03
Thanks for the help.  I did what you said and it didn't affect it, so I figured that I probably didn't have my username:usergroup right.  Anyways, I took what you said and tried ```
sudo chmod -R 777 /Directory
``` and it did the trick.  If you know, is 777 code ok or is giving files that kind of ownership a bad security risk or something like that?
Thanks again for your help.

---

### Post by flopsy on 2005-12-03
You can get your user name and group with id -un and id -gn respectively.

chmod 777 will allow any user account to modify your files. Which can be a security risk, depending on what the files are. To restore defualt permissions, do as kosmic explained (you might need to do sudo chown instead), then execute 
```
find ./ -type f -exec chmod 744 \{\} \;
```
in each directory.

chmod 755 /path/to/directory will restore default permissions to your directories.

---

### Post by kosmic on 2005-12-03
If you are concerned about security use 755 instead, because :
 
7 - gives write, read and execute permission
5 - gives read and execute permission
 
Simple way.
 
4 - is Read Permission
2 - is write Permission
1 - is execute Permission
 
so if you want a person to have write and read permission just do 4 + 2 = 6, in case you want read and execute permission is 4+1 = 5 it's very simple :)
 
Another thing you can have a look is the Sticky bit, but be very cautious with this option
 
EDIT : about the Chown command, lets supose your username is john and your group is also john
just do :
 
sudo chown john:john -R /home/john/myfilesdirectory/
 
This will change the owner of the files in myfilesdirectory to John and group John

---

