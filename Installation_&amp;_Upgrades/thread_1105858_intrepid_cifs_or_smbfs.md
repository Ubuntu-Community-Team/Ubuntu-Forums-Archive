---
title: "intrepid cifs or smbfs"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by benvantende on 2009-03-25
after updating my laptop from hardy to intrepid i encounter problems with samba. i am working a lot with this machine on a fileserver and i can't save files anymore. the message i get is: "The document could not be saved, as it was not possible to write to /media/ncfileserver/bentest.txt. Check that you have write access to this file or that enough disk space is available.". filepermissions are ok and I can for instance write to the mounted fileserver with the shell. i read somewhere you have to use cifs to mount the fileserver. i can 't find a proper solution unfortunately. i have read samba is broken for intrepid, but i just can't imagine there is no solution.

---

### Post by cariboo on 2009-03-25
Please provide a link to where you saw that samba was broken. I have been using Samba on my server for years and have never had a problem with it. If you want to manually mount your share, cifs is the way to go. Personally I use smbfs as it always works for me. For mounting using cifs have a look at this [howto]("http:///ubuntuforums.org/showthread.php?t=288534").

Jim

---

### Post by benvantende on 2009-03-25
Hi Jim,

You know how easily you can find links like this or that is broken :) I kinda disregarded that and assume samba is ok as i can't find tons of other problems with this. I had the same with bluetooth. It was all over that bluetooth was not working for Intrepid, but after upgrading to Intrepid it all worked. Duh.
Anyway after upgrading to Intrepid I cannot write to our fileserver anymore. Strange thing is that I can create a file there or copy a file to the fileserver, but I cannot save an edited file. Goes for all kind of files. When I edit a file with in Konsole I can save it however. I mount the fileserver in the regular way in fstab and in Hardy this all worked fine. Maybe Intrepid deals with permissions stricter and this wasn't ok in Hardy. I just have no idea where to look. Upgrading to Intrepid did not change anything for you?

tHNx

ben

---

