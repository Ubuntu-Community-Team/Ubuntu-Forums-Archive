---
title: "[SOLVED] How do I install software from tar.bz2 in KDE4?"
date: 2008-09-27
forum: General Help
---

### Post by kokkus on 2008-09-27
I am new to kde.
Plz tell me how I install software from tar.bz2 archive.
Thanks:)

---

### Post by Xiong Chiamiov on 2008-09-27
> **kokkus said:**
> I am new to kde.
Plz tell me how I install software from tar.bz2 archive.
Thanks:)
Depends on what is inside of it.  Take a look [here]("http://ubuntuforums.org/showthread.php?t=931340"), then ask back here if you have any questions.

---

### Post by kokkus on 2008-09-27
I Know how to execute a script, and there are none make file in the dir either. I won't ask if it was that easy.
OK, here's there program I would like to install:
[http://linux.softpedia.com/get/Multimedia/Video/KatchTV-11842.shtml](http://linux.softpedia.com/get/Multimedia/Video/KatchTV-11842.shtml)

Could you help me please?

---

### Post by oldos2er on 2008-09-27
Did you read this:

**[B]Installation:**

To actually install this, the easiest way is just to move the untarred directory to some location like /usr/local/KatchTV, and then make a symlink from that directory's KatchTV executable into /usr/local/bin or your personal ~/bin directory.

So basically, from scratch, you can do:

   cd /usr/local
   tar xvjf /path/to/the_downloaded/KatchTVtarball.tar.bz2
   ln -s /usr/local/KatchTV/KatchTV /usr/local/bin/KatchTV

Then, just run KatchTV from the command line, or make a KDE icon for it.[/B]

---

### Post by Xiong Chiamiov on 2008-09-27
> **kokkus said:**
> I Know how to execute a script, and there are none make file in the dir either. I won't ask if it was that easy.


I try not to assume any level of knowledge from people here, since the scale varies wildly.

---

### Post by kokkus on 2008-09-27
> **Xiong Chiamiov said:**
> I try not to assume any level of knowledge from people here, since the scale varies wildly.
I was just bored of not getting this to program to work.

---

### Post by kokkus on 2008-09-27
I try to run the KatchTV file in terminal and get the following error:

from kdecore import KAboutData, KCmdLineArgs, KApplication
ImportError: No module named kdecore

What does this mean?
Please help me with this.

Thanks:)

---

### Post by kokkus on 2008-09-28
Please help me with this. I don't know what to do.
I installed all the extras I need, but what is a symlink and what do you mean by this.

```
cd /usr/local
tar xvjf /path/to/the_downloaded/KatchTVtarball.tar.bz2
ln -s /usr/local/KatchTV/KatchTV /usr/local/bin/KatchTV
```

all the path/to stuff makes me comfused. 
Ok /usr/local I am with you so far coz that's the directory.
Ok I extract the archive, move it to /usr/local
And now then?

Or can you please create a .deb for me with all things done so I can just install it and it will work?

---

### Post by oldos2er on 2008-09-28
I'm on my brother's computer (running Vista), so I may not be of much help. This command:

ln -s /usr/local/KatchTV/KatchTV /usr/local/bin/KatchTV

creates the symlink, and according to the instructions, you should be good to go after that.

---

### Post by kokkus on 2008-09-28
So that is was symlink is? thanks:) 

Now I get this error when I try to run KatchTV:

```
Traceback (most recent call last):
  File "/usr/local/bin/KatchTV", line 59, in <module>
    mainFunc()
  File "/usr/local/bin/KatchTV", line 23, in mainFunc
    from kdecore import KAboutData, KCmdLineArgs, KApplication
ImportError: No module named kdecore

```

Any idea?

---

### Post by oldos2er on 2008-09-28
I believe kdecore was for KDE versions 3.x. See if there's a version of the program for KDE 4.x, assuming that's what you're running.

---

### Post by kokkus on 2008-09-28
I searched in synatic for kdecore. THe only package I found was python-kde4. I removed it but KatchTV will still not work.

---

### Post by oldos2er on 2008-09-29
Why did you remove python-kde4? I'd reinstall it if I were you.

---

### Post by kokkus on 2008-09-29
Ok done, but katchtv will still not start.

---

### Post by oldos2er on 2008-09-29
> **kokkus said:**
> Ok done, but katchtv will still not start.

 Again, Katchtv is a KDE 3.x program. You need to find an updated version that runs on KDE 4.x.

---

### Post by kokkus on 2008-09-29
OH so that's what you mean? SO I can't just install KDE 3 then?

---

### Post by kokkus on 2008-09-29
Thank you, I installed kde3 and it works. 
The program was lame so much work for nothing.
Or, not really.
I found out a little bit more about how programs work and are built with kde.

---

