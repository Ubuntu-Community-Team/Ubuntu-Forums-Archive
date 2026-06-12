---
title: "Permission denied as root user on file"
date: 2008-09-11
forum: General Help
---

### Post by markprice on 2008-09-11
Somehow one of the files that has been rsync to a backup server lost all of its permissions and owners and have been set to question marks. I have tried chmod, chown, and rm to the file but keep getting permission denied as the root user. Here is what the file looks like in the directory listing:

?????????? ? ?       ?      ?                ? 05green.jpg

Any ideas how to fix this?

---

### Post by ilrudie on 2008-09-11
what is the output from ls -li?

Does it have an inode number?

You could also try sudo rm -f 05green.jpg

Maybe try shred?

> 05green.jpg (as root) might at least zero the file out so its not taking up (much)space while you are finding the ultimate solution.

---

### Post by WRDN on 2008-09-11
When you entered the chown/ chmod commands, did you enter "sudo" before the command? Otherwise, the "Permission Denied" message will appear.

---

### Post by bingoUV on 2008-09-11
Seems like a screwed up filesystem. Can you read the file? do
```

eog 05green.jpg

```

You have rsynced the files. Have you run the above commands e.g. rm, ls etc. at the source of the files (original computer which held the files), or at the target (that is the backup server)?

---

### Post by markprice on 2008-09-11
The output of ls -li is:
54645 ?????????? ? ?       ?      ?                ? 05green.jpg

I have the root account enabled so I've been using root to perform the commands. I tried shred and it is still giving me permission denied. The source file is fine but rsync won't overwrite or delete the file anymore due to the messed up permissions. All the other images in the directory are fine as well. Rsync might have got cut off or something in the middle of transferring the file messing up the permissions. But now I can't do any commands to the file at this point.

Thanks

---

### Post by ilrudie on 2008-09-11
I don't know.  You can look up how to delete an inode.  You could try running this as root:  
```
find . -inum 54645 - exec rm -f {} \;
```

Many deletion by inode posts will say to do something like that but that's mostly for things with unprintable characters.  There should be a way to actually delete the inode though im just not sure what it is.

---

### Post by bodhi.zazen on 2008-09-11
The file itself is some how corrupt. Best way I know to fix it is to boot a live CD, mount your partition, and delete the file from there.

---

### Post by EmanresuusernamE on 2008-09-11
It could be a Unicode error.  Did that file's name contain only ASCII characters, or where there some characters from another language in it?

---

### Post by mb_webguy on 2008-09-11
> **bodhi.zazen said:**
> The file itself is some how corrupt. Best way I know to fix it is to boot a live CD, mount your partition, and delete the file from there.

+1

I've had this exact problem before, and this is how I fixed it.

---

### Post by doas777 on 2008-09-11
> **mb_webguy said:**
> +1

I've had this exact problem before, and this is how I fixed it.

I'm just curious, why that works, while rm -f fails? mount options?  i'm prolly displaying my n00bitude....

---

### Post by forger on 2008-09-11
I agree that the file somehow got corrupt. Probably using the live cd and mounting the partition and deleting the file will fix it

Otherwise, post the output of this command:
```
sudo lsattr 05green.jpg
```

---

### Post by pbhj on 2008-09-11
> **markprice said:**
> The source file is fine but rsync won't overwrite or delete the file anymore due to the messed up permissions. 

Have you tried "unlink"-ing the file as root?

When the link count is zero the filesystem can retrieve the file space, so don't worry about having file junk that's not cleaned up. This has worked for me with files that I couldn't delete in teh past ... but I don't recall ever having the exact symptoms you have.

:)

---

### Post by bodhi.zazen on 2008-09-11
> **doas777 said:**
> I'm just curious, why that works, while rm -f fails? mount options?  i'm prolly displaying my n00bitude....

I have already told you more then I know on this subject :twisted:

---

