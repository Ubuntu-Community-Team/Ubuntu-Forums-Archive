---
title: "I need a bigger Trash Can"
date: 2008-09-17
forum: General Help
---

### Post by kooldino on 2008-09-17
I have multiple drives mounted, however, my OS drive is the smallest.  

The problem I run into is that my Trash can fills frequently, since (I'm guessing) all of my Trash is going to some central place on (another guess) my OS partition.

Short of replacing my OS drive with a bigger disk, what can I do to resolve this?

---

### Post by houbysoft.xf.cz on 2008-09-17
You can resize your OS partition with a tool like gparted, for example, it's in the repos.

---

### Post by drs305 on 2008-09-17
For an interim solution on how to delete all your trash (and you can find out where it is), refer to the link in my signature line - ah heck, here it is:

[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by kooldino on 2008-09-17
> **houbysoft.xf.cz said:**
> You can resize your OS partition with a tool like gparted, for example, it's in the repos.


As stated above, that's not an option.

---

### Post by lswb on 2008-09-18
On Hardy the default trash file is /home/username/.local/share/Trash. In earlier versions of ubuntu IIRC it was /home/username/.Trash 

IF I had that problem I would try something along these lines. Use at your own risk:

Create a directory on a larger partition somewhere where you have rwx access. If you want to save what is currently in the trash (Doesn't that sound wierd) copy all the files from .Trash to the new directory. Then delete the trash file from your home directory and create a symlink that points to the directory on the larger drive, using the name ./local/share/Trash for hardy or (again IIRC) .Trash for older versions of ubuntu.

The sequence of commands would be something like this in a terminal

mkdir /otherpartition/BiggerTrash
cp -r .local/share/Trash/* /otherpartition/BiggerTrash
mv .local/share/Trash TrashBackup
ln -s /otherpartition/BiggerTrash .local/share/Trash

If it works OK you can rm Trashbackup, if not, remove the link with
rm .local/share/Trash, then 

mv TrashBackup .local/share/Trash

---

### Post by y@w on 2008-09-18
Yeah, you can either symlink your trash directory to another partition (what was explained above) or move your home directory to that other partition. If you copy-paste the output from 'df -h' we can most likely see which partition the trash is mounted on.

---

### Post by Mister.Vash on 2008-09-18
Have you checked your other drives for a .Trash-userid file
cd mountpount
ls -al
does it show something similar?
drwx------   4 user group        4096 2008-06-29 16:56 .Trash-1000

The is what ubuntu creates by default on other volumes.  If they are not there, you can add them using sudo, then set the owner and the group to match your account and the name of the folder to be .Trash-your user id

to get your userid, just type in echo #UID
If this account is the first one you set up on the system that UID will probably be 1000 so the folder would be .Trash-1000

I've checked my mounts, and on the ones that have the folder, the database remains on the original drive until the trash is emptied

---

