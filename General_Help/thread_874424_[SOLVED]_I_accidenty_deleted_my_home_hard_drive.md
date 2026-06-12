---
title: "[SOLVED] I accidenty deleted my home hard drive"
date: 2008-07-29
forum: General Help
---

### Post by dagoth_pie on 2008-07-29
I was switching back to ubuntu from Kubuntu, and i had a seperate 160gb hd set up as my home folder, i was figuring out to change the mount point of it to /home so it would be seen as the home folder, but i accidently clicked create instead of cancel and now i have a nice 159gb of unallocated disk space, i know that its possible to recover data seeing as its just marked as empty clusters etc, but ive never needed to know how to do it, would someone please be able to help me, just what program (linux based obviously) i could use? thanks

---

### Post by dagoth_pie on 2008-07-29
it didnt take long searching to find what it needed, heres the address for the thread that helped me, just in case someone has the same problem as me sometime
[http://ubuntuforums.org/showthread.php?t=787798&highlight=recovering+formated+files](http://ubuntuforums.org/showthread.php?t=787798&highlight=recovering+formated+files)

---

### Post by tamoneya on 2008-07-29
the easiest way is with test disk.  Since you have the data on a separate harddrive from your root you can just install test disk into ubuntu without worry about overwriting data.  It is in the repositories so you can get it with synaptic or apt-get.  

The way it works is that it searches the drive for files instead of looking in the MFT for the locations of the files.  This should work for you since hopefully all that disappeared was the partition MFT.

---

