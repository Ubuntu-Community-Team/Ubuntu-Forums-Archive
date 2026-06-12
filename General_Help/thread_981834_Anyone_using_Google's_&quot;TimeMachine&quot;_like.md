---
title: "Anyone using Google's &quot;TimeMachine&quot; like backup &quot;flyback&quot;"
date: 2008-11-14
forum: General Help
---

### Post by Kevitivity on 2008-11-14
Some Google code-monkeys have hacked together a program that works like Apple's wonderful TimeMachine backup application for Linux.  Just wondering if any Ubuntu users have any experience with this.  I really love it on the CentOS servers I have.  

Has the Ubuntu community considered providing a smart, super easy to use, rsync like, point and click backup utility like this?  Is there a way we can get this included in Ubuntu?  Are there other/better solutions?

Google Code (FlyBack):
[http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)

---

### Post by Zhukov on 2008-11-14
Didnt knew it... Thanks! =)

---

### Post by christophski on 2008-11-15
I used to use this all the time and just started doing so again today. It works fantastically but sadly it doesn't look as though there has been any progress on it in quite a while :(

---

### Post by scouser73 on 2008-11-15
What I have done with my PC is to have all the things I have downloaded from the repositories burnt onto a CD from a program called APTonCD; [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) once you have installed and done the necessary tasks, you should then install Remastersys, which makes a ISO backup of your system; [http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

Both are extremely easy to use, it took only 20 minutes to have everything back up and running as normal again.

---

### Post by Morty007 on 2008-11-30
I love flyback, but for some reason it doesn't backup one file in particular in my home directory. I think others are planning to step in and take over the development from the author, who has been too busy to keep up with it.

---

### Post by 12barz on 2008-12-07
Tried it today, but it didn't backup any subdirectories of the directories I had put into the "include" list.  Unfortunately, I have data that's nested several layers deep.  If I had to add each subdirectory and subsubdirectory individually, it would take forever, and I'd likely miss some.  Any idea what I'm doing wrong?  Surely there's a way to have the addition of a directory seen as a recursive event.  Help, anyone?

---

### Post by 12barz on 2008-12-11
Gentle but hopeful bump.

---

### Post by 12barz on 2009-01-02
Bump.

---

### Post by Morty007 on 2009-01-02
I'm still using flyback, and it's working great. I think I read somewhere on it's google code page that the developer abandoned it, but someone else is going to take it over.

---

### Post by 12barz on 2009-01-03
Morty007 - Does it recurse your designated "include" directories to include subdirectories and sub-subdirectories?  I can only get it to include the files in the directories named in the include list, but not the subdirectories.

---

### Post by Morty007 on 2009-01-03
As far as I know it does, but I just added some subdirectories. I will do a new backup shortly and will post back.

---

