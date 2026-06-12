---
title: "lilypond-data won't uninstall"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by Zugwrack on 2005-12-13
Hey everyone. I tried installing a program for gnome that will allow guitar tab and such to be read/edited,etc. Apparently it needed lilypond-data and lilypond. I fixed the broken package error for lilypond, but dpkg --remove lilypond-data fails with a script error exit 1. Anyone help me figure out how to force it to remove this package? This is also blocking my ability to upgrade some new packages available for download.

Thanks

Zug

---

### Post by eetu on 2005-12-30
[QUOTE=Zugwrack]Hey everyone. I tried installing a program for gnome that will allow guitar tab and such to be read/edited,etc. Apparently it needed lilypond-data and lilypond. I fixed the broken package error for lilypond, but dpkg --remove lilypond-data fails with a script error exit 1. Anyone help me figure out how to force it to remove this package? This is also blocking my ability to upgrade some new packages available for download.[/QUOTE]
I have the same problem. When you try 

```
apt-get remove lilypond-data
```

it tells you the following:

```
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
```

packages.ubuntu.com claims that /usr/bin/kpsewhich can be found from the package tetex-bin. So I installed it, but I still get the same error. When I looked through the file list of tetex-bin, it doesn't actually have /usr/bin/kpsewhich.

I'm kind of lost here.

---

### Post by jschilen on 2006-01-02
Hello,

Thanks to the last post, I went on a tetex package install rampage and installed:
libkpathsea3
tetex-base
tetex-bin
tetex-extra
I think the kpsewhich utility is in the libkpathsea3 package, but I'm not sure. Anyhow, it's in one of these 4.  I was able to then reinstall lily-pond and lily-pond data and then I was able to remove them.

Hope that helps

---

### Post by x1um1n on 2006-01-06
hi,
i have the same god-damned issue, and this looks like a really good solution..

only one prob: apt tries to remove lilypond-data before doing anything else and so dies before doing anything else!!!!!!

i'm a gentoo user by trade and our package management system (portage) has an option that allows you to skip problematic packages.  I'm assuming apt has something similar..

can i ask what it is please, cos i'm starting to tear my hair out :mad: 

thanks in advance..

---

### Post by drakewolf on 2006-01-07
Hello,

Run that 3 lines:

```
aptitude install tetex-bin
dpkg -i /var/cache/apt/archives/tetex-bin_2.0.2-30ubuntu3.4_i386.deb
aptitude remove tetex-bin
```

I want your comments.

---

### Post by x1um1n on 2006-01-07
ok, i get:-

> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following packages are unused and will be REMOVED:
  mozilla-firefox-locale-en-gb
The following NEW packages will be automatically installed:
  libwww-ssl0 perl-tk psutils tetex-base tetex-doc texi2html
The following NEW packages will be installed:
  libwww-ssl0 perl-tk psutils tetex-base tetex-bin tetex-doc texi2html
0 packages upgraded, 7 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/54.9MB of archives. After unpacking 117MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done

Preconfiguring packages ...
(Reading database ... 166675 files and directories currently installed.)
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
Ack!  Something bad happened while installing packages.  Trying to recover:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done


on the first command, followed by:-

> dpkg: error processing /var/cache/apt/archives/tetex-bin_2.0.2-30ubuntu3.4_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/tetex-bin_2.0.2-30ubuntu3.4_i386.deb


and finally:-

> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following packages are unused and will be REMOVED:
  mozilla-firefox-locale-en-gb
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/4736kB of archives. After unpacking 451kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done

Preconfiguring packages ...
(Reading database ... 166675 files and directories currently installed.)
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
Ack!  Something bad happened while installing packages.  Trying to recover:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done


sorry but that didn't seem to have any effect really..

what i need is some way to make apt think there's no issues with lilypond so i can manually delete it, i've done everything i can think of to get rid of it..

i've removed rosegarden which is the only package that depends on it, i've tried asking apt to remove it in various different ways, all to no avail..

if anyone knows which file apt uses to store the list of installed packages and whether its safe to just remove it direct from there, that'd be a huge help..

the only sure way i can think of to sort this out is to go for a complete reinstall an i REALLY don't want to do that, if i wanted this laptop to cause me grief i would've put gentoo on it, at least then the only issues would be with me not getting round to making things work properly!

