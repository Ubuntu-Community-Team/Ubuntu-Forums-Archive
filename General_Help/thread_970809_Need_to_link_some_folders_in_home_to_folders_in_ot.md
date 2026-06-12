---
title: "Need to link some folders in /home to folders in other partition"
date: 2008-11-04
forum: General Help
---

### Post by Wally_dog on 2008-11-04
First off, I HAVE looked through lots of threads on how to do this with a symlink, but for some reason, I can't get them to work right.

Basically I have a 50GB partition (sda4) with the label Data. That partition holds filed from "My Documents" in Windows XP. I want Ubuntu to stop using it's folders in /home to store things (such as Music, Pictures, etc.) and instead store it's files in the Windows folders (My Music, My Pictures, My Videos, etc.) The 50GB partition is formatted as NTFS, the Ubuntu partition ext3, and the Windows XP partition as NTFS. 

What I am trying to accomplish is a very easy way to be able to browse files between the two OS's by simply going into the 50GB drive (Data) to access whatever I need to. I do not want to move my /home folder to this drive. A diagram:

[Ubuntu operating files partition]-[Documents,movies,pics,etc.]-[Windows operating files partition]


I should probably also add that if I go to Places, then click Music or Pictures, I would like that to go the corresponding folder in the 50GB partition.

Thank you SO much for helping me, because this issue is really frustrating for me... 

-Wally

---

### Post by Wally_dog on 2008-11-04
Nevermind, I figured out how to do this. Moderators/Admins can delete this topic :)

---

### Post by bodhi.zazen on 2008-11-04
> **Wally_dog said:**
> Nevermind, I figured out how to do this. Moderators/Admins can delete this topic :)

In general we do not do that. Instead post your solution to help others :)

I think you have two options

ln -s

and 

mount --bind

---

### Post by Wally_dog on 2008-11-06
Oh well anyway, what I ended up doing was this:

In the Windows Partition, press and hold the middle-mouse button and drag the folder you want to link to to the Ubuntu partition (in my case, the HOME folder). 

Now you'll have the folder link, but not really any integration into the Places menu. Delete the Pictures, Videos, Documents, etc. folders in the HOME folder, and then drag all the folder links you want to be in the Places menu to the very bottom section on the left in Nautilus. Now they'll appear in the Places menu.

Enjoy :)

---

