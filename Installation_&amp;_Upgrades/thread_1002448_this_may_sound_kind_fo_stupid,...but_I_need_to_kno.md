---
title: "this may sound kind fo stupid,...but I need to know how to transfer files"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by ElevenWarrior on 2008-12-05
I installed 8.10 today, I just need to know how to find my old files (I had 8.04 installed as well) that I had on 8.04. I can read the HD and all i just can't find the files! (I don't know which directory there in)
I'm looking for my music, pics docs etc
any ideas?

---

### Post by Shwefty on 2008-12-05
One idea is to open up Terminal and type "locate " then the file name.

Example "locate pictures" to find the picture folder.  A bunch of results will probably spring up, check the path on the files to see if you can find them from that.  Oh, and it is CaSE SensiTIvE.

---

### Post by Partyboi2 on 2008-12-05
You could also go to "Places>Search for Files" and do a search.

---

### Post by generic_idea_machine on 2008-12-05
if you formatted the disk and had the fresh install going on the same partition...then your data is gone. 

otherwise, try the locate command as specified above. 

you can also use the find utility

to find anything by name, type:
find . -name blah (where blah is what you are searching for)

---

