---
title: "Please Help: Can't see anything after upgrade from 8.10 -&gt; 9.04"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by jtmelton on 2009-05-08
Hi, 
I just upgraded this morning from 8.10 -> 9.04, assuming everything would go well.  After the restart at the end of the process, the initial splash screen comes up, I get nothing, just a black screen - nothing.  My video card is a radeon 4350.  Any ideas please?  
Thanks,
John

---

### Post by brandon82 on 2009-05-08
I feel your pain. I just upgraded last night and now am experiencing the same problem. I get the splash screen, followed by a bunch of vertical colored lines, then eventually, nothing. I am dual booting with XP, with Grub as the boot loader. XP is still working properly.. help!

---

### Post by overdrank on 2009-05-08
> **jtmelton said:**
> Hi, 
I just upgraded this morning from 8.10 -> 9.04, assuming everything would go well.  After the restart at the end of the process, the initial splash screen comes up, I get nothing, just a black screen - nothing.  My video card is a radeon 4350.  Any ideas please?  
Thanks,
John

Hi and welcome, you may try and boot into recovery mode which is usually the second choice from the grub. Then you can choose the xfix option to correct graphical issues. After xfix complete it should give you the option to boot normally.

---

### Post by Gaz... on 2009-05-08
Me to...

I've just done the upgrade also, and now after the splash screen there is just a blank screen... :(

I've hit ESC on start up and gone through all options, but still nothing.

Now I've had to go to a Windows machine to get to here for help!!!

Gaz...

---

### Post by jtmelton on 2009-05-08
I tried the xfix option, and a little better.  I now get a screen that has a bunch of multicolored lines instead of a black screen - I still can't see anything though.  Any follow on thoughts?

---

### Post by jtmelton on 2009-05-08
Ok, got my screen back - had to do some translation, but found this 
[http://forum.ubuntuusers.de/topic/upgrade-ubuntu-8-10-9-04-pc-freeze-beim-boote/](http://forum.ubuntuusers.de/topic/upgrade-ubuntu-8-10-9-04-pc-freeze-beim-boote/)

and the key line for me was to drop into recovery mode to a terminal and then run
```
sudo apt-get remove --purge fglrx*
```

Hope this helps.

---

### Post by Gaz... on 2009-05-08
> **jtmelton said:**
> Ok, got my screen back - had to do some translation, but found this 
[http://forum.ubuntuusers.de/topic/upgrade-ubuntu-8-10-9-04-pc-freeze-beim-boote/](http://forum.ubuntuusers.de/topic/upgrade-ubuntu-8-10-9-04-pc-freeze-beim-boote/)

and the key line for me was to drop into recovery mode to a terminal and then run
```
sudo apt-get remove --purge fglrx*
```

Hope this helps.


Cheers J T Melton, your a star mate... 

It worked...


Its' a good job all those "Ubuntu Guru's" where on hand to show you and us the way!!!  :^o


Gaz...

---

### Post by overdrank on 2009-05-09
> **Gaz... said:**
> 

Its' a good job all those "Ubuntu Guru's" where on hand to show you and us the way!!!  :^o


Gaz...

Ouch!!!  :-#

---

### Post by Lightsider on 2009-05-21
Fixed it for me too - thank you very much!!

Just out of curiosity, what do the fglrx packages do?

---

### Post by oldrocker99 on 2009-05-23
The fglrx packages are the old ATI drivers, which only will work on what ATI chooses to call "legacy" chips. Fglrx is NOT compatible with Jaunty, and without those drivers, there's no OpenGL. :mad:

:guitar:

---

### Post by Davepar on 2009-07-20
Thank you very, very much for this tip. I recently switched my Ubuntu hard drive from a machine with an ATI video card to a machine with an NVIDIA. Couldn't find any way to avoid the blank screen after the machine booted until this thread. Saved me hours of re-installing my development environment.

Dave

---

