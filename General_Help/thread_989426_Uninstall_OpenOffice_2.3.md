---
title: "Uninstall OpenOffice 2.3"
date: 2008-11-21
forum: General Help
---

### Post by rpainter on 2008-11-21
I am running Ubuntu 8.10, and everything is going great. I have OpenOffice 2.4.1 installed on the computer, and it is working good. However, I noticed today, that when I double click an Excel Spreadsheet, it opens in OpenOffice 2.3. 

My question is: How do I remove OO 2.3 from my system, so that the spreadsheets will open in 2.4? Thanks for your help.

---

### Post by ibuclaw on 2008-11-21
Check if it is installed via the repository.

What is the output of dpkg -l in the commandline?

```
dpkg -l "openoffice*" | grep -v "<none>"
```


Regards
Iain

---

### Post by rpainter on 2008-11-21
I checked Synaptic, and it is not in there.

Here is the output of the above command:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version                                              Description
+++-==========================================-====================================================-============================================
ii  openoffice.org-base-core                   1:2.4.1-11ubuntu2                                    OpenOffice.org office suite -- libdba
ii  openoffice.org-calc                        1:2.4.1-11ubuntu2                                    OpenOffice.org office suite - spreadsheet
ii  openoffice.org-common                      1:2.4.1-11ubuntu2                                    OpenOffice.org office suite architecture ind
ii  openoffice.org-core                        1:2.4.1-11ubuntu2                                    OpenOffice.org office suite architecture dep
ii  openoffice.org-core01                      2.4.1-9311                                           Core module for OpenOffice.org 2.4
ii  openoffice.org-core02                      2.4.1-9311                                           Office core module for OpenOffice.org 2.4
ii  openoffice.org-core03                      2.4.1-9311                                           Office core module for OpenOffice.org 2.4
ii  openoffice.org-core03u                     2.4.1-9311                                           Office core module for OpenOffice.org 2.4
ii  openoffice.org-core04                      2.4.1-9311                                           Office core module for OpenOffice.org 2.4
ii  openoffice.org-core04u                     2.4.1-9311                                           Office core module for OpenOffice.org 2.4
ii  openoffice.org-core05                      2.4.1-9311                                           Office core module for OpenOffice.org 2.4
ii  openoffice.org-core05u                     2.4.1-9311                                           Office core module for OpenOffice.org 2.4
ii  openoffice.org-core06                      2.4.1-9311                                           Office core module for OpenOffice.org 2.4
ii  openoffice.org-core07                      2.4.1-9311                                           Office core module for OpenOffice.org 2.4
ii  openoffice.org-core08                      2.4.1-9311                                           Office core module for OpenOffice.org 2.4
ii  openoffice.org-core09                      2.4.1-9311                                           Office core module for OpenOffice.org 2.4
ii  openoffice.org-core10                      2.4.1-9311                                           Office core module for OpenOffice.org 2.4
rc  openoffice.org-debian-menus                2.4-9268                                             OpenOffice.org desktop integration
ii  openoffice.org-draw                        1:2.4.1-11ubuntu2                                    OpenOffice.org office suite - drawing
ii  openoffice.org-emailmerge                  1:2.4.1-11ubuntu2                                    E-Mail Mailmerge component for OpenOffice.or
rc  openoffice.org-filter-binfilter            1:2.4.1-1ubuntu2                                     Legacy filters (e.g. StarOffice 5.2) for Ope
ii  openoffice.org-gnome-integration           2.4.1-9311                                           Gnome integration module for OpenOffice.org 
ii  openoffice.org-graphicfilter               2.4.1-9311                                           Graphic filter module for OpenOffice.org 2.4
ii  openoffice.org-headless                    1:2.4.1-11ubuntu2                                    Headless VCL plugin for OpenOffice.org
ii  openoffice.org-help-en-us                  1:2.4.1-9ubuntu1                                     English_american help for OpenOffice.org
ii  openoffice.org-impress                     1:2.4.1-11ubuntu2                                    OpenOffice.org office suite - presentation
ii  openoffice.org-javafilter                  2.4.1-9311                                           Java filter module for OpenOffice.org 2.4
ii  openoffice.org-kde-integration             2.4.1-9311                                           KDE integration module for OpenOffice.org 2.
ii  openoffice.org-math                        1:2.4.1-11ubuntu2                                    OpenOffice.org office suite - equation edito
ii  openoffice.org-onlineupdate                2.4.1-9311                                           Online update modul for OpenOffice.org 2.4
ii  openoffice.org-pyuno                       2.4.1-9311                                           Pyuno module for OpenOffice.org 2.4
ii  openoffice.org-style-human                 1:2.4.1-11ubuntu2                                    Human symbol style for OpenOffice.org
ii  openoffice.org-testtool                    2.4.1-9311                                           Testtool module for OpenOffice.org 2.4
rc  openoffice.org-thesaurus-en-us             1:2.2.0-2ubuntu1                                     English Thesaurus for OpenOffice.org
ii  openoffice.org-writer                      1:2.4.1-11ubuntu2                                    OpenOffice.org office suite - word processor
ii  openoffice.org-xsltfilter                  2.4.1-9311                                           XSLT filter samples module for OpenOffice.or

