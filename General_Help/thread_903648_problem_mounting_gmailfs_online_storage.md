---
title: "problem mounting gmailfs online storage"
date: 2008-08-28
forum: General Help
---

### Post by miabe on 2008-08-28
hello out there,

I found this very interesting guideline on how to use your googlemail account as a free online storage and wanted to give it a try:

[http://www.jbip.net/content/how-free-encrypted-online-storage-ubuntu](http://www.jbip.net/content/how-free-encrypted-online-storage-ubuntu)

I solved some problems during install but unfortunately after everything seems to work my drive does not appear when I mount it.

so here is what I did: 

I followed the guideline, got an error about fuse-tools and installed fuse-utils instead.

Then I got the HTTP Error 400 described here:
[http://ubuntuforums.org/showthread.php?t=596352](http://ubuntuforums.org/showthread.php?t=596352)

I installed latest version of libgmail according to this page:
[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-installing.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-installing.html)

and got back the error that mechanize is missing and installed it via synaptic.

I created a folder in /media/gmail and tried to mount it via

sudo mount.gmailfs /usr/local/bin/gmailfs.py /media/gmail/ -o username=***,password=***,fsname=zOlRRa

I did not return any error but my /media/gmail folder disappears (but is still there as I cannot create a new one) and I don't see any drive I can access.
also trying it via fstab entry

/usr/local/bin/gmailfs.py /media/gmail/ gmailfs 
noauto,username=***,password=***,fsname=zOlRRa
did not work.

any ideas what I can do?

---

