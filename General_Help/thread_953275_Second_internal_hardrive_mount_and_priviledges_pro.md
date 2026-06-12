---
title: "Second internal hardrive mount and priviledges problem"
date: 2008-10-20
forum: General Help
---

### Post by plaxeb on 2008-10-20
I have little problem here: I can't get install or delete anything on my second internal hard drive. I dont know why is it because I added to myself rights at beginning with commands
> 
sudo mkdir /media/harty
sudo chgrp lassinni /media/harty
sudo chmod 774 /media/harty

Might cause be /etc/fstab file?
I added there this kind of text on end:
> 
# /dev/sda6
UUID=My UUID /media/harty ext3 nouser,relatime,atime,auto,rw,dev,exec


---

### Post by ajmorris on 2008-10-20
hi there,
 
do you mean even as root? If it is only your normal user, change the 'nouser' option, to 'user'  Also, what format is the second hard drive?
 
 
AJ

---

### Post by plaxeb on 2008-10-20
ext3 is what i applied to gparted when i formated it last time, and it seems that change to user did not help in fstab
and how you check it on terminal(I am beginner here, i swiched to ubuntu last friday )? in graphical characteristics information priviledges section root is both owner and group owner and it has as owner( but as marked gray and not that i can change it there (claims i dont have rights because i am not owner) ) it should have priviledges to create and destroy and as group owner nothing

---

### Post by jerome1232 on 2008-10-20
Try making those changes recursive,

```
sudo chgrp -R /media/harty
sudo chmod -R 774 /media/harty
```

Also if you just added this group to your user you have to log out then log back in for the group to take affect.

---

### Post by plaxeb on 2008-10-20
It insulted with chgrp that there should be some operand after /media/harty but it allowed to me to add chmod rights to myself now :D
thanks for help!

---

### Post by jerome1232 on 2008-10-20
Oh lol I was tired, replace [group] with the group you wanted.

```
chgrp -R [group] /media/harty
```

---

