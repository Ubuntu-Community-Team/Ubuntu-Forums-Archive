---
title: "Best way to share a folder across all users?"
date: 2008-11-03
forum: General Help
---

### Post by jondecker76 on 2008-11-03
What is the best way to share a folder and its subfolders to all users?

What I want, is one centralized location for our music and pictures collections. On top of that we use Moneydance for our finances, and I would like to be able to access the data file from anybody that is logged in.

So what i want is just a folder i can setup so that everybody has full read/write access to it. Furthering that, if "User A" creates a file in this shared folder, then "User B" amd "User C" can delete it if they want.

Also, where is the best place to put such a folder? (/home/share/ ?)

---

### Post by taurus on 2008-11-03
Perhaps create a new directory (not folder) called /share and give it worldwide read/write/executable permission.  Then, everybody can read and write (and execute) to it.

```
sudo mkdir /share
sudo chmod -R 777 /share
touch /share/test
```
The last command just to see if you can create an empty file in /share called test.

Or you can make it /home/share too.

---

### Post by jondecker76 on 2008-11-03
Thanks for your reply

I've already tried this approach, with limited success. I just tried it again per your instructions with the same results.

The problem is, I chmod the directory and all files within it (with the -R option). (I did it in /home/share)

Now I log in as "User A", and create a blank text file, and save it to /home/share.
Now I log in as "User B". I can see the text file I created as "User A", but it has a lock symbol on it...  I open it in gedit, and make a simple change by adding a line of text. Upon trying to save it, I get a permissions error.

What I need basically is a free-for-all directory where anyone can do anything with any file regardless of who created it.

Any other ideas?

thanks again

---

### Post by taurus on 2008-11-03
Can you post the output of this command from a terminal?

```
ls -la /home/share
```

---

### Post by mikewhatever on 2008-11-03
There is a brainstorm idea about this. 
[http://brainstorm.ubuntu.com/idea/2560/](http://brainstorm.ubuntu.com/idea/2560/)

Basically, the folder permissions are not applied to the files placed in it.

---

### Post by jondecker76 on 2008-11-03
Here is the output:
```

traceydecker82@studio-desktop:~$ ls -la /home/share
total 68
drwxrwxrwx 9 jondecker76    users           4096 2008-11-03 19:19 .
drwxr-xr-x 6 root           root            4096 2008-11-03 18:57 ..
drwxrwxrwx 4 jondecker76    jondecker76     4096 2008-07-07 05:47 Everio Upload
drwxrwxrwx 2 traceydecker82 traceydecker82  4096 2008-10-26 11:07 Incomplete
drwxrwxrwx 4 traceydecker82 traceydecker82  4096 2008-07-27 19:30 LMCE
drwxrwxrwx 3 traceydecker82 users           4096 2008-11-03 16:27 MoneyDance
drwxrwxrwx 2 jondecker76    users          36864 2008-10-26 11:06 My Music
drwxrwxrwx 7 jondecker76    users           4096 2008-07-05 15:07 MyPictures
drwxrwxrwx 2 jondecker76    users           4096 2008-07-04 17:07 MyVideos
traceydecker82@studio-desktop:~$ 


```

---

### Post by rhodry on 2008-11-03
This topic has been covered before in these forums. This thread,

[http://ubuntuforums.org/showthread.php?t=410335&page=2](http://ubuntuforums.org/showthread.php?t=410335&page=2)

using the post by 'rincewind_11' on Nov 7, 2007 about 'acl' also worked here for me.

Cheers,
Rhodry

---

### Post by amac777 on 2008-11-03
The way I solved this problem was the following 4 steps:

1. Change the umask in /etc/profile so that new files created by users will have write access granted to the group that owns the file:

```
sudo nano /etc/profile
```

change the last line so it looks like this:

```
umask 002
```

2. Make a new group (for example called "family") and include the usernames of your family members you want to be able to share the files in your shared directory in that group.

System->Administration->Users and Groups->[Manage Groups]->[Add group]

3. Make the shared directory, set it's group to be the name of the group you just created in step 2, give all users in the group full access to the directory, and tell it make all files created within that directory to the group of the directory:

```
sudo mkdir /sharedfolder
sudo chgrp family /sharedfolder
sudo chmod 775 /sharedfolder
sudo chmod g+s /sharedfolder
```

4. Logout and log back in to make the group changes take effect.

At this point, all users that you added to the family group should be able to create files in the shared folder, and also edit files created in the shared folder by other users in the family group.

Hope this helps.

---

### Post by ad_267 on 2008-11-03
The post above is exactly what I've done and works perfectly. There used to be a bug with nautilus not respecting the umask but this has been fixed.

---

### Post by jondecker76 on 2008-11-04
thanks guys, very excellent solutions!

---

