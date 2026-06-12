---
title: "Evince doesn't print dvi format"
date: 2008-07-14
forum: General Help
---

### Post by Urik on 2008-07-14
Hello everyone. I'm linux newbie, so trying to describe the problem as I can :)

There is a problem with evince, while trying to print dvi postscript files. It opens it, but when i'm trying to print, the program hangs with the following flood in console:

~$ evince
cairo context error: NULL pointer
cairo context error: NULL pointer
cairo context error: NULL pointer
....
cairo context error: NULL pointer

The other applications, like KGhostView etc, print it normally.
The problem exists with dvi format only, e.g. .pdf and .ps files are printed.


~$ dpkg --list evince*

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ &#1048;&#1084;&#1103;                          &#1042;&#1077;&#1088;&#1089;&#1080;&#1103;                    &#1054;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;
+++-===============================-===============================-==============================================================================
ii  evince                          2.22.2-0ubuntu1                 Document (postscript, pdf) viewer
un  evince-gtk                      <none>                        (No description available)




All libraries are up-to-date, including poppler and cairo.
I found some descriptions on launchpad about this bug, but it's figures out there as "fixed".

Any suggestions?
WBR, Urik.

---