```

---

### Post by ibuclaw on 2008-11-21
OK, I see no reason why it should be 2.3 if apt is correct...

Right-click on the "**Applications**" tab and select "**Edit Menus**"

Click "**Office**" and Double-click on one of the OpenOffice.org apps (ie: OpenOffice.org Word Processor) and can you state what it says in the "**Command**" box ?

Mine says:
> ooffice -writer %U

Regards
Iain

---

### Post by rpainter on 2008-11-21
OK. Did that. Is says:

> ooffice -writer %U

I also noticed a LOT of 2.3 stuff in there (none are checked). The command for "OpenOffice.org 2.3 Calc is:

> openoffice.org2.3 -calc %U

Don't know if this helps.

---

### Post by ibuclaw on 2008-11-21
Yeah, it does...

I don't know how OpenOffice 2.3 came to be installed on your filesystem... unless you aren't the only user (or you aren't telling me something ;) )

Just rename all shortcuts to the "**ooffice**" name for the moment.


ie:
> openoffice.org2.3 -calc %U 

becomes

> ooffice -calc %U

and do it for the rest too.

Regards
Iain

---

### Post by rpainter on 2008-11-21
OK. Ifigured out how to make the files open in the correct version, but I would still like to know how to remove the 2.3 stuff.

---

### Post by ibuclaw on 2008-11-21
Run
```
sudo updatedb
```
in the terminal (this updates your locate file database, which maps all files in your filesystem)

Then run:
```
locate openoffice.org2.3
```
or
```
locate openoffice2.3
```
or
```
locate 2.3 | grep office
```
That should help you track down those files/folders ;)


Regards
Iain

---

### Post by rpainter on 2008-11-21
> **tinivole said:**
> I don't know how OpenOffice 2.3 came to be installed on your filesystem... unless you aren't the only user (or you aren't telling me something ;) )

Regards
Iain

I would assume that it is left over from a previous version of Ubuntu? That's the only thing that I can think of. I have never "manually" installed OO, just used whatever was with the OS.

Instead of renaming the shortcuts, I figured out that I could go to the properties of an Excel file, and choose what program to use. I now have it opening in 2.4

---

### Post by ibuclaw on 2008-11-21
> **rpainter said:**
> I would assume that it is left over from a previous version of Ubuntu? That's the only thing that I can think of. I have never "manually" installed OO, just used whatever was with the OS.

Instead of renaming the shortcuts, I figured out that I could go to the properties of an Excel file, and choose what program to use. I now have it opening in 2.4

Ah, ok. That would explain it partially.

Though I never had that in the time I upgraded from Hardy to Intrepid Alpha 1, but Hey-Ho. :)

Good luck and Happy Ubuntu-ing

Regards
Iain

---

### Post by rpainter on 2008-11-21
> **tinivole said:**
> Run
```
sudo updatedb
```
in the terminal (this updates your locate file database, which maps all files in your filesystem)

Then run:
```
locate openoffice.org2.3
```
or
```
locate openoffice2.3
```
or
```
locate 2.3 | grep office
```
That should help you track down those files/folders ;)


Regards
Iain
OK. I ran
```
locate openoffice.org2.3
```
It came up with a TON of files. DO I just go in and delete all of those files and directories?

---

### Post by ibuclaw on 2008-11-21
I'd be cautious if it were me.
Though if you are absolutely certain that they aren't needed no more... Then I won't try to give reasons as to why you shouldn't, as there is no trace of OpenOffice2.3 on my system.

Regards
Iain

---

