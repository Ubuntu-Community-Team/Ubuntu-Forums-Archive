---
title: "Want to move Wubi Installation, but nothing seems to be working properly"
date: 2008-09-22
forum: General Help
---

### Post by SupaBeast on 2008-09-22
Hello there (my first post on this forum). 

So i need some help with my Wubi installation. I recently got hold of this Wubi installer "Wubi-8.04.1-rev506.exe" So i though, wow finally a solution for me to easily run Vista and Ubuntu, so i installed it on the hardisk that had most free space, which is my External Harddrive (E: ) Everything went perfect untill i came inside ubuntu and noticed i couldn't see anything else on the external harddrive. (Where all my music, video's, images and so on are.) 

So i though, ok everything seems to run fine, but i think i have to move the Ubuntu installation to the C: harddrive insted, so i can reach my External drive from both OS'es. 

Went into Vista, tried uninstalling Ubuntu from Add/Remove programs. Here comes my problem: when i press it it asks for UAC access, i accept but nothing happens. So i try a secound time, same result. 

Then i tried the uninstaller in the Ubuntu folder on E:, same result as above. I read the faq page and found a uninstaller there, which game same result also. Then i tried running "Wubi-8.04.1-rev506.exe" (aka the Wubi Setup again, which ALSO gave same result [UAC Access, then nothing happens]).

***So what i want to do is simply: Move my Wubi Ubuntu installtion to my C: harddisk, where my Vista Business installation is also located.***

Sorry for the long post, but i really need assistance in this matter. (If there are any annoying errors in my English i do appologize as i usually speak Swedish.)

---

### Post by SupaBeast on 2008-09-22
Oh right, seems like i solved the problem after all. I'll probably update this post and tell how i did it tomorrow, or as soon as i have time. Atm i just needs some sleep.

Edit:

Ok, what i did was uninstall Wubi and Ubuntu manually. Remove Ubuntu folder, then i used "EasyBCD 1.7.2" to remove Ubuntu from the boot list, restarted and now the Wubi installer worked again. So then i simply installed Ubuntu again with the Wubi installer.

---

