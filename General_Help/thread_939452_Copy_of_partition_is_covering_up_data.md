---
title: "Copy of partition is covering up data"
date: 2008-10-05
forum: General Help
---

### Post by vfrdude04 on 2008-10-05
The other day i was backing up my computer to an external hard drive (250 gb western digital) that has two partition tables on it. I was using Gparted too and noticed that I could make a copy of my partitions, so i made one of my internal hard drive and directed the copy to go to the partition with the rest of my saved data. Bad idea. I was about 7 mins into it and figured it would take too long so i would do it later, so i canceled the operation. After that the partition wasn't accessible anymore, it said something like it was corrupted and inaccessible. After searching for hours for programs i found test disk, so i ran it on the corrupted partition hoping it would let me see the data. eventually it fixed all the problems on the partition and lets me access it now, but it's only showing the copied partition i made from my internal hard drive. Its not showing all the pictures and other things i had stored on it. It says (JM (G: total size 39.7) before i messed up it used to say (JM comp backup (G: total size 122gb). I was thinking when i made the copy it would store it in a folder alongside my other data, but i must have been mistaken. :( It makes me sick that i may have lost all my pictures. 

My question is if there is anyway to undo this and get all my pictures back b/c i dont think the copy process actually deleted all the other data it's just being greedy and not showing it? All the partitions are formatted in NTFS by the way. 

Thanks everyone.

---

### Post by caljohnsmith on 2008-10-06
You might still be able to use testdisk to recover your lost data partition. After starting testdisk, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", "N" for Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen so I can see that partitions testdisk finds.

Also, in case testdisk can't recover the partition, a really great program for recovering files is "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")", which is part of the testdisk package. As long as you haven't actually overwritten your data (the pictures you want to recover), photorec usually does a great job of finding files from deleted/corrupt partitions or HDDs. I would definitely try testdisk first though as recovering the partition would be alot more ideal than trying to individually recover all your lost files. Let me know how it goes. :)

---

### Post by vfrdude04 on 2008-10-07
I ran test disk a second time from my ubuntu partition instead of my windows xp. I took a a couple screen shots for you. If you can't view them I'll just copy the output for you to see. The partition that is labled [JM] is the one i am trying to uncover. It's only showing the properties of the copy i made to the external. There is a partition underneath the [JM] one, if you know what i am trying to say. I am going to play a little more and do some more specific searches under that partition. I really appreciate all your help. :)

[IMG]http://i89.photobucket.com/albums/k203/vfrdude04/Screenshot2.png[/IMG]


[IMG]http://i89.photobucket.com/albums/k203/vfrdude04/Screenshot-jkmillejmd420-laptop.png[/IMG]



[IMG]http://i89.photobucket.com/albums/k203/vfrdude04/Screenshot-jkmillejmd420-laptop-1.png[/IMG]

---

### Post by caljohnsmith on 2008-10-07
So what partitions were originally on that 250 GB HDD? What is that first partition at the beginning of the HDD? Testdisk says it is NTFS file system, but the label says it is linux. And I see what you mean about your JM partition; it is only ~40 GB and not 122 GB like your original. If testdisk can't recover your partition, you can most likely recover a lot of your files with that photorec program. Keep in mind though that photorec will need somewhere to write all the files it recovers, so you might need to find another big HDD to save the files to.

---

### Post by vfrdude04 on 2008-10-11
The partitions that were orginally on there were "Linux OS" and one I named "JM Comp Backup". I split the 250 gb in almost equal sized partitions a while back. I made the copy of "JM" (my internal hdd) and put it in "JM Comp Backup" and it's only showing the "JM" one. The partition at the begining is called "Linux OS" becuase thats the partiton I usually stored different linux iso's and files on before i installed Ubuntu and it was NTFS because I used it in Windows more often. I just never changed the name. I probably should. It does get confusing some times. I've been running multiple recovery tools on it and storing the data on a different a partition with plenty of data. I'll try that photorec, I know it will take a while though. Thanks again.

---

