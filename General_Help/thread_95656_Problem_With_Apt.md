---
title: "Problem With Apt"
date: 2005-11-27
forum: General Help
---

### Post by GreenHawkIA on 2005-11-27
Is there any way to get apt to just ignore a package?  I tried to install Lilypond, but the installation failed part way through, and though I have tried to reinstall, remove, and fix the installation, none of them complete - all giving some variation of this message:
> dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
I have also tried all the above using just the lilypond-data portion of the package.  I also tried deleting the file manually from the cache - and synaptic still remembers it being there, so keeps returning the message, and prompting me to download the file again.  If I could just get the error message to go away - clean uninstall or not, the system is working fine, other than I can't do anything at all with apt now, and the install never appeared to get past the unpacking stage.  Any ideas out there?

---

### Post by Xian on 2005-11-27
Try this set of commands:

```

$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
$ sudo dpkg --configure -a
$ sudo apt-get -f install
```

---

### Post by GreenHawkIA on 2005-11-27
Xian - 
I tried your commands, but had no success.  I did, however, get a whole new set of error messages.  With the first I got this:
> /var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
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

No error for the second command, but for the third I got:
> Unpacking replacement lilypond-data ...
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
Both occurred in the same place - while unpacking the replacement file.  Any ideas?
Thanks for all your help.

---

### Post by Xian on 2005-11-27
[QUOTE=GreenHawkIA]
Any ideas?
[/QUOTE]

This should sort it out for you:

```
$ sudo apt-get install tetex-bin
$ sudo dpkg --configure -a
```

---

### Post by GreenHawkIA on 2005-11-27
Ahh...you saved me!  Thank you so much.  But now I just have one more question, if it's not too much.  What resources did you use to find this out so that I can try and figure stuff like it out on my own in the future?  Thanks again!  BTW, I really like the quote in your profile.

---

### Post by Xian on 2005-11-27
[QUOTE=GreenHawkIA]What resources did you use to find this out so that I can try and figure stuff like it out on my own in the future?[/QUOTE]

1. Your terminal output included the following:
/usr/bin/kpsewhich: No such file or directory

So, we know that the kpsewhich library is missing.

2. To find that library goto [Ubuntu Packages](http://packages.ubuntu.com/) and scroll to the section entitled, "Search the contents of packages". Here you put in the word kpsewhich and complete the search. This will tell you from which the package the library comes from.

3. The result is: [ Kpsewhich Package Association](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=kpsewhich&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386).
Notice that tetex-bin is what you need to install to get that file.

---

### Post by GreenHawkIA on 2005-11-27
Merci.

---

