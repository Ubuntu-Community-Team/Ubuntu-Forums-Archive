---
title: "My Hard Drive Is Shrinking!?!?!?"
date: 2008-12-01
forum: General Help
---

### Post by magearwig on 2008-12-01
I've been running 7.10 for about a year now.  My primary drive is 38 gigs, and I primarily store all my files on external drives.

I upload, download, and create a lot of audio/video material every day.   This takes up a fair amount of space.  It's not uncommon that I will fill up my drive over the course of week, and then have to empty it out at the end of the week.  I should be able to free up at least 20GB of space on my hard drive if/when I take everything off.

Lately (2 months), I haven't been able free up more than 4GB of space on my hard drive, no matter how much stuff I delete.  No matter how much I look around my home folder, I don't find anything ever remotley big enough to make 15GB of space just disappear.  

4GB isn't even enough space to burn a DVD, which only compounds the problem for me really.

I've tried booting off a live disc (doing it right now actually), still don't see anything I didn't see before.

Anyone had this problem before?  Have any ideas.

---

### Post by hyper_ch on 2008-12-01
run:

```

cd /path/to/38gb_drive
sudo du -h --max-depth=5 > ~/Desktop/output.txt

```
That will create a file containing up to 5 level deep the info and disk space used... maybe alter the 5 to 2 or so and you can find out where all the space goes...

---

### Post by whitethorn on 2008-12-01
Have you tried running the program 

```
baobab
```

It's a cool program which shows how big folders/files are and how much space they take up in a percentage on your HD.  Might help further.

---

### Post by magearwig on 2008-12-02
Okay.  I tried the terminal code, it didn't work.  I have a hard time doing anything more complicated than one thoughht at a time via the terminal, and may have just messed it up.

Here's what it looked like.

magearwig@magearwig-desktop:~$ sudo du -h --max-depth=5 > -/desktop/output.txt
bash: -/desktop/output.txt: No such file or directory
magearwig@magearwig-desktop:~$ cd /pathto/38gb_drive sudo du -h --max-depth=5 > -/desktop/output.txt
bash: -/desktop/output.txt: No such file or directory

I did get the disk analyser.  I got some rsults.  Evedentally, I have 21gb of trash that hasn't been disposed of.  So I'll go looking for that.  Also I noticed my USR folder (keeps most of the stuff that make my lightscriber work)  Look at the properties, it shows up as 7mb, but o n here it's 3gb.  Where is that coming from?

I think I can attach the screen shots I took here, let's try.

---

### Post by hyper_ch on 2008-12-02
it's not working because

~ is not the same as -

---

### Post by guiliker on 2008-12-02
perhaps not relevant but i had a problem with trash not actually trashing i found that files were becoming hidden and root only - not sure why or how! however i found the fix was to use nautilus as root with hidden files shown i soon went around deleting files i'd created and the problem was solved. I have found with gutsy i need to do this every now and again - i'm not sure why.

---

### Post by rbmorse on 2008-12-02
> **hyper_ch said:**
> it's not working because

~ is not the same as -

So where do you think his file ended up? Shouldn't that syntax produce an error?

---

### Post by hyper_ch on 2008-12-02
it did not run because of the "-"

---

### Post by drs305 on 2008-12-02
The title pretty much tells you what this link is about:
[How To: Disk Full? - Check Your Trash]("http://ubuntuforums.org/showthread.php?t=898573")

Emptying your user trash is just not enough sometimes. There is a bit about other ways to restore space as well.

---

