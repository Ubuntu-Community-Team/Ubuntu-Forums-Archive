---
title: "Where do new programs go?"
date: 2006-01-26
forum: Installation &amp; Upgrades
---

### Post by sbasak on 2006-01-26
In Windows, programs usually go 
C:\Program Files\<NEW PROGRAM>
and sometimes DLLs go to 
C:\WINDOWS\SYSTEM

So, what are the equivalent locations in Ubuntu?

---

### Post by ubuntumaneh on 2006-01-26
Usually the new apps we are downloading and installing is going to be in /etc. So try it in a termnal:

cd /etc
ls | less

and you are going to see your things.

---

### Post by MJN on 2006-01-26
Er not quite... or have I misunderstood the question?
 
It can be difficult to attempt to draw direct parellels between different OS's however for all intents and purposes the Linux equivalent to 'Program Files' is **/bin/** and **/usr/bin/** for user 'executables' (or, 'binaries') and **/sbin/** and **/usr/sbin/** for system binaries.
 
However, as you'll see, there are a whole load of other directories for other specific functions e.g. **/etc/** (config files), **/lib/** (libraries to support other binaries),** /var/** (variable data) and** /tmp/** (temporary files) etc.
 
Incidentally, you can regard **/home/<user>/** as 'My Documents' for <user> but this is starting to stretch things a little..
 
Mathew

---

### Post by Jucato on 2006-01-26
I thought the executable parts of the packages go to /usr/bin/ ?? I mean that's where I find them.

Does anyone have an explanation about how programs are installed? I'd like to know as well...

EDIT: I was typing this before MJN's post. Still, if anyone can provide clarifications on this... I'm just as curious as sbasak.

---

### Post by MJN on 2006-01-26
Yeah, I think we were all typing at once there!
 
But anyway, I'm right... ;) (or at least as right as you can get with an open-source variable/customisable distro OS...)
 
Check out [http://www.pathname.com/fhs/pub/fhs-2.3.html]("http://www.pathname.com/fhs/pub/fhs-2.3.html")
 
Mathew

---

### Post by Jucato on 2006-01-26
yeah I think you're right, too, at least as far as the /usr/bin is concerned. :D

Thanks for the link. I'll be browsing through that (or bookmarking it. it's huge!!)

EDIT: as far as "standards" are concerned, do most, if not all, Linux distros follow that document you linked to?

---

### Post by Luke771 on 2006-01-26
Well for an innocent newbie like me, it looks like the programs are simply "unpacked" (or decompressed or whatever) and that's enough to get them working, because there's no such thing as an "Ubuntu Registry" requiring (almost all) executable files to have registry entries, sometimes with "unlocking keys".
As I understand it you don't really need to "install" programs in Linux, you simply write the uncompressed files somewhere and it will work (But I may be completely wrong: please correct me if I am).
Where do they go when auomatically installed by Synaptic or Automatix? Looks to me like there's no one answer to that: Sometimes I find out that the executable file is in /bin, other times they are in /usr/[program directory], "invisible" ptograms (i.e. daemons) are often located in /etc/init.d... and the list goes on.
I guess the only way to know where an automatically installed program is hiding, if not found in the directories where it "should" be, is to launch a desktop search.
Anyways, the most often used "program directories" are those listed in the posts before this ( /usr/bin /bin and so on)

---

### Post by kabus on 2006-01-26
A good way to find out where an executable was installed is using the "which" command (only works for directories in your $PATH though).

---

### Post by MJN on 2006-01-26
[quote=Fenyx]EDIT: as far as "standards" are concerned, do most, if not all, Linux distros follow that document you linked to?[/quote]
 
Most do and, more importantly, Debian is one of them ergo so is (K)Ubuntu.
 
Luke, you mentioned the term 'install' - Linux applications most definitely do 'install'. In particular, many applications (that aren't in packages) would be provided as source code and you would compile them on your own machine... this arguably fits a common definition of 'installing', more so even than copying pre-compiled binaries to your Windows system.
 
Packaged applications, on the other hand, are usually pre-compiled binaries with all the associated files (config, documentation etc), and are built on a per-distro basis where the system construction is commonly defined. Thus, in this case you are generally just copying files into the relevant locations (as defined by the FHS standard) and configuring files on-the-fly. This is more akin to what happens in Windows (the 'installer' is just a decompressor and knows where to stick all the files, how to modify the registry etc). However, this is still termed 'installing', if only illustrated by the **apt-get *install* <package>** command...
 
Mathew

---

### Post by Tripmonkey_uk on 2006-01-26
Just incase u can't find a program in the usual places, u should also check in /opt.
This is normaly for when u install programs yourself, but things like Automatix etc. tend to put Firefox folders in there.

---

### Post by ubuntumaneh on 2006-01-26
I have misunderstood the question

---

### Post by Alpha_toxic on 2006-01-26
1. If you try "properties" in Synaptic or even on a .deb file it shoud give you a list of all files in the package and exactly where they are going.
2. In win: the whole (allmost) program goes in C: > program files > "program name". This means all .exe's, all docs, readmes, .dll's, libraries and so on (again allmost everything, as some stuff ends up in "C:\windows" or "docs and settings\app data" ). 
In linux: there are different dirs for the libraries, executables, docs and everything else, so a program is spread across a bunch of different dirs.

In my opinion the win way could be the  better one if there were not some pretty stupid things done there. It would be easyer to remove the program if it is completely in a single dir (just delete the dir), but in win even if you do so you have the registry, %AppData% and other stuff left behind, so it's no good. And after adding that the permissions stuff is easier to handle in the linux way, it's much better the linux way.

---

### Post by Jucato on 2006-01-26
Linux uses a different file system than Windows. It groups files according to functions rather than package. The closest thing that Windows has to this is it's WINDOWS/System and System32 directory where most dll's and basic programs are stored. Linux also doesn't have/use a registry, which they say makes it more secure (what harm can a registry-modifying virus do when you don't have a registry at all?). I've read somewhere (can't remember where, but it's online) that Linux separates files this way for security and general OS integrity. But being a newbie, I still can't understand why...

MJN, thanks for the link. Unfortunately, its quite too technical. I was actually looking for something that could explain (in easy-to-understand-but-not-too-noobish-terms) why Linux's file system is set up that way (or why it doesn't have/need a registry). But thanks anyway! I'll bookmark it for future reference. :D

---

### Post by MJN on 2006-01-26
You might prefer [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") which has a snapshot overview of the FHS structure. It doesn't discuss registries, but it does illustrate what files go where.
 
With regards to registries there are indeed pros and cons as discussed above. However, just because the Windows implementation may be poor doesn't mean the concept is. In view of this, there is a Linux project which provides a similar function - [http://www.libelektra.org/]("http://www.libelektra.org/").
 
Mathew

---

### Post by Jucato on 2006-01-26
Ooooh wiki-wiki!! Thanks MJN!!
Two more sites to add to my ever-growing Linux Bookmark Library! \\:D/

---

### Post by MJN on 2006-01-26
Soon you'll have to bookmark your bookmarks... Maybe call them Favourites? Err.. no.. we won't go there... ;)

---

### Post by Jucato on 2006-01-26
Hahaha! I'll just call them My Preferences. Sounds more sophisticated and less... oops.. not going there. :D

---

### Post by Luke771 on 2006-01-28
Well I was wrong. Nobody is perfect.
Some application must actually be installed, some must not and some other run as plugins in other programs.

---

