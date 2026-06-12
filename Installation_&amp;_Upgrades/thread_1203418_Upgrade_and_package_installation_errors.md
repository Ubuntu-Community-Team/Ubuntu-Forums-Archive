---
title: "Upgrade and package installation errors"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by Musmanno on 2009-07-03
I've noticed with Ubuntu I am getting a lot of corrupt packages.  I often have to go in an manually delete and try to install them two or three times.  I didn't have the trouble with OpenSUSE running on this same computer.

Most recently, when updating:

E: /var/cache/apt/archives/linux-image-2.6.28-13-generic_2.6.28-13.45_amd64.deb: short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.28-13-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko')
E: /var/cache/apt/archives/linux-headers-2.6.28-13_2.6.28-13.45_all.deb: corrupted filesystem tarfile - corrupted package archive

I ran fsck and everything came back good.  I have other OS running on the same drive and everything is good.

No matter how many times I go delete the downloaded packages and re-download, I get the same error.

Any thoughts?  Please keep in mind I am relatively new to linux, so don't assume a lot of expertise when you answer :)

---

### Post by Musmanno on 2009-07-03
Anyone? Anyone?

Bueller...?

---

### Post by Musmanno on 2009-07-04
I tried sudo apt-get install -f based on a recommendation on a site.  This is my response:

(Reading database ... 126171 files and directories currently installed.)
Unpacking libqtcore4 (from .../libqtcore4_4.5.0-0ubuntu4.1_amd64.deb) ...
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/libqtcore4_4.5.0-0ubuntu4.1_amd64.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/qt4/translations/qt_ar.qm')
Unpacking libqtgui4 (from .../libqtgui4_4.5.0-0ubuntu4.1_amd64.deb) ...
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/libqtgui4_4.5.0-0ubuntu4.1_amd64.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/libQtGui.so.4.5.0')
Unpacking libqt4-designer (from .../libqt4-designer_4.5.0-0ubuntu4.1_amd64.deb) ...
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/libqt4-designer_4.5.0-0ubuntu4.1_amd64.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
Unpacking libqt4-qt3support (from .../libqt4-qt3support_4.5.0-0ubuntu4.1_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libqtcore4_4.5.0-0ubuntu4.1_amd64.deb
 /var/cache/apt/archives/libqtgui4_4.5.0-0ubuntu4.1_amd64.deb
 /var/cache/apt/archives/libqt4-designer_4.5.0-0ubuntu4.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
rskimsey@rskimsey-linux:~$ 


It doesn't look like anyone here know about this, but if anyone can recommend another forum where I could post this question, please let me know. 

Thanks!

---

### Post by FrogPrince on 2009-07-04
Try[ Linux Forums]("http://www.linuxforums.org/forum/"). I hang around there from time to time. There are some very knowledgeable people there.

---

### Post by jherskow on 2009-08-25
i dont understand what u guys have been saying, but i have a problem that allot of stuff i try to install hae dependencies, and when i try to install them, they have dependencies, and nothing works.'
im pretty sure the qt4 thing is one of he dependencies
if that fits the problem here, can you please help me?

---

