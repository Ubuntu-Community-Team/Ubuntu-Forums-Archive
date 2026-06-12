---
title: "problem with pre installations for ms office2007"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by sam1948 on 2009-03-13
when trying to install 
:~$ wine msiexec /i ./Desktop/msxml3.msi

i get this error:
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:sfc:SFC_3 0

when rting this :
m:~$ sh winetricks msxml3 

i'm getting this error:
Using native,builtin override for following DLLs: msxml3
Executing wine regedit /home/oz/.wine/drive_c/winetrickstmp/override-dll.reg
Executing wine msiexec /i /home/oz/.winetrickscache/msxml3.msi
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
Note: command 'wine msiexec /i /home/oz/.winetrickscache/msxml3.msi' returned status 103.  Aborting.

any idea ?

---

### Post by pytheas22 on 2009-03-13
I think you need to make a few special modifications to wine in order to install Office 2007 (earlier versions of Office 'just work' in wine).  There's a guide [here]("http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-804/") that might be useful.

---

### Post by sam1948 on 2009-03-14
I tried that how to but the installer just stoped in the middle
I just want to make pptx open with ppt viewer with the support of the 
FileFormatConverters.exe
but it just doesn't work

---

### Post by pytheas22 on 2009-03-14
Sorry that didn't work.  Did you wait a little while when the installer stopped?  It might kick back in if you get a it a few minutes.  You might also have better luck if you uninstalled with completely (use the 'remove completely' option in Synaptic), delete the .wine directory in your home folder and tried again with a fresh installation.

Also, I'm not sure exactly what you're trying to do, but you could use an [online converter]("http://zamzar.com/") to convert your pptx files to ppt, and then play them in either OpenOffice or PowerPoint Viewer 2003, which should install in wine with fewer problems.  OpenOffice will also support pptx (and docx, etc.) files directly on Ubuntu if you [install a plugin]("http://librarycomputerguy.wordpress.com/2007/10/20/open-ms-word-2007-docx-documents-in-ubuntu/").

---

### Post by sam1948 on 2009-03-15
thanks for those advises

---

### Post by abn91c on 2009-03-15
Openoffice.org 3.0 will open MSO 2007 files without plug-ins, the first time you save then do file>save as> file type>Microsoft office...
this guide will upgrade OOo 2.4 to 3.0  [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by sam1948 on 2009-03-15
I tried OOffice 
it works o.k for simple text docx but pptx with theme or docx with tables are all messed up

---

### Post by pytheas22 on 2009-03-15
> **sam1948 said:**
> I tried OOffice 
it works o.k for simple text docx but pptx with theme or docx with tables are all messed up

Again, I suspect you'd have better luck if you converted them to Microsoft Office 2003 formats, then opened them in either OpenOffice or PowerPoint Viewer 2003 (which should install in wine with no problem, unlike the 2007 version).  In my experience, OpenOffice does have some trouble with docx and pptx formats (which is to be expected since Microsoft won't publish documentation), but it should do better with doc or ppt files.

---

