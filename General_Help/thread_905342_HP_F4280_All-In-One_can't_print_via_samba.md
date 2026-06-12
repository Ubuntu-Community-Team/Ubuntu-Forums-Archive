---
title: "HP F4280 All-In-One can't print via samba"
date: 2008-08-30
forum: General Help
---

### Post by MikeB23930 on 2008-08-30
I've recently installed an HP F4280 All-In-One printer on my small home network.  I got it working for local printing using HPLIP 2.8.7, but it does'nt show up when I try to install it on another Kubuntu 8.04 computer on my network.  It does, however, show up when I use smb4k to connect to the computer that it is connected to and via smb4k I can print a simple Kate text file, which I think means that the printer is being shared by samba, but when I try to print an Open Office file I get the following message:

The mimetype "application/vnd.oasis.opendocument.text" is not supported. Please convert the file to PostScript or PDF.

Any help setting up this printer to allow direct printing of files via samba would be most appreciated.  Barring that, instructions on converting files to postsript would be helpful.

Thanks,

Mike

Edit:  Installing HPLIP 2.8.7 on the client machine made the HP F4280 visible in the add printer wizard.  (I should have had enough sense to do that in the first place I guess.)  I then configured the HP F4280 as a generic postscript printer and now it prints well.

---

### Post by gjoellee on 2008-08-30
check this out:)
[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

---

