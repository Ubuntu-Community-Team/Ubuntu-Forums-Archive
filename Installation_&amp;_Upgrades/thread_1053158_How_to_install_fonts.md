---
title: "How to install fonts???????????"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by markomk on 2009-01-28
How or where to install new fonts?? :S in Windows is easy just copy the fonts and paste in to font folder but how to install on Ubuntu?

---

### Post by em4r1z on 2009-01-28
Create a folder named **.fonts** inside your personal folder and copy the desired fonts there. Restart the application where you want to use the new fonts. In Nautilus, you'll need to enable the hidden files view feature (Ctrl+H) to see the folder.

---

### Post by markomk on 2009-01-28
> **em4r1z said:**
> Create a folder named **.fonts** inside your personal folder and copy the desired fonts there. Restart the application where you want to use the new fonts. In Nautilus, you'll need to enable the hidden files view feature (Ctrl+H) to see the folder.


I like to use with OpenOffice

---

### Post by ok1958 on 2009-01-28
i just did this, it installed all the standard MS fonts:

sudo apt-get install msttcorefonts

---

### Post by markomk on 2009-01-28
> **ok1958 said:**
> i just did this, it installed all the standard MS fonts:

sudo apt-get install msttcorefonts


well i like to install Macedonian fonts for OpenOffice.

---

### Post by xyepblra on 2009-02-17
Can you modify this request specifying the path to a certain font to be installed?> **ok1958 said:**
> sudo apt-get install msttcorefontsI need some Chinese fonts to be installed, but nothing regarding new fonts seems to work in my system.

---

### Post by NJ0E on 2009-02-18
I did the same install function and this is what I got back.  Also ried it in Synaptic manager.  Any work around?  I am not dual booting.  Using 


nj0e@nj0e-laptop:~$ sudo apt-get install msttcorefonts
[sudo] password for nj0e: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 247 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up msttcorefonts (2.5) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

