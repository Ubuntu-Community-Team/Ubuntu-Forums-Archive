---
title: "File system check fail after using gParted"
date: 2009-06-21
forum: Hardware
---

### Post by troll1602 on 2009-06-21
First off I am running Ubuntu 8.10 with my '/' and '/home' directories on separate partitions .

What I did was use gParted to reformat an old ntfs partition into an ext3. Once I tried to boot back into ubuntu the file system check failed.

I followed the advice from this post:
[http://ubuntuforums.org/showthread.php?t=364216](http://ubuntuforums.org/showthread.php?t=364216)
but once I changed the UUID's I got the following error on login:

> 
Your home directory is listed as: '/home/ryan' but it does not appear to exist. Do you  want to log in with the /(root) directory as your home directory? it is unlikely anything will work unless you use a failsafe session.


I selected 'Yes' and then got the following error:
> 
User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.


Then I get a few more error messages and only the default background is displayed, nothing else.

let me know if more info is needed and thanks for any help.

---

### Post by troll1602 on 2009-06-21
Just a quick update on some things I have tried.

I logged in under a failsafe terminal session. I was thinking that this might be a permissions issue, because once I was logged in I would try to change directories to '/home' and I would get a permission denied message. So, I did the following:
```

$sudo chown -R username:username /home

```
After this this I could 'cd' in '/home', but all that was there was a 'lost+found' folder, with nothing in it.

So, I then thought that perhaps that partition wasn't being mounted, and tried:
```

$sudo mount -t ext3 /dev/sda5 /mnt/temphome 

```
which only shows the empty 'lost+found' folder.

Now I am all out of ideas :-). If anyone knows of anyway I could just view my home directory, that would be awesome. I have no problem doing a fresh install as long as I could backup a few important files.

---

### Post by troll1602 on 2009-06-21
Well, I didn't really solve the problem, but I kind of fixed it.

First thing I did was reformat the new ext3 partition back into ntfs. So i was back to my original setup: 3 partitions, 1 for root, 1 for home, and 1 for ntfs.

With the fix of changing the UUID's I could then log back in just fine. However, my home directory was completely wiped and look just as it does on a fresh install.

Finally, I used Foremost to recover a bunch of files on the home partition.

Moral of the story? Backup your important stuff often! Don't reformat partitions, unless you know what you are doing. But, I thought I knew what I was doing, so I would recommend to never reformat partitions when the other partitions are important!

---

### Post by Eeqmcsq on 2009-06-22
That's weird. I can't see how formatting your ntfs partition could have affected your home partition.

---

