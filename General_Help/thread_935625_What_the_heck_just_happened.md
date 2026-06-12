---
title: "What the heck just happened???"
date: 2008-10-01
forum: General Help
---

### Post by r4736 on 2008-10-01
ubuntu 7.10 / Win XP dual boot. asus z62j barebones laptop.

Last night I went to clear my trash bin. i did so useing Cirodock, it asked if i wanted to clear the trashbin, and then ubuntu froze. I thought maybe there was a large file in there so i gave it time. after a wile i hard booted it. went back into ubuntu to see that all of my settings were gone. some how my trashbin felt like deleting everything in my home directory, and almost all of my windows install on another partition. I have no clue what happened, but would love to hear any tips on getting my data back. the ubuntu part is nfs3 and windows is ntfs. I have a live 7.10 cd, and PE environment xp boot cd, and i can still boot and logon to my ubuntu install.

---

### Post by Pro-reason on 2008-10-01
That is bizarre.  There is no reason why it should happen.  I've never heard of it happening before.

Try [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery).

---

### Post by r4736 on 2008-10-01
I know right, I have used ubuntu for a fiew years, and never had anything like this happen. the annoying thing is that being that ubuntu deleted stuff from my windows partition i cant use simple undelete programs for ntfs. I will have to find my copy of getdataback for ntfs. I have been reading that documentation, and tried a fiew of the methods logged into ubuntu, and the livecd. not having much luck. going to try Autopsy next from the live cd, and will report how that goes. if anyone has any other tricks please let me know, and thank you in advance

---

### Post by findspiderweb on 2008-10-01
Yikes!

I read a bug report about this somewhere. I can't find it at the moment, but this thread looks eerily similar to your problem:
[http://ubuntuforums.org/showthread.php?t=684769](http://ubuntuforums.org/showthread.php?t=684769)

I'm guessing your 7.10 setup hasn't received the patch yet.

---

### Post by r4736 on 2008-10-01
unless the patch you are talking about came out in the past fiew days, or is something not automatically updated. otherwise i keep my system up to date.

---

### Post by findspiderweb on 2008-10-02
Does this look like the same issue though? 

If it's not, we should report this to the developers.

---

### Post by r4736 on 2008-10-02
yes that does seem like the same problem. I guess this all stems from me creating a link to blizzards patch downloader on my desktop from the ntfs partition, and then moving it to trash. odd how that small act sealed the fate of all my data lol. good thing i do backup, but there are some albums, and family photos that have not been backed up yet. there what im digging after. autopsy looks like it may work, now if only the browser on the live cd wasn't so slow this would be less painful.

---

### Post by findspiderweb on 2008-10-02
I just upgraded to 8.04 2 weeks ago after backing up all my data. You should consider upgrading too since you are backing up everything already.

Upgrade took over 4 hours for me, but everything worked fine after the reboot. Several annoying Nautilus bugs got fixed too. :)

---

### Post by r4736 on 2008-10-02
i actuarially was upgraded, but had a lot of problems with framerate playing my games, so i reinstalled 7.10. now i have a disk for 8.04 and as soon as i get my data off i will be installing that from scratch. also has anyone used autopsy. it sees a lot of the files i want, but it says i do not have read access to the files, and if i try to export them the file size is 0

---

