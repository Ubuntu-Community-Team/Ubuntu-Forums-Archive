---
title: "Archive manager doesn't extract multi-part (part01.rar) archives"
date: 2008-10-01
forum: General Help
---

### Post by davidryder on 2008-10-01
I've been using the command line (unrar x) to extract multi-part files but I would really like to be able to use archive manager. 

It works if there is only one file in the archive but if there are many files in the archive I have to use the command line.

Any ideas?

---

### Post by Meow27 on 2008-10-01
-in my opinion, simplest way to get out of this problem is to install the windows version of 7zip for Wine.

after that. you try to extract the file (note: you need all of the parts to extract the files otherwise)
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
[http://www.7-zip.org/download.html](http://www.7-zip.org/download.html)




-aside from that, you can check if you have winrar-nonfree and 7zip installed in synaptic. i dont recall extracting file parts in ubnuntu so i cant guarantee that this method will work (but it should)

---

### Post by TheLions on 2008-10-01
> **davidryder said:**
> I've been using the command line (unrar x) to extract multi-part files but I would really like to be able to use archive manager. 

It works if there is only one file in the archive but if there are many files in the archive I have to use the command line.

Any ideas?

file-roller opens multi-part files with extension which look like .r00, .r01, .r02 and so on, not the part00.rar, part01.rar ...

---

