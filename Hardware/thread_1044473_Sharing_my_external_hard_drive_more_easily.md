---
title: "Sharing my external hard drive more easily"
date: 2009-01-19
forum: Hardware
---

### Post by wyatt23 on 2009-01-19
i am currently running 8.10 and i use an external harddrive.  i leave it constantly connected to the system and it is there upon boot.

my system put it at mount point /media/STORAGE.  this hasn't really been a problem, but i am now setting up samba and ftp. for the moment, i give myself access to "/". i can get to "/home/wyatt" and get my files or i can go to "/media/STORAGE" to get my larger movies and music files.  

I would ideally like to make it's mount point "/home/wyatt/storage" that way my username will take care of the obvious vulnerability of giving a login access to "/"!

I can provide whatever files i'll need to like fstab or anything else.

PS> for my intentions:  i use a macbook and logging on through finder, so i can stream movies to VLC, only gives me access to my home folder.  also, i would like to be able (in the future), to be able to set up other FTP users who could also have access to that external hard drive.  I have found that hard to do. Tutorials only show me how to sandbox users to their own home folder with pam.   I can take this slow,  i'd like for my sole user 'wyatt' to have access first.

thanks for any help.

---

