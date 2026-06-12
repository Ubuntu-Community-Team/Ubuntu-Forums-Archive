---
title: "Iomega Internal Zip100 not mounting."
date: 2008-10-11
forum: Hardware
---

### Post by Ninja Krow on 2008-10-11
I have an Iomega Zip100 Internal Drive, for some reason it's not wanting to mount. I get this Error:

[center][IMG]http://i3.photobucket.com/albums/y65/NinjaKrow/LinuxError/Error-Mounting_Tran.png[/IMG][/center]

I tried an older HOWTO from around 2005, being that it's 2008 almost 2009 I guessing things have changed and thats why it didn't work.

The Drive it self is at **/dev/sdb** and I have both **/media/zip0** and a symbolic link at **/media/zip** I had to undo editing job i did because it made my computer rig's loadin time very long. took me almost 30 minutes from Power-on to GDM.

I've checked the Disk them selves, the are perfectly fine according to my roommates Windows rig. The problem is the files I want to retrieve onto my Gnome Desktop is take up 96.8MB and is far to large to email to myself via gmail, and he has no Network card or not to begin with.

We also installed the drive itself into his windows rig and the drive works fine as well. 

We're poor students and starving artist here. We can't go out and buy a NIC cards or other fancy stuff. I also just hate the idea of having hardware in my Ubuntu Studio system that is not able to be accessed.

Has anyone ran up against this wall before and succeeded to get the drive going? and if so, could I get a step by step of how you did that?

The file I'm trying to get is a RAW audio file and is very large. I need it for a song I want to create.

Thank you all in advance.

---

### Post by ortalab on 2008-10-16
Zip disks for some reason contains partitions so you have to mount the correct partition. Partition number 4 usually contains the file system.
Try to mount **/dev/sdb4** instead of **/dev/sdb**

---

