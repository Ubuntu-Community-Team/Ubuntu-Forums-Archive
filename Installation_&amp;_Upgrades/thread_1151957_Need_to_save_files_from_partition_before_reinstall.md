---
title: "Need to save files from partition before reinstalling"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by LegendaryOdin on 2009-05-07
An upgrade locked me out of the x server and in case nothing can work through this problem, I need to know how to save my files from the original disk. It will load if I insert the Live CD but only through the Try without changing anything on your computer option. A very nice person who has been helping me with this issue has suggested I need to the partition on the disk and copy the files to a network share or burn the files to a CD/DVD. Can anyone give me specific instructions on how to do this? Please and thanks.

---

### Post by cholericfun on 2009-05-07
from the LiveCD you should be able to access you HD/ files.
also the burner should be up and running..
just drag and drop really

---

### Post by bixejo on 2009-05-07
Probably there is some other more nice way to do this, but what I'll tell you will work:

[LIST=1]
[*]Boot with your CD or USB drive and get into live session. This won't give you direct access to your HD, so you'll need to continue with the following.
[*]You need to manually mount your HD filesystem(s). First, identify your HD filesystem(s) that should be mounted. You may run System --> Administration --> Partition Editor (be [COLOR=Red]**very careful**[/COLOR] what you do over there.)
[*]In Partition Editor, see the list of filesystems that are currently in your HD. Your HD will probably be called **sda** or **[COLOR=Black]hda[/COLOR]**. Select this drive and have a look at your filesystems. One of them (perhaps more) will be the one(s) where your data are stored.
[*]Let's assume that your Ubuntu installation has two filesystems, one for root and the other for /home, and these are **/dev/sda2** and **/dev/sda3**.
[*]Open a terminal: Applications --> Accesories --> Terminal
[*]Create as many directories as filesystems you are about to mount. Following with our assumptions, type in the terminal:
```

sudo mkdir /media/drive1
sudo mkdir /media/drive2

```
[*]Mount your filesystems. In the therminal:
```

sudo mount /dev/sda2 /media/drive1
sudo mount /dev/sda3 /media/drive2

```
[*]At this point you'll probably see in your desktop two (or whatever the number of filesystems is) icons that will give you direct access to your HD if you double click on them. If not, you may still point your file browser (like Nautilus) to directories /media/drive1, /media/drive1, etc.
[*]Now you have access to your HD data. Use any CD/DVD burner to backup it all to disks, or send your data to some network server if you have access to the Internet. Note that in your live session you'll be able to install all the needed software to burn CD/DVD if it's not already available in your live session. It won't keep on installed if you reboot, of course, but who cares? :)
[/LIST]
Hope this helps.
Regards,

---

### Post by LegendaryOdin on 2009-05-07
Lol well it took me a few times and some combo breakers but I finally got it. Thanks for all your help!

---

