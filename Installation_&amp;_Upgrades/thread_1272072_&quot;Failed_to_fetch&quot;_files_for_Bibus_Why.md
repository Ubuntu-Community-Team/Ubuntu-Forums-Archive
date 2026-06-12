---
title: "&quot;Failed to fetch&quot; files for Bibus? Why?"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by oldtime on 2009-09-21
Hi all.
I'm trying to install Bibus on my Hardy 8.04. I have been following instructions from [http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu](http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu) and also 
[https://wiki.edubuntu.org/Bibus](https://wiki.edubuntu.org/Bibus)

Using the "sudo gedit /etc/apt/sources.list" command from my terminal, I added the following sources to my /etc/apt/sources.list
_____________
## Bibus
deb [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./
deb-src [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./
_______________
So then I used the wget command and got the following response:
___________________
 me@mycomputer:~$ wget -q [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/pmartino.gpgkey](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/pmartino.gpgkey) -O- | sudo apt-key add - OK me@mycomputer:~$ _____________________ Then when I entered the command "sudo aptitude update", I get:
_____________________
........
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Err [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Packages
  302 Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Err [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) ./ Sources
  302 Found
W: Failed to fetch [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Packages.gz](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Packages.gz)  302 Found

W: Failed to fetch [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Sources.gz](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Sources.gz)  302 Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
________________________
It looks to me like that's an error message telling me that while it can find all the Hardy updates, it can't find the sourceforge files needed to install Bibus. Presuming it DID find them using this command, it looks like I could then run "sudo apt-get install bibus libsqliteodbc python-pysqlite2 python-wxgtk2.6 python-uno" to install bibus and it's depedencies. (I think there's some elegant way of commanding the computer to "check for dependencies", but I don't know what that is). I've made SURE that I've entered the addresses into my package manager correctly (I've done it 6 times or something), so it's not typos. Could the addresses be outdated? I thought about that and tried using the following instead in my /etc/apt/sources.list:
_________________________
deb [http://sourceforge.net/projects/bibus-biblio/files/](http://sourceforge.net/projects/bibus-biblio/files/)
deb-src [http://sourceforge.net/projects/bibus-biblio/files/](http://sourceforge.net/projects/bibus-biblio/files/)
___________________________
...I was thinking that, since these are the websites to find Bibus files, I might use those instead. I tried including and not including a ". /" at the end of the lines, but that got me nowhere as well.

Any ideas? I'm three months new to Ubuntu (from Windows) and have been learning a TON off of forums and messing around with my maching...although I did have to reinstall my OS because I somehow crashed my software manager in the first week ;-)

Thanks, in advance, for any help.
Oldtime

---

### Post by stlsaint on 2009-09-21
sudo apt-get update 

run that first then try adding key again...if not you can add the key via sources list in System>admin>authentication!

---

### Post by oldtime on 2009-09-21
Thanks for the ideas. 
When I run sudo apt-get update, it gives me the same error - it "hits" all my usual sources and packages (like those for Hardy), but "err" on my sourceforge stuff that I need for Bibus. Here's what it looks like:

Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [29.3kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [5401B]
Fetched 949kB in 4s (228kB/s)                       
W: Failed to fetch [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Packages.gz](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Packages.gz)  302 Found
W: Failed to fetch [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Sources.gz](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Sources.gz)  302 Found
E: Some index files failed to download, they have been ignored, or old ones used instead.

When I run sudo apt-key list (I wanted to see if the Bibus stuff was there) it gave me this:

me@mycomputer:~$ sudo apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024R/ADDE29B2 2009-01-22
uid                  Launchpad PPA for tobydox

pub   1024D/EB7A4D95 2009-04-21
uid                  Pierre Martineau (used to sign bibus releases) <pmartino@users.sourceforge.net>
sub   2048g/2583330C 2009-04-21

And when I go to the software sources manager through system>admin>software sources, it lists "Pierre Martineau (used to sign bibus releases) <pmartino@users.sourceforge.net>" 
As a TOTAL newbie, this at least does indicate that I've added sourceforge to my trusted software sources (my repository? right?). 

But I still don't understand how to get my computer to recognize where to look for the bibus files. I don't know why the installation instructions ([http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu](http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu)) are failing my machine. Further, it's IMPORTANT that I get this to work. I used to run Endnote on Windows and it's critical for my work. I genuinely like learning about computers with Ubuntu, but this one is a pain! 

Any ideas? Thanks, stlsaint, for the suggestion. I hope I'm not screwing up what you said.

---

### Post by oldtime on 2009-09-21
Seems like another option would be to just download the .deb package manually from the bibus website ([http://sourceforge.net/projects/bibus-biblio/](http://sourceforge.net/projects/bibus-biblio/)). 
When I try to install the 1.4.3-3 package, I get the error that "error: Dependency is not satisfiable: python-central". When I go to my Synaptic Package Manager, it shows that I have python-central 0.6.7ubuntu0.1 installed. So that just confuses me. Why would I get an error about my python-central from the install window when my computer already has it?
So then there are a bunch of packages I could download from ([http://sourceforge.net/projects/bibus-biblio/files](http://sourceforge.net/projects/bibus-biblio/files)). I was thinking an early version (like 1.0.0.tgz) would load without the "python-central" dependency issue. But, coming from a Windows background, I have no clue which XX.py script I should run to start the install. 
I suppose I would use the alt+F2 command to "run" one of the files, but I don't know which one because none of them are labeled "install". Confusions like this encouraged me to learn how to use the terminal early on, and I've been fairly successful with that.

Suggestions? Either for (a) solving my original problem and doing it from the terminal, or (b) running a script from the bibus-1.0.0.tgz package? (I think that's the package I should use for Hardy, but I'm not sure).

Thanks for any help. I'm confused and frustrated. Sorry about being wordy - it seems like more info tends to help with these posts, at least as far as I can tell from the many I've surfed in the past 3 months.

---

### Post by beathovn on 2009-09-28
Hi oldtime,

the .deb version 1.4.3-3 at sourceforge depends on python-central >= 0.6.11, that is why it doesn't work for you - your python-central is too old. But you may try version 1.4.3-2 from sourceforge, which depends on python-central >= 0.6.5. That should work.

By the way, if you like, you may want to express your interest in bibus over at the scientific ubuntu team, where I asked for somebody taking care of bibus in Ubuntu - trying to get backports to older Ubuntu releases and so on. Have a look here: [https://answers.edge.launchpad.net/scientific-ubuntu/+question/83839](https://answers.edge.launchpad.net/scientific-ubuntu/+question/83839)
It wouldn't hurt, if anybody actually running Ubuntu and having an interest in bibus would indicate to them, that there are users which care about bibus... ;-) I am just the Debian maintainer of bibus - unfortunately I lack both time and expertise to care about Ubuntu specifically.

Good luck,
Jan

---

### Post by oldtime on 2009-11-11
Thanks Jan!
I actually posted this to the "general help" and got my answer - or, at least an answer that worked well enough for me. I was directed to the bibus_1.4.2-1_all.deb file, and that installed fine. I was also able to export my old endnote libraries as...hmmm...remember...I think .txt files, and Bibus imported them just fine. Nice app! Not that it's your job, but it would be sweet if it were available in the repository for future Ubuntu releases. I don't plan on upgrading until the next Ubuntu LTS version comes out, so I'll see then, I guess.
Thanks.
Brandon

So I should mark this as "solved" too, well, more or less - folks can check it out here:
[http://ubuntuforums.org/showthread.php?t=1277161](http://ubuntuforums.org/showthread.php?t=1277161)

---

### Post by beathovn on 2009-11-12
Bibus is in the official Ubuntu repositories starting from Karmic, see
[http://packages.ubuntu.com/search?keywords=bibus](http://packages.ubuntu.com/search?keywords=bibus)

So it's already done... ;-)

---

