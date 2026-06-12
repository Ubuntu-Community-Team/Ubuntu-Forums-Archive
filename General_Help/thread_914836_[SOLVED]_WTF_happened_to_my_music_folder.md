---
title: "[SOLVED] WTF happened to my music folder??"
date: 2008-09-09
forum: General Help
---

### Post by MaindotC on 2008-09-09
I'm trying to access my music folder and I found this:
[[IMG]http://img58.imageshack.us/img58/7160/aasdfic8.th.jpg[/IMG]](http://img58.imageshack.us/my.php?image=aasdfic8.jpg)

Wtf is going on ??  I don't recall anything happening that would warrant a change to the folder.  Is this an attack from the RIAA or MediaDefender or some crap like that because it's music that I bought!

---

### Post by adam_kimber on 2008-09-09
It appears you are trying to chmod a directory whilst in it. The way the chmod and many other Linux commands work is by being below the directory you wish to work on. In this case 

Say for instance you need to change permissions on the "Bloat" directory that resides in the "System" directory. You need to be in the "System" directory to change the permissions on the "Bloat" one? Make sense? :D 

```
cd ~/Desktop
chmod 777 Music 
```

should do the trick. Unless of course you have a recursive directory structure of ~/Desktop/Music/Music <-- and this is where the Music is stored. Then my bad! 

PS Why are you changing permissions to such an insecure setting?

---

### Post by MaindotC on 2008-09-09
It's not really a concern about changing permissions of the folder - it's that my folder permissions, owner, and group have been replaced by question marks!

---

### Post by Rocket2DMn on 2008-09-09
If the folder is linked to another filesystem, you may need to make sure it is functioning normally.  If it is on the same filesystem as root or /home, you may need to fsck the partition.

---

### Post by Archmage on 2008-09-09
> **strAlan said:**
> It's not really a concern about changing permissions of the folder - it's that my folder permissions, owner, and group have been replaced by question marks!

Than maybe this needs to be done:

```
cd ~/Desktop
sudo chmod 777 Music 
```

Kindly note that you may be asked for your password to make sudo work.

---

### Post by MaindotC on 2008-09-09
Archmage - THE FILES ARE GONE and the question marks are now appearing.  I just tried to change the permissions just in case that was the issue.  It's not - the files are gone and as you can see the directory properties have all been replaced with question marks.

I appreciate you replying and I don't appreciate the "kindly note that..." sarcastic remark.

---

### Post by /etc/init.d/ on 2008-09-09
Check dmesg after you get the I/O error and look for any messages that might indicate hardware failure.  Otherwise it is file system corruption.  Image the drive then run fsck on the partition (you don't want to risk fsck making things worse).

---

### Post by adam_kimber on 2008-09-09
> **Rocket2DMn said:**
> If the folder is linked to another filesystem, you may need to make sure it is functioning normally.  If it is on the same filesystem as root or /home, you may need to fsck the partition.

I did a test to see if the error could have been caused by a removed symbolic link as previously suggested. The theory goes "if the target link is removed then is should throw up errors and question marks". This is however the result of a symbolic link listing after ls -l (target has been removed, shows up black with red text in my terminal). 

Still correct permissions, no question marks. 

```
lrwxrwxrwx 1 adam adam       5 2008-09-09 18:25 Music -> temp/

```

Is the Music a separate disk/partition and the fact it is not mounted? Or mounted incorrectly for some reason?

---

### Post by Rocket2DMn on 2008-09-09
OK, we need some more information then, please post the outputs of these commands (I know, there are quite a few, I'm trying to cover as much as I can in one pass):
```
cd ~/Desktop
ls -al
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
ls -l temp/
ls -l Music/
```

---

### Post by MaindotC on 2008-09-09
Sorry but I had to move on.  It was just taking too much time and frustration.  I reinstalled Debian and I guess my music is gone now.

---

### Post by /etc/init.d/ on 2008-09-10
> **strAlan said:**
> Sorry but I had to move on.  It was just taking too much time and frustration.  I reinstalled Debian and I guess my music is gone now.
Did you even try fsck'ing the partition as suggested in the 3rd post of the thread?  If it were just minor inode corruption, that would have probably fixed it. 

Hope you don't give up on other issues in life so easily (especially when others were trying to help you.)

And yes, your music is almost certainly gone now.

---

