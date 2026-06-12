---
title: "Copy files created after a date?"
date: 2008-09-02
forum: General Help
---

### Post by G1ZmO65 on 2008-09-02
I was looking at the manual for cp but it doesn't do what I need apparently. 

I'd normally use xcopy in windows to copy only files/folders created after a certain date.

Can I do this in linux some way with cp? or another command?

Thanks,

---

### Post by Titan8990 on 2008-09-02
I would use the find command in combination with cp.

Something like this:


find / -atime +1 | cp * /whereiamcopyingto


Not saying this work specifically to your needs but a point in the right direction.

If you are doing this for backup purposes then you should look in to rsync.

---

### Post by LesFromWaldenVT on 2008-09-02
Check out 'find'.

find $HOME -mtime 0

finds all files changed (starting in $HOME and going down through all subdirectories of $HOME) in the last 24 hours. In general, '-mtime <n>' says find all files changed in the last n*24 hours (or n days).

Also, check out xargs ('man xargs'). It can be used in combination to do all sorts of repetitive tasks.

You can pass the results of a find to any program that accepts stdin. For example,

find $HOME -type d | grep -v '/\.'

will find all subdirectories of $HOME that do not start with '.'. The backslash before dot is required because otherwise it would stand for any character in grep searches.

Some of the power of Linux comes for the ability to pass data from one program to another thru the pipe '|'.

Have fun,
Les
BTW, 'find / -atime +1 | cp * /whereiamcopyingto' won't work because if one of the items found is a directory, the 'cp' will not copy or create it. Any files under the changed directory would be copied but if they had the same name as another file in 'whereiamcopyingto', they would overwrite the existing file there. Also, '/' would search the entire space (which you probably don't want).

---

### Post by ghostdog74 on 2008-09-02
> **Titan8990 said:**
> I would use the find command in combination with cp.

Something like this:


find / -atime +1 | cp * /whereiamcopyingto

not really. Have you tried this out?

---

### Post by Titan8990 on 2008-09-02
No I haven't. I was just trying to show that he can pipe cp through find to get the end result he is looking for. The user after me explained it much better.

---

### Post by ghostdog74 on 2008-09-02
> **Titan8990 said:**
> No I haven't. I was just trying to show that he can pipe cp through find to get the end result he is looking for. The user after me explained it much better.

you can do piping to cp, but through the use of xargs. If not, use the -exec or -execdir option of the find command.

---

### Post by G1ZmO65 on 2008-09-02
OK to explain what I'm trying to do :)

Copy the last 24 hours chat logs of our daughter into mums documents folder (both sets of docs reside on a windows 2k3 box and are mounted on the ubuntu box)

I have tried:

find /mnt/chatlogs/*.html -atime +1 | cp * /mnt/mumsdocs/kidschatlogs

however this copied the contents of the folder where the script resided /home/paul/scripts into /mnt/mumsdocs/kidschatlogs

now I know I can just copy all of them with the -u option in the cp command but my better half insists she only wants the last days logs gah! (besides it gives me something to practice linux with)

given that brief, I'm assuming that the cp * bit of the code is where the problem lies and is copying the wrong stuff to the target dir.

A bit later.....

Ok I kinda managed it: 
find /mnt/chatlogs/*.html -atime +1 | cp -p /mnt/chatlogs/*.html /mnt/mumsdocs/kidschatlogs

Now, the only problem with that is that it seems to reset the created and modified dates of the files. Any way to avoid that?

---

### Post by unutbu on 2008-09-02
```
find /mnt/chatlogs -type f -name "*.html" -mtime -1 -print0 | xargs -0 -I{} cp -a {} /mnt/mumsdocs/kidschatlogs
```

---

### Post by G1ZmO65 on 2008-09-02
Thanks unutbu, that appears to work fine apart from the timestamp issue though I'll need to get the manuals out to work out what it all means lol

Cheers

---

### Post by unutbu on 2008-09-02
What exactly is the timestamp issue?
Is the find command I posted grabbing too many or too few files? I might be able to fix it up, but it would help to know what the problem is first :)

---

### Post by G1ZmO65 on 2008-09-02
> **G1ZmO65 said:**
> 
Now, the only problem with that is that it seems to reset the created and modified dates of the files. Any way to avoid that?

It's just reset the timestamps to the time of copying the file. A minor issue really. I tried -p on the cp command to preserve the timestamps but no joy.

---

### Post by unutbu on 2008-09-02
Hm. cp -p (or -a) should have worked. Why kind of filesystem is /mnt/mumsdocs on? NTFS? Does this work any better?
```

cd /mnt/chatlogs
find . -type f -name "*.html" -mtime -1 -print | rsync -aL --files-from - /mnt/chatlogs /mnt/mumsdocs/kidschatlogs

```

---

### Post by G1ZmO65 on 2008-09-02
Yes it's NTFS. The new line produced the same result.
I'll have another go at it tomorrow. Have to crash due to early start in the morn. Thanks for your help :)

Paul

---

### Post by unutbu on 2008-09-04
G1ZmO65, I believe the problem is in the driver/kernel module/app that is being used to mount the NTFS filesystem. The problem is not in the "cp -p" command you are using to backup the data. (The 'find | cp' and 'find | rsync' commands all work with timestamps preserved in my tests on an ext3 filesystem).

Can you describe how you are mounting the NTFS partition?
Are you allowing the system (gnome-volume-manager) to automount the drive? or are you using /etc/fstab and issuing your own mount command? Are you using SAMBA?

Unfortunately, NTFS and SAMBA are two things I have zero experience with, so you might be best served starting a new thread to tackle this problem.

---

