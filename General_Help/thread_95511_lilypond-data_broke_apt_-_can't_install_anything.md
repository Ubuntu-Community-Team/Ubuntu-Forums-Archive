---
title: "lilypond-data broke apt - can't install anything"
date: 2005-11-26
forum: General Help
---

### Post by halo five on 2005-11-26
Hi, I installed the package lilypond-data from the universe repository, and then tried to remove it.  My system is now in an inconsistent state, I can't install or uninstall anything, it always tries to finish the uninstall of lilypond-data, failling each time.  Here's the output when I try to remove it:

> $ sudo apt-get remove lilypond-data
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  lilypond-data
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 15.4MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing lilypond-data (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
$ Errors were encountered while processing:
 lilypond-data

So apt is telling me to try to install it again.  So I do:

> 
$ sudo apt-get install lilypond-data
Reading package lists... Done
Building dependency tree... Done
lilypond-data is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/4736kB of archives.
After unpacking 0B of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package lilypond-data.
(Reading database ... 70014 files and directories currently installed.)
Preparing to replace lilypond-data 2.6.3-9~breezy1 (using .../lilypond-data_2.6.3-9~breezy1_all.deb) ...
Unpacking replacement lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

No love!  It wants /usr/bin/kpsewhich, which through googling I surmise is in the libkpathsea-dev (correct me if I'm wrong).  However, I can't install libkpathsea-dev because it will try to uninstall lilypond.  Chicken and egg:

> 
$ sudo apt-get install libkpathsea-dev
Reading package lists... Done
Building dependency tree... Done
libkpathsea-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/4736kB of archives.
After unpacking 0B of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 70014 files and directories currently installed.)
Preparing to replace lilypond-data 2.6.3-9~breezy1 (using .../lilypond-data_2.6.3-9~breezy1_all.deb) ...
Unpacking replacement lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
$


I have tried running dpkg --configure -a, because a few apt websites say this is what you do when things get broken.  Please help!!!  If I can provide any more logging to help you guys out, let me know and I will post it.  Otherwise I'll have to be a noob and reinstall the whole OS.  I'd like to avoid that though!

---

### Post by Xian on 2005-11-26
Try this set of commands and let's see where it leaves you:

```
$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb

$ sudo dpkg --configure -a

$ sudo apt-get -f install
```

---

### Post by halo five on 2005-11-26
Thanks for the quick reply! 

I tried:

$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb and got the same error as before - 

> 
$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
(Reading database ... 70014 files and directories currently installed.)
Preparing to replace lilypond-data 2.6.3-9~breezy1 (using .../lilypond-data_2.6.3-9~breezy1_all.deb) ...
Unpacking replacement lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb (--install):
 subprocess new post-removal script returned error exit status 1
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb


I am trying to find a source version of this kpsewhich command to build outside of apt -- it looks to be part of TeTex but I can't find much info on it.  This is the last time I try to install guitar tabbing software :(

---

### Post by halo five on 2005-11-26
Sorted it -- I installed TeTeX-base from the universe repository, which installed kpsewhich as a dependency.  However, the install was broken thanks to lilypond-data, so I then ran dpkg --configure -a, which setup TeTeX-base.   

Then I could install lilypond-data over the corrupted version, and subsequently remove it.

---

### Post by Xian on 2005-11-26
[QUOTE=halo five]/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory[/QUOTE]

This might be of interest to you: [Kpsewhich Package Contents Search](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=kpsewhich&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386)

EDIT: Heh, looks like we were both heading down the same path. Glad you got it fixed. You can use the Ubuntu Packages website to search for package contents, which is where I got the link provided.

---

### Post by halo five on 2005-11-28
Thanks -- Got it bookmarked now ;)

---

### Post by Locutus on 2005-11-28
I am having the exact same problem. I cannot install anything! I fear my ubuntu installation is broken. 

I get the following errors when trying to overwrite:

> root@box:/home/dstahan# dpkg -i --force-overwrite /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
(Reading database ... 131386 files and directories currently installed.)
Preparing to replace lilypond-data 2.6.3-9~breezy1 (using .../lilypond-data_2.6.3-9~breezy1_all.deb) ...
Unpacking replacement lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb (--install):
 subprocess new post-removal script returned error exit status 1
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
root@box:/home/dstahan#


I was able to install some downloaded packages such as tetex-base by using the following command 

> sudo dpkg --configure -a

I tried to uninstall lilypond-data and I get the following:

> apt-get remove lilypond-data Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  lilypond-data
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 15.4MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing lilypond-data (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
root@box:/home/dstahan# Errors were encountered while processing:
 lilypond-data


I am stuck now and do not know where to begin to fix this. Can anyone help or is my installation ubuntu borked?

Thanks for any help.

/Locutus

---

### Post by Locutus on 2005-11-28
Ok, I snooped around some more in the forums and tried this [http://www.ubuntuforums.org/showthread.php?t=95656&highlight=lilypond-data]("http://www.ubuntuforums.org/showthread.php?t=95656&highlight=lilypond-data")

> $ sudo apt-get install tetex-bin
$ sudo dpkg --configure -a

I am relieved that I do not have to reinstall ubuntu.

Thanks again for the excellent help. This is what makes the Ubuntu community so special :KS 

/Locutus

---

