---
title: "Latex install and uninstall"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by wangx on 2008-12-18
Hello,
   I tried to installed Latex in kubundu, but as a new user, I made a mistake soon. I tried to compile a tex code and found it has an error of finding some .sty files, then I assumed that my latex installation is not proper. My mistake is that I tried to remove the current latex by using 'rm', instead of sudo adt-get remove latex. Now after some files in texmf-live have been removed, i then tried to uninstall the latex by sudo adt-get remove latex (so that i can install it again), and the results of removal is:
-----------
sudo apt-get autoremove latex                                    
Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
Package latex is not installed, so not removed                                  
The following packages were automatically installed and are no longer required: 
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic                         
The following packages will be REMOVED:                                         
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic                         
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.                  
After this operation, 52.0MB disk space will be freed.                          
Do you want to continue [Y/n]? Y                                                
(Reading database ... 114100 files and directories currently installed.)        
Removing linux-headers-2.6.27-7-generic ...                                     
Removing linux-headers-2.6.27-7 ...   
---------------------------------



But obviously Latex is not removed from my system. When i type Latex in the command line, it has such results:
---
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
**
-----

I do not know what to do now. It seems that i can not remove the old latex installation, neither install a new one. I need help and any suggestion will be highly appreciated !


xf

---

### Post by unutbu on 2008-12-18
Part of the problem is that there is no package called 'latex'.
There are packages called things like 'latex-209-base', but nothing called plain 'latex'. 

We'll need the correct package name in order to remove it.

Please post the output of 
```
dpkg --get-selections | grep tex
```
It will show all the packages with the letters 'tex' in their names.

---

### Post by wamgx on 2012-09-11
> patrick@patrick-desktop:~$ sudo apt-get autoremove texlive-full 
[sudo] password for patrick:  
E: dpkg a été interrompu. Il est nécessaire d'utiliser « sudo dpkg --configure -a » pour corriger le problème. 
patrick@patrick-desktop:~$ dpkg --get-selections | grep tex

texlive-lang-norwegian				install 
texlive-lang-other				install   
texlive-lang-polish				install 
 texlive-lang-portuguese				install 
 texlive-lang-spanish				install 
 texlive-lang-swedish				install 
 texlive-lang-tibetan				install 
 texlive-lang-ukenglish				install 
 texlive-lang-vietnamese				install 
 texlive-latex-base				install 
 texlive-latex-base-doc				install 
 texlive-latex-extra-doc				install 
 texlive-latex-recommended			install 
 texlive-latex-recommended-doc			install 
 texlive-latex3					install 
 texlive-luatex					install 
 texlive-math-extra				install 
 texlive-metapost				install 
 texlive-metapost-doc				install 
 texlive-music					install 
 texlive-pictures				install 
 texlive-plain-extra				install 
 texlive-pstricks				install 
 texlive-pstricks-doc				install 
 texlive-science					install 
 texlive-science-doc				install 
 texlive-xetex					install 
 thailatex					install
Here it is ;)

---

