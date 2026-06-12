---
title: "[SOLVED] Evince opens ps but not pdf"
date: 2008-08-06
forum: General Help
---

### Post by ubuntubrian on 2008-08-06
I hope starting a new thread on this isn't amajorbadbut Ithink the one I replied on isn't active, so here goes.

I have been working on this for hours and haven't gotten anywhere. I have Hardy installed on my G3Powerbook and evince works fine. On my G4 TiBook it won't open pdf's but it does open ps docs. (xpdf and kpdf open them fine except that gpdf layers the pages so that they are illegible.) 
After reading other posts and other lists I think that this is a mime problem but am not sure.
I checked my .local/share/mime directory on the G4 and there is nothing in there that refers to either ps or pdf. The G3 has a mimeapps.list in .local/share/applications file with:
Quote:
[Added Associations]
application/pdf=userapp-evince-O6PU8T.desktop;
application/x-shockwave-flash=userapp-gnash-HWEXEU.desktop;
application/vnd.rn-realmedia=totem-gstreamer.desktop;mplayer.desktop;
Whereas the G4 only has:
Quote:
[Added Associations]
application/octet-stream=userapp-gedit-VZ2AFU.desktop;
There are mime files in /etc/mime.types that refer to:
Quote:
application/pdf pdf
application/pgp-encrypted
application/pgp-keys key
application/pgp-signature pgp
application/pics-rules prf
application/pkcs10
application/pkcs7-mime
application/pkcs7-signature
application/pkix-cert
application/pkix-crl
application/pkixcmp
application/postscript ps ai eps
among many others.

Also have:
/usr/share/mime/application/pdf.xml and
/usr/share/mime/application/postscript.xml

The /usr/share/mime/application/pdf.xml has:
Code:

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

A couple of ideas are that the .local/share files on the G4 have the wrong or missing files or,
the reference in /usr/share/mime/application/pdf.xml to:
Code:

<alias type="application/x-pdf"/>

is wrong. I read something similar on this post:
[http://markmail.org/message/vlvrn3uf5mnlncvv](http://markmail.org/message/vlvrn3uf5mnlncvv)
I guess I'm thinking that there is a configuration or link problem but have no idea how to resolve it. I tried copying my .local/share file from the G3 to the G4 and that doesn't work nor does copying any of the other files.
I also tried moving the .local/share and seeing if evince would generate another but it won't run at all.

Bottom line is that if 2 completely updated Hardy installs on 2 ppc boxes can't both run evince, I don't think this is a bug.

---

### Post by ubuntubrian on 2008-08-11
I finally got evince to open pdf's! It only took 20 or 30 hours too.
I uninstalled evince and poppler stuff with synaptic and reinstalled
many times to no avail. I read the lists and saw that there were issues
with poppler, evince and pdf's in the newest versions.
I downloaded source packages for each, in multiple versions, and built
them. Poppler built, evince did not in any version.
I installed epdf (doesn't have print abilities though!) with synaptic
which uninstalled poppler-data-missed that at first. I cleaned up all
the evince and poppler stuff again with:
make-distclean
in the appropriate directories.
I reinstalled poppler-0.8.5 with make and then the latest evince with
synaptic. Now evince works.
I had also previously moved my mime.cache file in ~/.local/share/mime
but it hadn't made a difference. After restarting and now with evince
working the file did not regenerate-interesting.

---

