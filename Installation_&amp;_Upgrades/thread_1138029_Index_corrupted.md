---
title: "Index corrupted"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by einfeldt on 2009-04-26
hi,

I *think* that I have found a work-around on an issue which some other people might experiencing, but I am not sure.  The basic problem is that I am getting a repeating error message that says "index corrupted" and my CPU usage varies between 50% and 100% if I don't apply the tracker-processes -r workaround discussed below.  Apparently, a lot of people are experiencing this problem with Jaunty.

**_My questions ar_**e: 

1. Should I be worried?
2. Should I remove the contents of ~/.cache/tracker and of ~./.local/share/tracker/data ? (see below for discussion).
3. Am I damaging my system by running tracker-processes -r ?  And what services am I missing by not running tracker-processes? (see below for more)
4. Am I correct in concluding that by running the work around shown below I am reducing my CPU usage to comfortably low levels of 93.67% idle for CPU 0 and 77.80 for CPU 1? (see below for details).
5. Should I install the patch described here, and how hard is it to do that?  I generally prefer to wait for stuff to show up in the Ubuntu repository so that Synaptic will install everything properly for me.
[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361205/comments/10](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361205/comments/10)

**_Description of problem_**:

I just upgraded from Ubuntu Intrepid to Ubuntu Jaunty.  It was really quite smooth and seamless overall.  But now I have this issues: When I log into my one and only user account on this machine, I get an error message which appears to send my computer into a loop.  The error says: 

  Tracker
  There was an error while performing indexing:

  Index corrupted

I then get re-occurring dialogs GUIs (only one on the screen at a time) which all give the same tracker error I describe above (index corrupted, etc).  If I click on cancel on one of those dialog boxes, it just comes back.  Same thing if I click OK.  Same thing if I click the X to close it.  

And of course, there is a deeper problem behind this GUI dialog box error message, which is that my CPU usage varies between 50% and 100% if I don't apply it, and I get a huge file at

~/.local/share/tracker/tracker-indexer.log

with sometimes as much as 198,160 lines with the same message over and over, like this:

25 Apr 2009, 22:57:48: Tracker-Warning **: Could not store word 'random': with fatal error

**_Work around_**:

Googling, I found out that there are two relevant known bugs assigned:


