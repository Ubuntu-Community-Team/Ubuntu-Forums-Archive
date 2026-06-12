---
title: "Unmount/Eject CD Help"
date: 2008-11-17
forum: General Help
---

### Post by nuffy on 2008-11-17
I have been somewhat frustrated by having to unmount then eject a cd as root using 'sudo nautilus' then right click the cdrom, then click eject... 

I would love to do this as a user....cos when I use a cd for any purpose.... I am but a lowly user...and not root.

I have searched the forums and found this how to....
[https://help.ubuntu.com/community/EjectCDLauncher](https://help.ubuntu.com/community/EjectCDLauncher)
..... but alas I have not been successful in making it work for me.

Should this work?  Or is there an easier way to eject a cd each and every time I want to??

---

### Post by eternalnewbee on 2008-11-17
Can't you just right-click and unmount/eject?

---

### Post by bigbrovar on 2008-11-17
add your self to the cdrom group .. that happens something ..
```
sudo  adduser yourunsername cdrom
```
eg my username is nile 
```
sudo adduser nile cdrom
```

---

### Post by nuffy on 2008-11-17
eternalnewbee   
nope.... no can do!  Get error message - you do not have privileges to unmount what ever media is in the cdrom

and, bigbrovar
tried this.... same problem as above.

---

### Post by Marius Derekus on 2008-11-17
Can't you use the sudo nautilus command, then right-click the cdrom, then click properties and change the permissions.

---

### Post by nuffy on 2008-11-18
MD....Nope cannot change permissions either as I am not root!!!  

Now when I try to unmount/eject I get this message...'only root can unmount dev/cdrom0 from media/cdrom'  What the??

This has to be the most frustrating experience I have had with Ubuntu in the short time I have been using it....so much so it may drive me back to Windows!!!  Arrrgghhhh!

Is there some way of granting myself the same 'power' as root across all aspects of Ubuntu??

---

### Post by easoukenka on 2008-11-18
sudo gedit /etc/group

locate cdrom here is my entry
cdrom:x:24:haldaemon,eric,mythtv,amyloveseric

add yourself to the cdrom then ctrl alt backspace to restart the x server now give it a try.

worst case scenario just add a shortcut to your desktop gksudo umount /media/(whateveryourcdromis)    

I am not really sure why you are trying to unmount your cdrom though can you even do this in windows?

---

### Post by nuffy on 2008-11-18
Thanx easoukenka.... I had success with gksudo eject /media/cdrom0

All I wanted to do was to eject the cd when I had finished with it..

Thanx to all who replied....

---

### Post by bigbrovar on 2008-11-18
ok try this go to **System/Administration/User and Groups**
click **Unlock** and provide your password.NOW click your **user name** and on the side plane select **properties**. this would open a new window . in this new window go to user **privileges tap** and check **use CD-ROM drives **

[IMG]http://farm4.static.flickr.com/3195/3040851946_96333f65d7_o.jpg[/IMG]

---

### Post by nuffy on 2008-11-18
Thanx bigbrovar... I have the CD-ROM dve option checked but I still can't eject the cd using this method! The only way is by using gksudo eject /media/cdrom0.

Frustrating....

---

### Post by nuffy on 2008-11-22
Still no joy! 

I upgraded to Ubuntu 8.10 thinking this may help.... but alas it did not!!!

I have a shortcut gksudo umount /media/cdrom0 for now... this doesn't work every time now!!  Shish!!

Is there information available what the default settings should be for all users?  Basically I want to reset all permissions back to default to see if this helps.

Or failing this, can I have the same permissions as root each and every time I login to Ubuntu?

---

### Post by jmontelius on 2008-11-28
Hi, I've had/have the same problem mostly when the cdrom has been opened by wine. Try this, in /etc/fstab one specifies how drivers should be mounted at boot time. There is one line there for the cdrom thatt probably looks something like this:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

try changing the option "user" to "users", check this for more in fstab

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

I'm not sure that this solves the problem but it's wort a try.

---

### Post by nuffy on 2008-11-29
Hey jmontelius!

Thanks for the advise!! It works a treat!!

---

