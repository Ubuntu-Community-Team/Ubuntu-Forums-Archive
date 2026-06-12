---
title: "Evince doesn't open all pdf files"
date: 2008-07-31
forum: General Help
---

### Post by muadnu on 2008-07-31
I've been having this problem for a while already. I'd say 1 out of 3 or 4 times I try to open a pdf file with Evince, it seems to try to, but then nothing happens. The window list shows the window with the right title, but as soon as I click it it's closed and the file is never shown. I don't see a pattern on which files it doesn't open, it can be files I just downloaded or files I've been working on for a while.

One solution would be to start using another viewer, but I haven't found any that I like better. Acrobat is too bloated, and I want at least the functionality of Evince...

---

### Post by cmnorton on 2008-07-31
Will another viewer open these files, like Xpdf or Kpdf? You can use Kpdf in Ubuntu.

Suggest you post a bug about this in Ubuntu Launchpad [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu) and attach one or two of the pdf files that don't load.

Make sure to give your Evince version number.

---

### Post by muadnu on 2008-08-01
Yes, I forgot to mention that... Every other viewer I tried usually opens them (xpdf, kpdf, acrobat, epdfview).

I'll post a bug in launchpad, thanks for the suggestion.

---

### Post by ubuntubrian on 2008-08-05
I have been working on this for hours and haven't gotten anywhere. I have Hardy installed on my G3Powerbook and evince works fine. On my G4 TiBook it won't open pdf's but it does open ps docs. I checked my .local/share/mime directory on the G4 and there is nothing in there that refers to either ps or pdf. The G3 has a mimeapps.list in .local/share/applications file with:
> [Added Associations]
application/pdf=userapp-evince-O6PU8T.desktop;
application/x-shockwave-flash=userapp-gnash-HWEXEU.desktop;
application/vnd.rn-realmedia=totem-gstreamer.desktop;mplayer.desktop;

Whereas the G4 only has:
> [Added Associations]
application/octet-stream=userapp-gedit-VZ2AFU.desktop;

There are mime files in /etc/mime.types that refer to:
> application/pdf					pdf
application/pgp-encrypted
application/pgp-keys				key
application/pgp-signature			pgp
application/pics-rules				prf
application/pkcs10
application/pkcs7-mime
application/pkcs7-signature
application/pkix-cert
application/pkix-crl
application/pkixcmp
application/postscript				ps ai eps

among many others.

Also have:
/usr/share/mime/application/pdf.xml and 
/usr/share/mime/application/postscript.xml

The /usr/share/mime/application/pdf.xml has:
```
<mime-type type="application/pdf">
&#8722;
<!--
Created automatically by update-mime-database. DO NOT EDIT!
-->
<comment>PDF document</comment>
<comment xml:lang="bg">&#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090; — PDF</comment>

<snip>

<acronym>PDF</acronym>
<expanded-acronym>Portable Document Format</expanded-acronym>
<alias type="application/x-pdf"/>
<alias type="image/pdf"/>
</mime-type>
```

A couple of ideas are that the .local/share files on the G4 have the wrong or missing files or,
the reference in /usr/share/mime/application/pdf.xml to:
```
<alias type="application/x-pdf"/>
```
is wrong. I read something similar on this post:
[http://markmail.org/message/vlvrn3uf5mnlncvv](http://markmail.org/message/vlvrn3uf5mnlncvv)
I guess I'm thinking that there is a configuration or link problem but have no idea how to resolve it. I tried copying my .local/share file from the G3 to the G4 and that doesn't work nor does copying any of the other files.
I also tried moving the .local/share and seeing if evince would generate another but it won't run at all.

Bottom line is that if 2 completely updated Hardy installs on 2 ppc boxes can't both run evince, I don't think this is a bug.

---

### Post by altonbr on 2009-08-17
> **ubuntubrian said:**
> I have been working on this for hours and haven't gotten anywhere. I have Hardy installed on my G3Powerbook and evince works fine. On my G4 TiBook it won't open pdf's but it does open ps docs. I checked my .local/share/mime directory on the G4 and there is nothing in there that refers to either ps or pdf. The G3 has a mimeapps.list in .local/share/applications file with:


Whereas the G4 only has:


There are mime files in /etc/mime.types that refer to:


among many others.

Also have:
/usr/share/mime/application/pdf.xml and 
/usr/share/mime/application/postscript.xml

The /usr/share/mime/application/pdf.xml has:
```
<mime-type type="application/pdf">
&#8722;
<!--
Created automatically by update-mime-database. DO NOT EDIT!
-->
<comment>PDF document</comment>
<comment xml:lang="bg">&#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090; — PDF</comment>

<snip>

<acronym>PDF</acronym>
<expanded-acronym>Portable Document Format</expanded-acronym>
<alias type="application/x-pdf"/>
<alias type="image/pdf"/>
</mime-type>
```A couple of ideas are that the .local/share files on the G4 have the wrong or missing files or,
the reference in /usr/share/mime/application/pdf.xml to:
```
<alias type="application/x-pdf"/>
```is wrong. I read something similar on this post:
[http://markmail.org/message/vlvrn3uf5mnlncvv](http://markmail.org/message/vlvrn3uf5mnlncvv)
I guess I'm thinking that there is a configuration or link problem but have no idea how to resolve it. I tried copying my .local/share file from the G3 to the G4 and that doesn't work nor does copying any of the other files.
I also tried moving the .local/share and seeing if evince would generate another but it won't run at all.

Bottom line is that if 2 completely updated Hardy installs on 2 ppc boxes can't both run evince, I don't think this is a bug.

You seem to be on to something here because I'm having problems opening an application/pdf file (which contains PHP code) and will only work when acroread is installed.

I made a separate thread for it here: [http://ubuntuforums.org/showthread.php?p=7800763](http://ubuntuforums.org/showthread.php?p=7800763)

---

