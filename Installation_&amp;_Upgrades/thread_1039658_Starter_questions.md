---
title: "Starter questions"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by niallheavey on 2009-01-14
Hi everyone,

Brand new to Ubuntu and any operating systems bar Windows!!!

But just a few starter questions though.....

I have to download and install and run a programme,

When I go to download it I get 2 options 
.rpm
.deb
.tar.bz2

1st of all, what is the difference between these different formats? And second, once my download is complete what do I do then to install and run the programme? 

Many thanks,

Niall.

---

### Post by taurus on 2009-01-14
The .rpm extension is for RedHat an related releases.  For Ubuntu (Debian), you want to get the .deb extension.  On the other hand, the .tar.bz2 or .tar.gz are mostly for source codes where you either have to compile it for your machine or run/install it.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by niallheavey on 2009-01-19
Thanks very much for the reply.

However when I went to do it I realised that the .deb version was only available on a version that I dont want.
So on the version I need to download I only have the .tar.bz2 available to me.

I was searching through ways to install this and none of them seem to be working for me. I keep getting the error messages like
No such file or directory,
Error is not recoverable: exiting now
child returned status 2
Error exit delayed from previous errors

As I have never used Ubuntu until now I have no Idea what these mean!!!

So hopefully someone can tell me what I might be doing wrong when trying to install this .tar.bz2 file.

(Also, when I do get it installed how do I run it!!)

Thanks very much,

Niall.

---

### Post by jken146 on 2009-01-19
When you want to install something, first check to see if it is in the Ubuntu repositories.  These are collections of software that have been compiled for Ubuntu and it is recommended to use the packages there if possible.

Look in Applications > Add/Remove or in System > Administration > Synaptic to install new packages.

What exactly are you trying to install?

---

### Post by niallheavey on 2009-01-19
Its a programme called Webots,
Its a robotics simulator.

I need the simulator for my final year project in college. I was told to use the linux versions of the programme!!!
However, I had never used linux before so i'm trying to learn a new Op system as well as everything else!!!

Just checked that list and there is no sign of it anywhere!!

---

### Post by taurus on 2009-01-19
When you download something, the default save directory is your ~/Desktop.  So, look in there first.

```
ls -la ~/Desktop
```
Otherwise, include the site where you've downloaded it (plus the name of the file).

---

### Post by niallheavey on 2009-01-19
Yea when I do that it gives me a list of the things on the desktop.

The one i'm looking for is 

-rw-r--r--  1 niall niall 43612621 2009-01-14 16:34 webots-5.8.0-i386.tar.bz2

How do I go about installing it and then running it?

---

### Post by taurus on 2009-01-19
```
cd ~/Desktop
tar xvjf webots-5.8.0-i386.tar.bz2
```
At this point, it will unpack itself into a new directory, probably webots-5.8.0.  You need to change to that new directory and have a look at either README or INSTALL.

```
cd webots-5.8.0
ls -la
```

---

### Post by niallheavey on 2009-01-19
Ok, thats great. It make a new file on the desktop for me, when I do the commands you said I get the following list:

total 7936
drwxr-xr-x 9 niall niall    4096 2008-03-06 13:00 .
drwxr-xr-x 4 niall niall    4096 2009-01-19 15:44 ..
drwxr-xr-x 4 niall niall    4096 2008-03-06 13:00 doc
drwxr-xr-x 6 niall niall    4096 2008-03-06 13:00 include
drwxr-xr-x 2 niall niall    4096 2008-03-06 13:00 lib
-rw-r--r-- 1 niall niall     498 2008-03-06 13:00 .nautilus-metafile.xml
drwxr-xr-x 7 niall niall    4096 2008-03-06 13:00 projects
drwxr-xr-x 5 niall niall    4096 2008-03-06 13:00 resources
drwxr-xr-x 3 niall niall    4096 2008-03-06 13:00 transfer
drwxr-xr-x 2 niall niall    4096 2008-03-06 13:00 util
-rwxr-xr-x 1 niall niall 8071825 2008-03-06 13:00 webots

So no Install or readme

P.S. I'm really sorry about all the stupid questions, I'm a complete novice with Ubuntu!!!

---

### Post by taurus on 2009-01-19
The documents should be in the doc directory.  The executable file is webots.

```
cd ~/Desktop/webots-5.8.0
```

If you want to look at the doc, look in the doc directory.

```
cd doc
ls -la
```

And if you want to run it, do

```
./webots
-or-
sudo ./webots #with root privilege
```

---

### Post by niallheavey on 2009-01-19
Ok,

Finally got it.

Thanks very much for your help.

No doubt I will have more Ubuntu questions in the future!!!

Niall.

---