as always, any help'd be much appreciated..

---

### Post by drakewolf on 2006-01-08
Hi,

[LIST=1]
[*]The lillypond install/deinstall fail because there are a file not found
[*]The file not found is /usr/bin/kpsewhich
[*]That file is in tetex-bin package
[*]When you run the first command, aptitude download that package and storage it in /var/cache/apt/archives, but no can install it (remember, aptitude is broken)
[*]When you run the second command, dpkg decompress and install than package skipping dependences and other stuff
[*]Finally, with third command, you remove all packages, including lillypond

[/LIST]
So, why not run ok? Maybe your tetex-bin version in /var/cache/apt/archives is not equal to my version

What you can do? Write 
dpkg /var/cache/apt/archives/tetex-bin
and hit the tab key, thus the shell complete all, after it, hit Return


I wait your comments. :D

---

### Post by drakewolf on 2006-01-08
[QUOTE=drakewolf]Hi,

[LIST=1]
[*]The lillypond install/deinstall fail because there are a file not found
[*]The file not found is /usr/bin/kpsewhich
[*]That file is in tetex-bin package
[*]When you run the first command, aptitude download that package and storage it in /var/cache/apt/archives, but no can install it (remember, aptitude is broken)
[*]When you run the second command, dpkg decompress and install than package skipping dependences and other stuff
[*]Finally, with third command, you remove all packages, including lillypond

[/LIST]
So, why not run ok? Maybe your tetex-bin version in /var/cache/apt/archives is not equal to my version

What you can do? Write 
dpkg /var/cache/apt/archives/tetex-bin
and hit the tab key, thus the shell complete all, after it, hit Return


I wait your comments. :D[/QUOTE]



Please, somebody that compile my pseudo-english and convert it in native-english :razz:

---

### Post by x1um1n on 2006-01-08
cheers drakewolf,
that sorted it, i don't know why i didn't think to check the package name i was using, i just copied and pasted it..

this machines a PPC, guess i'm still used to x86 :)

thanx for your time, effort & patience

---

### Post by gosh on 2006-01-16
[QUOTE=x1um1n]cheers drakewolf,
that sorted it, i don't know why i didn't think to check the package name i was using, i just copied and pasted it..

this machines a PPC, guess i'm still used to x86 :)

thanx for your time, effort & patience[/QUOTE]

