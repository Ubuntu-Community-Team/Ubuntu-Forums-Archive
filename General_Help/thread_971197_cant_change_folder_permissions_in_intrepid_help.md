---
title: "cant change folder permissions in intrepid help"
date: 2008-11-04
forum: General Help
---

### Post by Naegling23 on 2008-11-04
Im trying to mount a flash card in kubuntu intrepid running kde4.  sudo chmod777 does not change anything!  changing the permissions in dolphin or konqueor, once again do nothing!

whats going on, can anyone help me out...very frustrated, I cant transfer anything without using the sudo cp command...very very tedious.

---

### Post by Altay_H on 2008-11-04
To change the permissions of a folder use:
```
sudo chmod -R 777 FOLDERNAME
```
Where FOLDERNAME is the name of the folder of which you're attempting to change the permissions. Make sure you've navigated to the directory containing the folder using cd.

NOTE: The -R will cause it to change all of the permissions of the files contained within the folder as well. If you don't want that, just remove the -R.

---

### Post by taurus on 2008-11-04
Chmod won't work with ntfs & fat32 filesystems.  You need to mount it with the right permissions to be able to write to it as a regular user.  

However, it doesn't automount it for you (with right permissions) when you plug it in?

---

### Post by Naegling23 on 2008-11-04
chmod -R is not working either.

I used to change the mount permissions and all of that in the disk and filesystem directory under system settings....its not there in kde4 though.

---

### Post by mc4man on 2008-11-05
I've only spent a few hrs. with kde 4.1 and things are different to say the least. 
Why don't you open dolphin and from there you can get a r. click -> properties -> permissions. Look at either a file or folder or go root -> media -> your flash drive.
I'm not having any issues with flash drives, ownership comes up user -> me, group -> root.
If i come across how to view 'mount options' ala ubuntu I'll post.

---

### Post by Naegling23 on 2008-11-05
I had tried right clicking on the folder and changing the permissions, everything changes, i click apply, wait a few seconds, no error messages, then go back into properties, and my permissions were the same as before.

I did try to transfer some files again, this time I had success.  dolphin is still telling me I dont have write permissions, but it seems to be working, btw, I have no idea how or why its working, but it is....so immediate crisis averted.  I wont close this thread, because im still looking for something to replace the drive and filesystem manager under kde4.  I still have a seldom used ntfs hard drive that is currently not mounting, but the error message seems to tell me to look into ntfs issues....I was too frustrated to start that quest last night...thanks for the help everyone, maybe it was chmod -R 777 or another suggestion, I tried them all.

does anyone know why dolphin would list file permissions as not supporting write, but I would be able to write files?  it doesnt seem like that should be working (though...dummy me, I should have checked permissions in the terminal...oh well, im at work now)

---

