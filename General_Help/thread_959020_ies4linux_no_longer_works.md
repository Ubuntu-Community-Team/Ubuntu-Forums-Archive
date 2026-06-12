---
title: "ies4linux no longer works?"
date: 2008-10-26
forum: General Help
---

### Post by figo2476 on 2008-10-26
Hi:

Try to install ies4linux and it generates following errors:

----------------------------------------------------------------------
Installing IE 6
  Initializing
  Creating Wine Prefix
  Extracting CAB files
/home/me/.ies4linux/downloads/ie6/EN-US/ADVAUTH.CAB: No such file or directory
/home/kenpeter/.ies4linux/downloads/ie6/EN-US/CRLUPD.CAB: No such file or directory
/home/kenpeter/.ies4linux/downloads/ie6/EN-US/HHUPD.CAB: No such file or directory
/home/kenpeter/.ies4linux/downloads/ie6/EN-US/IEDOM.CAB: No such file or directory
/home/kenpeter/.ies4linux/downloads/ie6/EN-US/IE_EXTRA.CAB: No such file or directory
/home/kenpeter/.ies4linux/downloads/ie6/EN-US/IE_S*.CAB: No such file or directory
/home/kenpeter/.ies4linux/downloads/ie6/EN-US/SETUPW95.CAB: No such file or directory
/home/kenpeter/.ies4linux/downloads/ie6/EN-US/VGX.CAB: No such file or directory
 An error occured when trying to cabextract some files.
----------------------------------------------------------------------

Basically, it is not able to download those files anymore. 
The download addressed from the install.sh are

URL_IE6_CABS=http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP

download [http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE](http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE)

download [http://activex.microsoft.com/controls/vc/mfc42.cab](http://activex.microsoft.com/controls/vc/mfc42.cab)

download [http://download.microsoft.com/download/win98SE/Update/5072/W98/EN-US/249973USA8.exe](http://download.microsoft.com/download/win98SE/Update/5072/W98/EN-US/249973USA8.exe)

Did someone find a solution for this? The worse, I may have to install virtual box, or the like.

---

### Post by TransitMan on 2008-10-26
Have you installed "cabextract" from the repos?
If not, then this is why you are having problems.

---

### Post by figo2476 on 2008-10-26
I have cabextract 1.2 in my linux box. If you try to copy and paste links in my first post to firefox, most of them are not working. I guess that is the problem behind.

---

### Post by TransitMan on 2008-10-26
I just downloaded all three programs from your post above using Opera 9.61 without a problem.

Might be something else keeping you from getting these files.

---

### Post by figo2476 on 2008-10-26
I don't think you are able to access this link.

[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP](http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP)

---

### Post by TransitMan on 2008-10-26
Maybe not that one, but I do have a copy of IE6 stand-alone for installation.

---

### Post by figo2476 on 2008-10-29
"Maybe not that one, but I do have a copy of IE6 stand-alone for installation." --- Is there any way I can download a IE6 stand alone version for Linux?

---

### Post by TransitMan on 2008-10-29
ies4linux is the only way you can a stand-alone IE browser installed.

If you want to go the WINE route, you could install IE that way.
A note though, ies4linux is based on a WINE derivitave.

---