How exactly did you sorted it?
I can't seem to solve this.
I installed the latest version from [http://lilypond.org/web/install/#2.7](http://lilypond.org/web/install/#2.7)
but the error in synaptic stays.

---

### Post by x1um1n on 2006-01-19
yeah, unfortunately that wouldn't work because the problem isn't with lilypond itself but apt/dpkg.  or more precisely with the particular .deb package for lilypond-data.

if you follow the commands supplied by drakewolf you should be able to remove the error.  but make sure you use tab-completion (type the start of the filename then hit tab) for the filenames in case you have slightly different package names as i did.

if that doesn't work post back with the exact errors you're getting and i'll see if i can help; tho i should warn you i'm by no means an expert on debian-based distro's :)

if i can't help you i'm sure someone else will be able to..

---

### Post by cptncatholic on 2006-01-20
yo ho ho!

I just typed:

```
sudo apt-get -f install
```

And it seemed to clear everything up.

Peace be with you!
tc

---

### Post by 4rc on 2006-01-23
I just encountered this too, luckily you guys found out how to fix it and posted it here. 

Shouldn't something be done to the broken package?

---

### Post by x1um1n on 2006-01-24
if ubuntu has a bugzilla it can be posted there and one of the dev's will sort it out, thats normally the way it works..

anyone with a bugzilla a/c can do it, i unfortunately am no longer using ubuntu on my pbook (i've put gentoo on it :)) but anyone on this thread can report it..

---

### Post by KevNice on 2006-02-17
Now I've got this problem as well. I was able to delete the package that was messing up everything, but the file lilypond-data still won't be deleted. I followed DrakeWolf's instructions, and here's what happened: (warning, very long)

**_installing tetex-bin:_**

The following NEW packages will be automatically installed:
  libt1-5 libwww-ssl0 perl-tk psutils tetex-base tetex-doc texi2html
The following NEW packages will be installed:
  libt1-5 libwww-ssl0 perl-tk psutils tetex-base tetex-bin tetex-doc
  texi2html
0 packages upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 54.3MB of archives. After unpacking 116MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/universe lilypond-data 2.6.3-9~breezy1 [4736kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libwww-ssl0 5.4.0-9ubuntu0.5.10 [448kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main tetex-bin 2.0.2-30ubuntu3.4 [3884kB]
Get:4 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/main tetex-base 2.0.2c-8 [14.4MB]
Get:5 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/main libt1-5 5.0.2-3 [141kB]
Get:6 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/main tetex-doc 2.0.2c-8 [28.2MB]
Get:7 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/universe perl-tk 1:800.025-2 [2380kB]
Get:8 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/main psutils 1.17-17 [81.3kB]
Get:9 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/main texi2html 1.66-1.2 [93.8kB]
Fetched 54.3MB in 9m8s (99.0kB/s)

Preconfiguring packages ...
Selecting previously deselected package lilypond-data.
(Reading database ... 69025 files and directories currently installed.)
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
Selecting previously deselected package tetex-base.
Unpacking tetex-base (from .../tetex-base_2.0.2c-8_all.deb) ...
Selecting previously deselected package libt1-5.
Unpacking libt1-5 (from .../libt1-5_5.0.2-3_i386.deb) ...
Selecting previously deselected package libwww-ssl0.
Unpacking libwww-ssl0 (from .../libwww-ssl0_5.4.0-9ubuntu0.5.10_i386.deb) ...
Selecting previously deselected package tetex-bin.
Unpacking tetex-bin (from .../tetex-bin_2.0.2-30ubuntu3.4_i386.deb) ...
Selecting previously deselected package tetex-doc.
Unpacking tetex-doc (from .../tetex-doc_2.0.2c-8_all.deb) ...
Selecting previously deselected package perl-tk.
Unpacking perl-tk (from .../perl-tk_1%3a800.025-2_i386.deb) ...
Selecting previously deselected package psutils.
Unpacking psutils (from .../psutils_1.17-17_i386.deb) ...
Selecting previously deselected package texi2html.
Unpacking texi2html (from .../texi2html_1.66-1.2_all.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack!  Something bad happened while installing packages.  Trying to recover:
Setting up libt1-5 (5.0.2-3) ...

Setting up texi2html (1.66-1.2) ...
Setting up tetex-base (2.0.2c-8) ...

Creating config file /etc/texmf/mktex.cnf with new version

Creating config file /etc/texmf/dvips/config.builtin35 with new version

Creating config file /etc/texmf/updmap.d/00updmap.cfg with new version

Creating config file /etc/texmf/dvipdfm/config with new version

Creating config file /etc/texdoctk/texdocrc with new version

Setting up libwww-ssl0 (5.4.0-9ubuntu0.5.10) ...

Setting up perl-tk (800.025-2) ...
Setting up tetex-bin (2.0.2-30ubuntu3.4) ...

Creating config file /etc/texmf/texmf.d/05TeXMF.cnf with new version

Creating config file /etc/texmf/texmf.d/15Plain.cnf with new version

Creating config file /etc/texmf/texmf.d/45TeXinputs.cnf with new version

Creating config file /etc/texmf/texmf.d/55Fonts.cnf with new version

Creating config file /etc/texmf/texmf.d/65BibTeX.cnf with new version

Creating config file /etc/texmf/texmf.d/75DviPS.cnf with new version

Creating config file /etc/texmf/texmf.d/85Misc.cnf with new version

Creating config file /etc/texmf/texmf.d/90TeXDoc.cnf with new version

Creating config file /etc/texmf/texmf.d/95NonPath.cnf with new version
Generating /etc/texmf/texmf.cnf ...
Creating config file /etc/texmf/texmf.cnf with new version
done
Generating /var/lib/texmf/web2c/fmtutil.cnf ... done
Regenerating /var/lib/texmf/web2c/updmap.cfg ... done
Running initex. This may take some time. ...
fmtutil: /var/lib/texmf/web2c/latex.fmt installed.
fmtutil: /var/lib/texmf/web2c/pdflatex.fmt installed.
fmtutil: /var/lib/texmf/web2c/pdftex.fmt installed.
fmtutil: /var/lib/texmf/web2c/tex.fmt installed.
fmtutil: /var/lib/texmf/web2c/cont-en.efmt installed.
fmtutil: /var/lib/texmf/web2c/elatex.efmt installed.
fmtutil: /var/lib/texmf/web2c/etex.efmt installed.
fmtutil: /var/lib/texmf/web2c/latex.efmt installed.
fmtutil: /var/lib/texmf/web2c/mptopdf.efmt installed.
fmtutil: /var/lib/texmf/web2c/pdfelatex.efmt installed.
fmtutil: /var/lib/texmf/web2c/pdfetex.efmt installed.
fmtutil: /var/lib/texmf/web2c/pdflatex.efmt installed.
fmtutil: /var/lib/texmf/web2c/mf.base installed.
Running updmap. This may take some time. ...


If you want to change the default settings,
use /usr/bin/texconfig to configure teTeX.

Fixing permissions and group of ls-R as specified by debconf ...
mode of `/var/lib/texmf/ls-R' changed to 0664 (rw-rw-r--)
mode of `/var/lib/texmf/ls-R-TEXMFMAIN' changed to 0664 (rw-rw-r--)
mode of `/var/cache/fonts/ls-R' changed to 0664 (rw-rw-r--)
changed group of `/var/lib/texmf/ls-R' to users
changed group of `/var/lib/texmf/ls-R-TEXMFMAIN' to users
changed group of `/var/cache/fonts/ls-R' to users

Setting up psutils (1.17-17) ...

Setting up tetex-doc (2.0.2c-8) ...
mktexlsr: Updating /usr/local/share/texmf/ls-R...
mktexlsr: Updating /var/lib/texmf/ls-R...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN...
mktexlsr: Updating /var/cache/fonts/ls-R...
mktexlsr: Done.

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done



**_depackaging:_**

sudo dpkg -i /var/cache/apt/archives/tetex-bin_2.0.2-30ubuntu3.4_i386.deb
(Reading database ... 79238 files and directories currently installed.)
Preparing to replace tetex-bin 2.0.2-30ubuntu3.4 (using .../tetex-bin_2.0.2-30ubuntu3.4_i386.deb) ...
Unpacking replacement tetex-bin ...
Setting up tetex-bin (2.0.2-30ubuntu3.4) ...
Merging information from /etc/texmf/texmf.d/ into /etc/texmf/texmf.cnf ... done
Regenerating /var/lib/texmf/web2c/fmtutil.cnf ... done
Regenerating /var/lib/texmf/web2c/updmap.cfg ... done
Running initex. This may take some time. ...
fmtutil: /var/lib/texmf/web2c/latex.fmt installed.
fmtutil: /var/lib/texmf/web2c/pdflatex.fmt installed.
fmtutil: /var/lib/texmf/web2c/pdftex.fmt installed.
fmtutil: /var/lib/texmf/web2c/tex.fmt installed.
fmtutil: /var/lib/texmf/web2c/cont-en.efmt installed.
fmtutil: /var/lib/texmf/web2c/elatex.efmt installed.
fmtutil: /var/lib/texmf/web2c/etex.efmt installed.
fmtutil: /var/lib/texmf/web2c/latex.efmt installed.
fmtutil: /var/lib/texmf/web2c/mptopdf.efmt installed.
fmtutil: /var/lib/texmf/web2c/pdfelatex.efmt installed.
fmtutil: /var/lib/texmf/web2c/pdfetex.efmt installed.
fmtutil: /var/lib/texmf/web2c/pdflatex.efmt installed.
fmtutil: /var/lib/texmf/web2c/mf.base installed.
Running updmap. This may take some time. ...


If you want to change the default settings,
use /usr/bin/texconfig to configure teTeX.

Fixing permissions and group of ls-R as specified by debconf ...
mode of `/var/lib/texmf/ls-R' changed to 0664 (rw-rw-r--)
mode of `/var/lib/texmf/ls-R-TEXMFMAIN' changed to 0664 (rw-rw-r--)
mode of `/var/cache/fonts/ls-R' changed to 0664 (rw-rw-r--)


**_removing:_**

sudo aptitude remove tetex-bin
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following packages are unused and will be REMOVED:
  libt1-5 libwww-ssl0 perl-tk psutils tetex-base tetex-doc texi2html
The following packages will be REMOVED:
  tetex-bin
0 packages upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
Need to get 0B/4736kB of archives. After unpacking 116MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done

Preconfiguring packages ...
(Reading database ... 79238 files and directories currently installed.)
Preparing to replace lilypond-data 2.6.3-9~breezy1 (using .../lilypond-data_2.6.3-9~breezy1_all.deb) ...
Unpacking replacement lilypond-data ...
(Reading database ... 80182 files and directories currently installed.)
Removing tetex-bin ...
Removing libt1-5 ...
Removing libwww-ssl0 ...
Removing perl-tk ...
Removing psutils ...
Removing tetex-base ...
Removing tetex-doc ...
Removing texi2html ...
Setting up lilypond-data (2.6.3-9~breezy1) ...
/var/lib/dpkg/info/lilypond-data.postinst: line 15: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing lilypond-data (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lilypond-data
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack!  Something bad happened while installing packages.  Trying to recover:
Setting up lilypond-data (2.6.3-9~breezy1) ...
/var/lib/dpkg/info/lilypond-data.postinst: line 15: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing lilypond-data (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lilypond-data
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done



I have no idea what's going on here. Please help!!

---

### Post by rpj911 on 2006-02-18
Thanks to all that posted above on how to get out of lillypond-data hell...

To get back to being able to use apt-get or use aptitude, 
- do a rm on /usr/kpsewhich*
- install tetex-bin as advised above
- reinstall lilypond-data as described above, note above about using tab to fill in remainder of name on your particular system *very important*
- uninstall lilypond-data

Whew, thought I was back in the days of Fedora there for a minute...

How do I think I got into this mess in the first place?

#1 installing musical notation software...sofiere I think
#2 removing a dependency lillypond, because I didn't think I needed it
Thanks again to all..

---

### Post by hitjim on 2006-02-25
**[SIZE="3"]thankyou google, and thank you guys[/SIZE]**

---

### Post by christianstritzelberger on 2006-03-12
Thanks a BIIIIG lot. According to this thread I've finally been able to kick this D*RN lilypond the F*CK off my system... 
Didn't believe in it anymore....:mrgreen: :mrgreen: :mrgreen:

---

### Post by unfear on 2006-03-29
hey, thanks guys, yet I can sleep nice

---

### Post by munroe on 2006-05-07
Hey, I found this thread after fixing the problem myself. The problem lies within a few lazy developers who decided not to do a bit of error checking. There are four lines in 
/var/lib/dpkg/info/lilypond-data.postrm

```
TEXMFMAIN=`/usr/bin/kpsewhich -expand-var '$TEXMFMAIN'`
: ${TEXMFMAIN:=$std_TEXMFMAIN}
VARTEXFONTS=`/usr/bin/kpsewhich -expand-var '$VARTEXFONTS'`
: ${VARTEXFONTS=$std_VARTEXFONTS}
```

Change them to this
```
#TEXMFMAIN=`/usr/bin/kpsewhich -expand-var '$TEXMFMAIN'`
#: ${TEXMFMAIN:=$std_TEXMFMAIN}
#VARTEXFONTS=`/usr/bin/kpsewhich -expand-var '$VARTEXFONTS'`
#: ${VARTEXFONTS=$std_VARTEXFONTS}
```

Which comments them out. See where it says /usr/bin/kpsewich. If the developer had checked to see if that directory existed before fiddling with it, none of us would of been in this sticky situation.

Now that you've commented out those lines run

```
sudo apt-get remove lilypond-data
```

and everything should be hunky-dory.

---

### Post by ubu_dynamite on 2006-05-17
sudo touch /usr/bin/kpsewhich
sudo chmod 777 /usr/bin/kpsewhich

sudo apt-get remove lilypond-data

sudo rm /usr/bin/kpsewhich

Workt for me.

---

### Post by munroe on 2006-06-19
Well if you want to add a file to your system, you could just use 

sudo touch /usr/bin/kpsewich 

could you not?

---

