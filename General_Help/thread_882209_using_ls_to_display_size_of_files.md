---
title: "using ls to display size of files"
date: 2008-08-06
forum: General Help
---

### Post by milasch on 2008-08-06
Hello...

ls -s displays the size of a file in blocks...

A file A with 12072 blocks (ls -s), in Nautilus is 12343489 bytes... 
This would mean the block size is: 1022.489148442677269715043074884 bytes

file B:
1772 blocks in ls
nautilus reports it to have 1807751 bytes
Block size: 1020.175507900677200902934537246 bytes

So I can say nautilus reports the actual file size, and ls -s the actual disk usage, right?

now, is there a way of getting the same size being reported by nautilus with ls? it would be quite handy.

Thanks

---

### Post by Oldsoldier2003 on 2008-08-06
ls -l or if you want the human readable: ls -lh

---

