---
title: "[SOLVED] NTFS files missing when browsed from Ubuntu"
date: 2008-07-12
forum: General Help
---

### Post by Lami6895 on 2008-07-12
Hi,
First post on the forum for me ! :)
Just installed Ubuntu 8.04 after partitioning my disk (after defrag from windows XP Home).
When browsing my NTFS partition from Linux, some folders do not appear in Nautilus, whereas they still exist when I look at them from Windows XP...
Anybody has an idea about how to solve it ?
Have a nice week-end !

---

### Post by coffeecat on 2008-07-12
> **Lami6895 said:**
> When browsing my NTFS partition from Linux, some folders do not appear in Nautilus, whereas they still exist when I look at them from Windows XP...

I find it the other way round. As far as I can see Linux shows your directory tree in NTFS exactly as it is. I should imagine Windows alters the shown tree structure either to protect the system from the user or for some nefarious Microsoft reason.

Can you post some screenshots of browser windows in Ubuntu and Windows to show what you mean?

**Edit**, sorry - should have added: to do a complete screenshot press the PrtSc key. For a shot of the selected window, Alt+PrtSc. Can't remember the Windows shortcuts. Probably the same.

---

### Post by boblemur on 2008-07-12
very strange...

did so are you saying that, you had it installed and then after you did defrag the files disappeared? 

or was it like this since you installed ubuntu...

how have u mounted the ntfs? in fstab? or manualy?

---

### Post by Lami6895 on 2008-07-12
Thanks for these replies !

Attached are the screenshots from windows and from Linux of the same folder (with items sorted by names, I made sure this is not only a sorting problem ! you can see a 117 vs 166 number of items).

I actually did not have to do any manipulation to mount my NTFS partition : it appeared from my first start of Ubuntu in the "places" menu.

Thanks a lot !

[ATTACH]77434[/ATTACH]

[ATTACH]77435[/ATTACH]

---

### Post by boblemur on 2008-07-12
i dono if its just a strange coincidence but none of the folder in the ubuntu picture have special symbols such as the e with the accent


i dont know what this could mean, or how it could effect the visability of the files

maybe the file browser is not displaying some kind of errors...

open terminal (applications > accessories > terminal)

change to the folder...

cd /Documents and settings.../my pics/my images/

and then run this...

```
 ls -l -a | wc -l

```

looks odd so ill explain( ls -l -a, will display the contence of the folder... in a list and show hidden files, and wc -l is "wordcount" and will count lines)

let me know if that say 117 still

---

### Post by coffeecat on 2008-07-12
This is very interesting. I've got involved in another thread [here]("http://ubuntuforums.org/showthread.php?t=857189") with a very similar problem. This time it's Nautilus not showing folders that Gnome-Commander shows.

I'm beginning to wonder if it's a Nautilus bug.

Can I suggest two things? Install Gnome-commander and/or thunar and/or konqueror and/or the file manager of your choice and see what that shows. The other is to post on that thread. I think you and the OP of that one need to compare notes. :)

---

### Post by Lami6895 on 2008-07-12
Again thanks for the answer,
Says 120

Tried to change a folder's name from windows: now it appears in Nautilus!

Thanks again, maybe it is because I choosed to install Linux in English whereas I am a French in France ?

---

### Post by Lami6895 on 2008-07-12
Just added Gnome Commander, which doesn't show the folders either :

[ATTACH]77471[/ATTACH]

---

### Post by boblemur on 2008-07-12
my guess as to where you go from here would be either... in windows...

write urself a lil script to rename the folders (can be a pain) and replace É with E etc... but it would be a long process...

or you can try this...

right click the ntfs drive and go unmount or if that dosent work

```
sudo umount /dev/sda?
```

then remount it ( for example to /mnt/windows):

```
sudo mount /dev/sda? /mnt/windows -t ntfs -r -o iocharset=utf8
```

this may solve your problem. let me know :)

ohh.. and note: you may have problems copying these files ( but you can convert the names .. but then windows may not like them so that will still be an issue..)

---

### Post by Lami6895 on 2008-07-23
Just used your answers to solve the issue in two steps :
1. I installed French as a supported language on my system
2. I changed the /etc/fstab as hereunder (after making a backup of it!)

/dev/sda2 /media/Rothmans ntfs-3g defaults,locale=fr_FR.utf8 0 0
# /dev/sda2 /media/Rothmans ntfs-3g defaults,locale=C 0 0

It now works fine !

Thanks again !

---

