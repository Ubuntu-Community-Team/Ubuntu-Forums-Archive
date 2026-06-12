---
title: "How do I share files between operating systems, on the same machine?!?!"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by tkdmaster01 on 2007-04-05
Hey!

I am somewhat new to Ubuntu, and just got it installed on my laptop. I have a version of windows xp home edition also, on another partition. I have a great deal of music and other files I would like to access both from Ubuntu and from Windows, whichever I may be logged on to at the moment.

Also If possible, I would like to do so without a hooked up internet connection, such as at school or during a trip. 

I have looked around for ways to file-share, and not one of the posts or tutorials I found applied to one single machine. They were all inter-machine file sharing.
If anyone could direct me to a site they found to do this, or help me out in any way, it would be much appreciated!!!

Thanks!

---

### Post by djheadley on 2007-04-05
Could you tell us how your machine is set up?  What partitions do you have?

---

### Post by BRAXS69 on 2007-04-06
i found that this wiki [http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") would have just about answer any questions i had....

**sharing the windows files with Linux**
to share the files between the os, you would need to mount your windows partition assuming that its using (NTFS) and you would probably want (read and write)  [LINK]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")

**and to share Linux files with windows**
all you would need is this [http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by tkdmaster01 on 2007-04-06
I have an 80 Gig HD

3 gig swap for ubuntu
31.4 gig partition ext3 for ubuntu

the rest is set for windows under the original partition type I bought the laptotp with.

I can set up NTFS mounts to access the files with another computer, but I would like some kind of partition accessible from both windows and Linux on the same machine


Thanks for the relply

---

### Post by tkdmaster01 on 2007-04-06
Thanx BRAXS!
that last link pretty much answers the question.

---

### Post by strabes on 2007-04-06
I recommend having a separate ext3 data partition that is shared between windows and linux. That way you don't have to back up any of your music or movies when you reinstall windows or ubuntu. I wrote a blog post about this awhile ago: [http://strabes.wordpress.com/2006/11/21/readwrite-support-for-ext2ext3-filesystems-for-windows/](http://strabes.wordpress.com/2006/11/21/readwrite-support-for-ext2ext3-filesystems-for-windows/)

---