[https://bugs.launchpad.net/ubuntu/jaunty/+source/tracker/+bug/346912](https://bugs.launchpad.net/ubuntu/jaunty/+source/tracker/+bug/346912)

[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361205](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361205)

Essentially, what appears to have happened is that developer Michael Biebl forgot to include tracker-processes in the Debian package, as documented here:

[https://bugs.launchpad.net/ubuntu/jaunty/+source/tracker/+bug/346912/comments/15](https://bugs.launchpad.net/ubuntu/jaunty/+source/tracker/+bug/346912/comments/15)

but now that package has been added in:

[https://bugs.launchpad.net/ubuntu/jaunty/+source/tracker/+bug/346912/comments/18](https://bugs.launchpad.net/ubuntu/jaunty/+source/tracker/+bug/346912/comments/18)
I went into Synaptic and I completely uninstalled these packages

tracker
tracker-search-tool

because doing so was sort of implied, I thought, by the suggestion to install tracker-utils here:

[https://bugs.launchpad.net/ubuntu/jaunty/+source/tracker/+bug/361205/comments/23](https://bugs.launchpad.net/ubuntu/jaunty/+source/tracker/+bug/361205/comments/23)

and then run tracker-processes -r
--------------------------------------
cje@rb:~$ tracker-processes -r
Found 133 pids...
Found process ID 3381 for 'tracker-applet'
  Killed process 3381
Found process ID 3387 for 'trackerd'
  Killed process 3387
Found process ID 3427 for 'tracker-indexer'
  Killed process 3427
Setting database locations
Checking database directories exist
Checking database version
Checking database files exist
Removing all database files
  Removing database:'/home/cje/.local/share/tracker/data/common.db'
  Removing database:'/tmp/tracker-cje/cache.db'
  Removing database:'/home/cje/.cache/tracker/file-meta.db'
  Removing database:'/home/cje/.cache/tracker/file-fulltext.db'
  Removing database:'/home/cje/.cache/tracker/file-contents.db'
  Removing database:'/home/cje/.cache/tracker/email-meta.db'
  Removing database:'/home/cje/.cache/tracker/email-fulltext.db'
  Removing database:'/home/cje/.cache/tracker/email-contents.db'
Setting index database locations
Checking index directories exist
Checking index files exist
Removing all database index files
  Removing database index:'/home/cje/.cache/tracker/file-index.db'
  Removing database index:'/home/cje/.cache/tracker/email-index.db'
---------------------------------------------------------------------------

Now, the load on my CPUs seems to be more reasonable:

cje@rb:~$ mpstat -P ALL
Linux 2.6.28-11-generic (rb)     04/25/2009     _i686_    (2 CPU)

11:44:13 PM  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
11:44:13 PM  all    6.29    2.72    1.56    3.74    0.01    0.01    0.00    0.00   85.67
11:44:13 PM    0    2.64    1.47    0.98    1.24    0.00    0.00    0.00    0.00   93.67
11:44:13 PM    1    9.88    3.95    2.13    6.20    0.02    0.02    0.00    0.00   77.80
cje@rb:~$

But the problem appears to be that I am not getting the benefits of tracker-processes, whatever those benefits are.  Also, it seems that I must run tracker-processes -r every time I turn on my machine.

Thanks in advance for any help!

---

### Post by chrisccoulson on 2009-04-26
All "tracker-processes -r" does is a "hard reset" of tracker, where it purges all the index files and stops all tracker related processes. It is currently necessary as a workaround due to index corruption, as reindexing isn't removing all the corrupt indexes, leading to this repeated presentation of the ugly fallback notification dialog with "reindex", "ok" and "cancel" buttons. The dialog is misleading anyway, as it tricks the user in to thinking that they can actually dismiss the dialog without reindexing, when the only valid option really is to reindex.

An updated tracker will be uploaded this week hopefully. It won't fix the corruption as that requires much more significant changes, but it will re-index (properly) when index corruption is detected, won't require user intervention and won't require you to run "tracker-processes -r". This is what my referenced patch does, and you can already use the build in my PPA which incorporates this patch (plus others) [here]("https://edge.launchpad.net/~chrisccoulson/+archive/ppa")

I don't know why the index corruption is happening so frequently. Certainly it seems to be happening after the upgrade from 0.6.6 in Intrepid to 0.6.93 in Jaunty. Hopefully once a reindex is done (with no user intervention), things should settle out and improve a little and you should hopefully see the corrutption issues less frequently (I don't see it at all on my machine now, and the only way I could test out my patch was to manually flip bits in the index files to trigger corruption).

---

### Post by einfeldt on 2009-04-26
> **chrisccoulson said:**
> All "tracker-processes -r" does is a "hard reset" of tracker, where it purges all the index files and stops all tracker related processes. 

And what does tracker do?  I am guessing that it is the workhorse that provides data to a program like "locate" or "find".  I do use "locate" a lot from the command line, and would like to have it available. 

> **chrisccoulson said:**
> An updated tracker will be uploaded this week hopefully. 

Yay!  Thx! Does this mean that it will be available to Synaptic so that I don't have to download the source and compile it?

> **chrisccoulson said:**
> It won't fix the corruption as that requires much more significant changes, but it will re-index (properly) when index corruption is detected,

This is good.  It sounds as if the updated tracker will produce the same functional results as a full fix, or at least nearly so.  

Thanks again, Chris! 

Christian Einfeldt,
Producer, The Digital Tipping Point

---

### Post by OzzyFrank on 2009-04-26
I ran **[COLOR="Indigo"]sudo apt-get install tracker-utils[/COLOR]** and then **[COLOR="Blue"]tracker-processes -r[/COLOR]** and all seems fine now.

---

### Post by einfeldt on 2009-04-26
> **OzzyFrank said:**
> I ran **[COLOR="Indigo"]sudo apt-get install tracker-utils[/COLOR]** and then **[COLOR="Blue"]tracker-processes -r[/COLOR]** and all seems fine now.

Yeah, I went through the process outlined above yesterday, and today I just ran **[COLOR="Blue"]tracker-processes -r[/COLOR]** and my CPU usage is normal, but I have not yet tried to use the "locate" CLI command.  Normally, "locate" is lightning fast, but I am worried that it probably will not be so fast now.  That or I will have to run updatedb every time before using it.  

Also, something new happened today. When I booted into my user account today for the firs time, I was greeted with an announcement that tracker was going to run, but the announcement was two paragraphs long, and I was not able to read the full before it spontaneously exited, probably according to default settings.  At any rate, when I saw that notice, I promptly opened a shell and ran **[COLOR="Blue"]tracker-processes -r[/COLOR]** to protect my CPUs. I am looking forward to the death of this bug :-)

Thx to everyone who is helping to squash this bug!

---

### Post by euchrid33 on 2009-04-29
I had the same bug, and this seems to have sorted it out.  Thanks a lot!

---

### Post by arno_de_Parno on 2009-04-30
For as far as I know tracker and updatedb don't interfere/interact.
updatedb reads (almost) your whole filesystem, and trackerd will index (almost) all files in a user’s home directory.

From the locate (1) man page:
> locate reads one or more databases prepared by updatedb (8) and writes file names matching at least one of the PATTERNs to standard output, one per line.

So updatedb and/or locate seem not to be effected by this bug.

---

### Post by DavidTangye on 2009-05-01
There are many posts here all repeating your issue. For a solution see the launchpad bug reports, in this case [this one is good]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/346912") and there are many duplicate reports there too.
I can recommend you search before posting issues, especially [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu), as your answers are often already there, and it saves these forums being filled with 10,000 'me too' issues.

---

### Post by aklilom on 2009-09-21
> **OzzyFrank said:**
> I ran **[COLOR="Indigo"]sudo apt-get install tracker-utils[/COLOR]** and then **[COLOR="Blue"]tracker-processes -r[/COLOR]** and all seems fine now.

Thanks, this worked for me.

---

### Post by OzzyFrank on 2010-06-24
> **OzzyFrank said:**
> I ran **[COLOR="Indigo"]sudo apt-get install tracker-utils[/COLOR]** and then **[COLOR="Blue"]tracker-processes -r[/COLOR]** and all seems fine now.

I spoke too soon... things got so bad, with it continually trying to index, and basically not being able to search for anything, even after multiple reboots and not using the PC so the indexing could occur uninterrupted... I just had no choice but to totally purge my system of Tracker, and reinstalled Beagle, and I can now search, and reliably.

---

