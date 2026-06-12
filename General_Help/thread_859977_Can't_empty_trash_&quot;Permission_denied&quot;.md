---
title: "Can't empty trash: &quot;Permission denied&quot;"
date: 2008-07-15
forum: General Help
---

### Post by Shunsuke_01 on 2008-07-15
There is a folder in my trash called "beacon", and it doesn't get deleted when I try to empty it. If I try to delete it manually, it says "permission denied".

Is there a code I can use to force contents of the trash to be removed? 


Any help would be appreciated.

---

### Post by iaculallad on 2008-07-15
> **Shunsuke_01 said:**
> There is a folder in my trash called "beacon", and it doesn't get deleted when I try to empty it. If I try to delete it manually, it says "permission denied".

Is there a code I can use to force contents of the trash to be removed? 


Any help would be appreciated.

Terminal way:

```
sudo rm -rf /home/your_user_name/.local/share/Trash/*
```

or doing it the graphical way:

```
gksudo nautilus
```

and try to browse the trash folder: /home/your_user_name/.local/share/Trash, and delete the file/folder that can't be deleted.

---

### Post by explosive on 2008-07-15
Open up a Terminal and type these 2 commands.

cd .Trash
sudo rm -r beacon

You will have to enter your password to delete the folder.

---

### Post by Shunsuke_01 on 2008-07-15
> **iaculallad said:**
> Terminal way:

```
sudo rm -rf /home/your_user_name/.local/share/Trash/*
```

or doing it the graphical way:

```
gksudo nautilus
```

and try to browse the trash folder: /home/your_user_name/.local/share/Trash, and delete the file/folder that can't be deleted.

Thank you so much! I searched google for some help, but none of it seemed to do the trick.

Great, it's empty now. :)

Thanks again for the help.

---

### Post by andreaso on 2008-10-23
Thanks guys. It really helped me. But why is the permission denied ?:confused:

---

### Post by sirhalos on 2008-10-23
You most likely opened up a nautilus as a super user and didn't realize it then deleted a folder or file. Which in that case put the file or folder in question in your trash bin but was a super user file which is why your normal user couldn't delete it.

---

### Post by jamesisin on 2008-12-19
I too am curious about why this should happen.  I'm afraid I have to reject sirhalos' answer for the following reasons:

