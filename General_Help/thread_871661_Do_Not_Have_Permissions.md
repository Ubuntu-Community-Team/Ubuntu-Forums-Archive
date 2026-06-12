---
title: "Do Not Have Permissions"
date: 2008-07-27
forum: General Help
---

### Post by Paul Earland on 2008-07-27
Hello.
Have two work partitions on my Hard Drive. Work 1 I have had for a long time, work 2 is a recent addition (it is where my old XP was). When I try to move stuff from work 1 to work 2 I get the following message. Error while copying. Folder cannot be copied because you do not have permissions to create it in the Destination. How do i get these Permissions?
Thanks.
Paul

---

### Post by knutschr on 2008-07-27
Start the file manager with gksu in terminal.
(Sorry. Edited before I saw answer.
You are perfectly right, northern lights.)

---

### Post by northern lights on 2008-07-27
> **knutschr said:**
> Start the file manager with sudo in terminal.

_Never_ run graphical apps with 'sudo'. Use 'gksu' in gnome/xfce and 'kdesu' in KDE.

If you want to open directories as root, please use ```
gksu nautilus /path/to/directory
```

> **Paul Earland said:**
> How do i get these Permissions?
As for the actual problem, opening 'work2' as superuser should not be necessary. It's not like that's systemfiles. Run ```
chown -R USER /media/work2
```to give you permission. USER obviously needs to be replaced by your username and you might also want to check whether it's really 'work2' in /media.

---

### Post by CryptSphinx on 2008-07-27
well, if your general user is 'bob' 
and the location of your work partition is

/home/bob/work1

the command would be

chown -R bob:bob /home/bob/work

this breaks down as [change ownership] [-recursive] [bob as owner ,etc]  [the location of the directory]

this changes all the permissions to the main user

alternatively

if using ubuntu us gksu natilus /kubuntu kdesu konqueror

this will give you temporary root control within the window 

==be really carefull with this, you could do a lot of damage to your system as you now have unlimited power==

then navigate to wherever your folder is (work 2) right click to change permissions and set them as you see fit

hope that helps 

==by the time i finished typing this two other users had replied :) ==

---

### Post by Paul Earland on 2008-07-27
> **northern lights said:**
> _Never_ run graphical apps with 'sudo'. Use 'gksu' in gnome/xfce and 'kdesu' in KDE.

If you want to open directories as root, please use ```
gksu nautilus /path/to/directory
```


As for the actual problem, opening 'work2' as superuser should not be necessary. It's not like that's systemfiles. Run ```
chown -R USER /media/work2
```to give you permission. USER obviously needs to be replaced by your username and you might also want to check whether it's really 'work2' in /media.

Regarding the work 2/media comment. Perhaps I have done something wrong here. I erased XP which left me with an empty partition, which I just renamed as work 2, perhaps I should have done more than just re naming it?
Paul

---

### Post by northern lights on 2008-07-27
> **Paul Earland said:**
> I erased XP which left me with an empty partition, which I just renamed as work 2, perhaps I should have done more than just re naming it?
If the partition hosted XP before, it should be formatted as ntfs and thus readable (writable also) in Ubuntu out of the box.

What I asked you to do is navigate to '/media/' and check whether it's really called work2. Alternatively, just run 'chown -R USER /media/work2/' - if /media/work2/ does not exist, it won't solve your problem, but this command also can't screw anything up, so no danger in trial&error here.

---

