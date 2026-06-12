---
title: "A problem when install Debian file"
date: 2008-08-03
forum: General Help
---

### Post by jingqi on 2008-08-03
jqduan@jqduan-laptop:~/Desktop/software$ sudo dpkg -i clcsequenceviewer_5.0.1-2_i386.deb 
(Reading database ... 105728 files and directories currently installed.)
Preparing to replace clcsequenceviewer 5.0.1-2 (using clcsequenceviewer_5.0.1-2_i386.deb) ...
Unpacking replacement clcsequenceviewer ...
Setting up clcsequenceviewer (5.0.1-2) ...
Relocation is broken in this rpm release.
If you specified a relocation, please reinstall the package
with the default settings.
Preparing JRE ...

---

### Post by pbpersson on 2008-08-03
Where did this deb package come from?  

Is the deb package designed for your version of Ubuntu?  

Did someone create this deb package by converting an rpm package using Alien?

---

### Post by brian_p on 2008-08-03
> **jingqi said:**
> jqduan@jqduan-laptop:~/Desktop/software$ sudo dpkg -i clcsequenceviewer_5.0.1-2_i386.deb 
(Reading database ... 105728 files and directories currently installed.)
Preparing to replace clcsequenceviewer 5.0.1-2 (using clcsequenceviewer_5.0.1-2_i386.deb) ...
Unpacking replacement clcsequenceviewer ...
Setting up clcsequenceviewer (5.0.1-2) ...
Relocation is broken in this rpm release.
If you specified a relocation, please reinstall the package
with the default settings.
Preparing JRE ...

A Google search on clcsequenceviewer gives six results, one of them being your post! It appears to be software for the Mac so it won't run on Linux anyway.

---

### Post by pbpersson on 2008-08-03
> **brian_p said:**
> A Google search on clcsequenceviewer gives six results, one of them being your post! It appears to be software for the Mac so it won't run on Linux anyway.

Okay - so now I am wondering why software for the Mac ended up in a Debian package....  See?  The mystery deepens...  ;)

---

### Post by jocko on 2008-08-03
It's not only a mac program. A google search (for "clc sequence viewer") turned up [this page]("http://www.clcbio.com/index.php?id=28"). On the download page they have mac and windows installers as well as a "Linux (RedHat/SuSE) installer" (.sh) and a RedHat/SuSE package (.rpm).
The .deb is probably converted from the .rpm by alien.

I downloaded and tried the installer (the .sh file) and it seems to work ok.
The application itself seems to be java based, so as long as java is working, it should work.
I'll have to check it out and see if it's something I need... seems similar to vector nti...

To install it, download the .sh file to your desktop from [this page]("http://www.clcbio.com/index.php?id=479"), run it by:
```
sh ~/Desktop/CLCSequenceViewer_5_0_1.sh
```that will start a graphical installer.
During the installation you'll get the choice to install locally (in a folder in your home directory) or system wide. If you need/want it system wide, you'll have to prefix the above command with sudo. You'll also get a question if/where you want to create symlinks. If you install locally (without sudo) you probably don't need symlinks (and won't have write acces to the system anyway), so just select the options to not make symlinks.

---

### Post by jingqi on 2008-08-03
Hello jocko,
I sh the CLCSequenceViewer_5_0_1.sh file and meet another problem: 

jqduan@jqduan-laptop:~/Desktop/software$ sh CLCSequenceViewer_5_0_1_64.sh 
Unpacking JRE ...
Starting Installer ...
/home/jqduan/Desktop/software/CLCSequenceViewer_5_0_1_64.sh.6429.dir/jre/bin/java: 1: Syntax error: "(" unexpected

---

### Post by jocko on 2008-08-04
Sorry. I have no clue how to solve that. I didn't have that problem.

---

### Post by jingqi on 2008-08-04
Anyway, Thanks a lot to everyone above.

---

