---
title: "Installed Python 2.6 from source, apps are now broken...."
date: 2008-10-26
forum: General Help
---

### Post by besseriym on 2008-10-26
Please help,

I decided to install the newest version of Python last night (2.6 from source, downloaded from the Python website.) I compiled the install from source and everything ran smoothly, no errors at all.

After the install finished, I attempted to run some of my applications that use Python and none of them will start.

Example:
```
~$ avant-window-navigator
Traceback (most recent call last):
  File "/usr/share/avant-window-navigator/awn-applets-migration.py", line 3, in <module>
    import awn
ImportError: No module named awn

```

This is interesting, considering that I actually had a version of Avant-Window-Navigator running as I was installing Python. This error happened when I rebooted and attempted to run AWN.

When I ran the command "whereis awn" I found out that it is in fact where it is supposed to be:
```
$ whereis awn
awn: /usr/bin/awn /usr/lib/awn /usr/lib64/awn

```

The problem is very similar in each of the apps I attempt to start. I will get a "No module named *."

I run Ubuntu Hardy Heron 8.04 on an AMD64 system. After doing some research online, I see that other people have been experiencing similar problems (almost all of them AMD64 users) but have not found any fixes. If there is ANY help you guys could offer me, I would greatly appreciate it. I use python apps very frequently and this is something I hope to fix ASAP. :)

Thank you in advance,
beseriym

---

### Post by besseriym on 2008-10-27
:(

I have tried reverting back to Python2.5, but was receiving a similar error whenever I attempted to start a program that utilized Python.

I then tried (out of desperation) to remove Python2.5 through Synaptic (which was trying to delete A LOT of my other programs) so I decided to try and manually uninstall Python2.5 and then download the 2.5 source from the official Python website and do a manual install. After a whole lot of searching the net/forums, I figured out that when you compile Python from source on Ubuntu, it attempts to install into the prefix "/usr/local", whereas the default Ubuntu Python installation prefix is "/usr". So I fired up Synaptic and looked at where all the Python2.5 files are stored and started to manually delete them one-by-one.

After I had manually removed all of the Python2.5 files from my system, I tried to run a Python App without any success, experiencing the same erros as I had before. I then continued to compile Python2.5 from source and installed using "./configure --prefix=/usr".

That was obviously a mistake, because now I can't use any of the 3 versions of Python on my system (2.4, 2.5 or 2.6) and I can't even get things like System Monitor to load. I'm also receiving errors with Synaptic saying that "A problem has occurred when checking for the updates" and won't even let me see my updates anymore. I have also tried downloading the packages I needed from packages.ubuntu.com and force the install using dpkg, but it didn't help.

I am at a complete loss in this one....I can't figure out how to fix this problem and I need to use those Applications. I am about to just call it quits and start backing up as much data as I can and try a fresh install of Ubuntu (which would be bad for me...definitely trying to avoid this option.)

PLEASE...IF ANYONE CAN EVEN GIVE ME A HINT to steer me in the right direction, I'll try and figure it out myself, but unfortunately, I really need to use some of the programs that are currently broken because of this, so time is not on my side.

---

### Post by besseriym on 2008-10-27
Sadface. :(

I don't have very much luck getting replies, this is my 3rd unanswered post (my first 2 about the same problem, ubuntu continues to disconnect every hour or so from the internet...which has made things unpleasant because I can't finish large downloads, I turn off my IM client so the people on my buddy list don't have to hear the sound of me disconnecting and reconnecting every half hour or so.) Since I could find absolutely NO help what-so-ever on that subject, after countless hours of searching and trying fixes I posted 2 times without a single response. I still have that problem to this day, and still search constantly for some kind of fix, but have ran into road blocks on all fronts.

Don't get me wrong, I am not in the least bit angry about the lack of replies. I completely understand that it's a community forum and not a technical support forum, and that you guys all post help for us newbs out of your own free time and without any real personal gain. I very much admire the amazing effort that the community gives to helping out the newer members...it just so happens that I'm not so lucky with getting help :P

Sigh...I seem to have a lot of problems due to my AMD64 system (I REALLY wish I would have bought the 32-bit CPU instead.) I might be forced into reinstalling this Operating System for the first time. That makes me sad on the inside :(

---

### Post by octo_flush on 2008-11-10
A new install of python2.6 won't 'know' about libraries installed in /usr/lib/python2.5 or any other previous version of python.

Quick dirty fix:
```
cp /usr/bin/python2.5 /usr/bin/python
```

Now, you will also have to specify python2.6 whenever you want to use python2.6 (I said it was dirty!)

The system maintainers (and actually everyone) should have been explicit as to which version of python their software expects to use.

---

### Post by bgs100 on 2008-11-28
Whoa! I just had the same problem as you, and I FIXED IT!!!!!!!!
YEAH!!!
1. So, do "sudo nautilus" in terminal and go to /usr/local/bin.
2. Delete "python", "python2.6", "python2.6-config", and "python-config".  
3. Then, go to /usr/bin.  
4. copy "python2.5" and paste it into /usr/local/bin.
5. also copy "python2.5-config" and paste it into /usr/local/bin.
6. Make sure your in /usr/local/bin.
7. Copy "python2.5" and paste it in the same folder
8. Rename the copy "python"
9. Right click "python2.5-config" and hit "Make Link"
10.Rename the link "python-config"

It should be fixed!!!!
Hope this helps!!!

---

