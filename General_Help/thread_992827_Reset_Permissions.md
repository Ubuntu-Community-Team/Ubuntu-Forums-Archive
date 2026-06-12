---
title: "Reset Permissions"
date: 2008-11-25
forum: General Help
---

### Post by anjanesh on 2008-11-25
I dont know how the file permissions are set for files and directories but something got screwed up.

Im running apache httpd 2.2 server and have a directory /home/username/www/somesite which runs in the browser as localhost/username/somesite
I did a chown -R username:username somesite 

**sudo chmod 777 -R somesite** works. But how do I set it to **chmod 666 -R somesite** ?
I got **chmod: cannot access `somesite/js': Permission denied** I had to do sudo to get it to work.
But now the website is not accessible ! I get a Forbidden message !

How can I reset the permissions ?  Thanks

---

### Post by cmnorton on 2008-11-25
You're probably getting this error, because you used sudo chmod -R for the first command and eliminated sudo for the second command.

Who owns any of the files/directories under the /home/username tree? If there is more than one owner, deal with each owner first, by applying commands on each separate sub-tree under /home/username. 

If all files and directories belong to username, then sudo chown -R username:username /home/username. Then you should be able to set permissions without sudo.

However, you are doing this without regard to directories, and they must have +x permission, if you want to cd to them. I would use the find command using -type f and -type d to segment the kinds of entries, files or directories, on which you want to set permissions.

---

### Post by natrik on 2008-11-25
Just to be clear, it seems the last commenter was assuming you were dealing with **/home** but it looks to me like you're dealing only with /home/user/www/**somesite**  

In that case, it should be okay to leave the ownership alone, you don't mention affecting it at all. 

Mode 666 takes away execute permissions from all users, including owner.  For directories, execute means the ability to enter the directory.

For web directories, you PROBABLY don't want them or the files in them to be world-writable.  You also probably don't want any of the files in them to be executable, but the directories should be readable and executable (writable only by owner).  

These commands will accomplish that:

first set the affected directory, if it's not okay now.
[FONT="Courier New"]**sudo chmod 755 /home/user/www/site**[/FONT]

Then deal with subdirectories
[FONT="Courier New"]**sudo find /home/user/www/site -type d -exec chmod 755 {} \;**[/FONT]

Then fix the files, so that the owner has read / write permissions, and everyone else has read-only access.  sudo should not be necessary if you are the owner of the files:
[FONT="Courier New"]**find /home/user/www/site -type f -exec chmod 644 {} \;**[/FONT]

If group members need write access, it would be 775 for directories and 664 for files.

If there are any other permissions that need to be changed (cgi, or any other scripts) address those individually.

Hope this helps!  

Read up on 'find' ... it's a very powerful program.  Tricky though.  The **{}** gets replaced by the current filename.  The **\;** is needed at the end of an -exec argument.  Depending on what shell you're using, you might need to use **\{}\;**  instead of **{}\;** in the examples above.  I use tcsh, which you can access by typing '**tcsh**'

-- Nate

EDIT: forgot to show you the results when I did this myself to make sure:

```
ichigo@zangetsu:~/test> ls -lR somesite/
somesite/:
total 12K
drwxr-xr-x 3 ichigo ichigo 4.0K 2008-11-25 08:17 ./
drwxr-xr-x 3 ichigo ichigo 4.0K 2008-11-25 08:45 ../
drwxr-xr-x 2 ichigo ichigo 4.0K 2008-11-25 08:17 arf/
-rw-r--r-- 1 ichigo ichigo    0 2008-11-25 08:16 asd
-rw-r--r-- 1 ichigo ichigo    0 2008-11-25 08:16 asdsadf
-rw-r--r-- 1 ichigo ichigo    0 2008-11-25 08:16 dsdaf
-rw-r--r-- 1 ichigo ichigo    0 2008-11-25 08:16 oiuas
-rw-r--r-- 1 ichigo ichigo    0 2008-11-25 08:16 oiuop
-rw-r--r-- 1 ichigo ichigo    0 2008-11-25 08:16 qwer

somesite/arf:
total 8.0K
drwxr-xr-x 2 ichigo ichigo 4.0K 2008-11-25 08:17 ./
drwxr-xr-x 3 ichigo ichigo 4.0K 2008-11-25 08:17 ../
-rw-r--r-- 1 ichigo ichigo    0 2008-11-25 08:17 098ayfe
-rw-r--r-- 1 ichigo ichigo    0 2008-11-25 08:17 89aywe098
-rw-r--r-- 1 ichigo ichigo    0 2008-11-25 08:17 987
-rw-r--r-- 1 ichigo ichigo    0 2008-11-25 08:17 9a8seya
-rw-r--r-- 1 ichigo ichigo    0 2008-11-25 08:17 9qr
-rw-r--r-- 1 ichigo ichigo    0 2008-11-25 08:17 asd
```

---

### Post by anjanesh on 2008-11-25
> Who owns any of the files/directories under the /home/username tree? If there is more than one owner, deal with each owner first, by applying commands on each separate sub-tree under /home/username.
Just me.

> Mode 666 takes away execute permissions from all users, including owner. For directories, execute means the ability to enter the directory.
Wow. Thanks. I was wondering what on earth does execute mean to folders !

I got a couple of these
**chmod: changing permissions of `./site/var/cache/.........': Operation not permitted**
This is because there are 2 directories that need to be writable - one is site/var which contains cache etc and the other is media which contains images uploaded via the browser.
So should I do 
sudo chmod 777 -R media
sudo chmod 777 -R var

Im afraid of using sudo because it may change ownership ?
While uploading to a FTP linux server, do permissions of the file/directories by any chance get sent too ?

---

