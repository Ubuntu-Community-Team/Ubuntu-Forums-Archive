---
title: "Can't remove program"
date: 2008-08-13
forum: General Help
---

### Post by perks on 2008-08-13
I try to use 'sudo apt-get remove nvidia-glx-new' to remove the program but i get the following error message:> Removing nvidia-glx-new ...
dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx-new (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx-new
E: Sub-process /usr/bin/dpkg returned an error code (1)
Can someone please help in in fixing this?

---

### Post by gcday on 2008-08-13
I get the same error in trying to remove it.

---

### Post by cariboo on 2008-08-13
Have a look at this thread:

[http://ubuntuforums.org/showthread.php?p=5269498](http://ubuntuforums.org/showthread.php?p=5269498)

Jim

---

### Post by gcday on 2008-08-13
> sudo mkdir /usr/lib32
sudo touch /usr/lib32/libGL.so.1


What does this mean? what am I suppose to do with this information?

---

### Post by Ryadt on 2008-08-13
Type them in the terminal.

---

### Post by gcday on 2008-08-13
Great that's solved that problem - but it's caused another. 

Everything is now very jerky (graphics) - I'm guessing because the system is no longer configured corrected for my onboard graphics card (intel gma 3100).

What's my next move?

---

### Post by gcday on 2008-08-14
Anyone? how do I even check what driver my graphics card is currently using? Ubuntu doesn't seem to have a device manager...

---

