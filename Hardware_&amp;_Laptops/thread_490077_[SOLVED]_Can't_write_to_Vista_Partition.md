---
title: "[SOLVED] Can't write to Vista Partition"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by theDaveTheRave on 2007-07-02
Hello all.

I've just recently installed festy onto my new laptop, an all is wonderfull and happy in the world.

but unfortunately some things need to have vista / windows to function (:sad:  

anyway, I have a tendency to use my windows HDD partition to hold my personal files and stuff so as I can access them from windows if required, or at least that what I have done in the past.

I had everything running nicely and all setup correctly, and tried to eddit a document on the windows partition (I use open office on both partitions so no compatibility issues there). Well it seems that I don't have write permissions on the files.

so I ran <chown> to give me permisions on the file / directory, but no change. It seems as though the Vista partition is read only!

I've not seen this before, I was a bit confused :-k

Well If I can't fix it I will simply create another partition on the Ubuntu part and make it available to Windows by formatting as NTFS - I assume that will work.

I'm just concerned that I am going to waste 20GB of disk space..... is this another case of MS trying to stop people from using other OS's?? or is my setup just wrong / bad?

Has anyone else experienced this problem??

Dave

---

### Post by mjfernandez on 2007-07-02
It might be mounted read-only. I don't know if this has changed, but ntfs partitions have been read-only by default in the past because the file system drivers were still somewhat unstable, or in beta.

---

### Post by tarasbulba on 2007-07-02
please search forum for ntfs writing.search for ntfs-3g

---

### Post by theDaveTheRave on 2007-07-02
Guys.

Thanks for the posting advice.

I had allready searched under <write to Vista partition> on the forum, but if I need to try again i shall with the <write to ntfs partition>.

If the NTFS partition does boot without write access, how do I get it to allow write access at startup?? as I can't set write access to the drive from within the terminal using <sudo chmod> or <sudo chown>, and I can't unmount the drive either - as I don't have permissions to do so.... although I haven't tried from a terminal with <sudo>

so I shall try that tonight, change the permissions and then re mount.

but I may still need to have a boot up script.... it that correct?

Dave

---

### Post by theDaveTheRave on 2007-09-17
Solution was to use the NTFS 3g facility.

here is the link to the forum thread.

thanks for the help gents, sorry it took such a long time to "solve" this thread.

[http:///ubuntuforums.org/showthread.php]("http:///ubuntuforums.org/showthread.php")




dave

Just realised each time I close a thread it increases my bean count!!

---

