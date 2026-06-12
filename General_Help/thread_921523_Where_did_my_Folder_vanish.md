---
title: "Where did my Folder vanish?"
date: 2008-09-16
forum: General Help
---

### Post by redenex on 2008-09-16
I have lost all my songs, that was in a folder which was titled My JukeBox.

It was working fine, I was playing a few songs too, but suddenly the folder seems to have vanished. And no, it is not hidden either. Any help please? I have lost a whole 25 GB of songs, and ironically when I run Disk Usage Analyser, it seems that the space of that vanished folder is taken into consideration as well. 

(I found a similar thread but I can't post in that and neither was there any guidance):popcorn:

---

### Post by russo.mic on 2008-09-16
Well, did you have the folder in a seprate partition or something like that?  What music player were you using?  Is it possible that the music player 'organized' your music?

---

### Post by redenex on 2008-09-17
Well, I just have ONE partition, and no the music player haven't "rearranged" anything. I am using Totem Movie Player.

I am still not able to locate the entire folder, though the disk space is shown as used. Any help please?

---

### Post by gareththomasnz on 2010-02-09
A folder just vanished on my desktop.

When I create a new folder with the same name it wont let me and says there is allready a folder with that name.

When I search it cant find the folder.

There is no preceding full stop so its not invisible in that way so the view hidden files checkbox does nothing.

I need to access the folder but cant even find it.

---

### Post by john newbuntu on 2010-02-09
Check your trash.  If it is not there and if you can remember the name of any one file (say "nevermind"), open up a terminal (applications->accessories->terminal) and type:
sudo find / -name "*nevermind*" -print
This will take a while to chug along.  If you find it, you will know the folder where it is located.  I hope it is not in a different filesystem, in which case, you will have to see if that filesystem is mounted.

---