1. I believe root has no trash and when root performs "Move to Trash" it hard-deletes (if not, where is root's Trash folder?).
2. How does one "accidentally" open Nautilus as a super-user?
3. I checked the file permissions on the files in my Trash and confirmed they were owner-assigned to and marked as deletable by my normal username.

In my case, prior to finding this solution I attempted to remove the stuck folder back to my Desktop (drag and drop).  Since removing the folder from the Trash was blocked (permission denied) Nautilus made a copy of that folder on the Desktop.  I then moved that to Trash and it also would not be removed from Trash.  Empty Trash ignored both of these identical folders (presumably permission denied errors are dropped silently by that command).

Any other ideas as to what may have caused this?

---

### Post by jamesisin on 2008-12-19
Shunsuke_01 - Thanks.

---

### Post by Francewhoa on 2009-08-13
Same here. Thanks iaculallad #2 work for me.

---

### Post by malachi1990 on 2009-08-14
The times I've seen permission mess ups like this happen when you delete files that have been moved off of a flash drive and stored onto your hdd.

---

### Post by Neezer on 2009-11-10
So I am having a problem doing this....I have been deleting duplicate songs in my music file, and I got rid of 9+ GB of stuff....now I'm trying to empty my recycle bin and it isn't working....

when I do:
```

sudo rm -rf /home/your_user_name/.local/share/Trash/*

```

I just get another command prompt, but my trash bin isn't emptied...

```

nathan@lappy:~$ sudo rm -rf /home/your_user_name/.local/share/Trash/*
nathan@lappy:~$ 

```

but my trash icon still says that there are 1955 items in it.

What gives??

when I navigated to /.local/share/Trash there weren't any files in it.

---

### Post by wojox on 2009-11-10
Try this, delete home trash and root trash

```

sudo rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
sudo rm -rf /root/.local/share/Trash/*/** &> /dev/null

```

---

### Post by Neezer on 2009-11-10
I guess I forgot this tidbit of info,

the music is on an external hdd. I unmounted it, and the trash bin said it was empty. Then when I plug it back in, I have a trash bin with 1955 items in it agian.

Trying to clear the root trash doesn't do the trick either.

Edit:

I found a .Trash file on my external drive that if full of files....I'm sure that is it, but when I try 
```

sudo rm *

```

in that directory, it tells me that all the files are read only and I can't use rm to get rid of them.

---

### Post by sisco311 on 2009-11-10
> **Neezer said:**
> So I am having a problem doing this....I have been deleting duplicate songs in my music file, and I got rid of 9+ GB of stuff....now I'm trying to empty my recycle bin and it isn't working....

when I do:
```

sudo rm -rf /home/your_user_name/.local/share/Trash/*

```

I just get another command prompt, but my trash bin isn't emptied...

```

nathan@lappy:~$ sudo rm -rf /home/your_user_name/.local/share/Trash/*
nathan@lappy:~$ 

```

but my trash icon still says that there are 1955 items in it.

What gives??

when I navigated to /.local/share/Trash there weren't any files in it.

You have to replace your_user_name with your login name or:
```
sudo rm -rf ~/.local/share/Trash/*
```

You can right click on the file and select Properties to get the location of the file. Then open nautilus as root:
```
gksu nautilus
```
navigate to the location, select the files and press Shift+Delete to remove the files.

---

### Post by sisco311 on 2009-11-10
> **Neezer said:**
> I guess I forgot this tidbit of info,

the music is on an external hdd. I unmounted it, and the trash bin said it was empty. Then when I plug it back in, I have a trash bin with 1955 items in it agian.

Trying to clear the root trash doesn't do the trick either.

Look for a .Trash-<uid> directory in the root of the partition:
```
ls -al /media/mountpoint/.Trash*
```
assuming that the partition is mounted in /media/mountpoint/

---

### Post by sisco311 on 2009-11-10
> **Neezer said:**
> 
Edit:

I found a .Trash file on my external drive that if full of files....I'm sure that is it, but when I try 
```

sudo rm *

```

in that directory, it tells me that all the files are read only and I can't use rm to get rid of them.

How did you mount the partition?

What's the output of:
```
mount
```

---

### Post by wojox on 2009-11-10
Ah, what filesystem is it? 

Press Control-H, look for the hidden .Trash or .Trash-1000 folders, and hard-delete them (press Shift-Delete and not just Delete).

---

### Post by Neezer on 2009-11-10
I didn't do anything to mount it...I just plugged it into the USB port and it comes up.

It is mounted under /media/My Passport


I fount the the .Trash on My Passport.

I tried removing it with
```

nathan@lappy:/media/My Passport$ sudo rmdir .Trash-1000
rmdir: failed to remove `.Trash-1000': Read-only file system
nathan@lappy:/media/My Passport$ 

```

as you can see, it didn't work. 

I have tried multiple times to use gksudo nautilus and gksu nautilus to delete the folder with no luck.

This sure is a head scratcher for me, and I appreciate all of your help.

---

### Post by sisco311 on 2009-11-10
try to remount it rw:
```
sudo mount -o remount,rw /media/My\ Passport
```

---

### Post by Neezer on 2009-11-10
> **wojox said:**
> Ah, what filesystem is it? 

Press Control-H, look for the hidden .Trash or .Trash-1000 folders, and hard-delete them (press Shift-Delete and not just Delete).

Shift+Delete isn't working....I don't get any results.

I keep getting these messages telling me there are read-only files in the folder and that is why I can't delete them. Is there a way I can make it so they aren't read only?

---

### Post by Neezer on 2009-11-10
> **sisco311 said:**
> try to remount it rw:
```
sudo mount -o remount,rw /media/My\ Passport
```

I don't think it is working. I'm still getting all kinds of errors on it.

When I go to /media/My Passport I tried this to check

```

nathan@lappy:/media/My Passport$ ls -al
.stuff
.stuff
.stuff
drwx------   5 nathan root     32768 2009-11-09 01:47 .Trash-1000
.more stuff

```

So I should be able to do it, but it isn't working....tried 

```

sudo rm -R .Trash-1000

```
Got read only errors again.

---

### Post by Neezer on 2009-11-10
Well,

I got it fixed, but not the Ubuntu way....I just took it out and plugged into windows XP. highlighted the .Trash-1000 file and pressed delete...It asked me something about if I really wanted to delete the read only files. I said yes, and away they went!

It is odd cause I had been doing this for a few days now and never had any problems emptying it in the past. Could the side of it have anything to do with it? it was over 9GB.

Anyways, Thanks for all the quick help. I really appreciate it.

---

