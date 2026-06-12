---
title: "Trying to repair Gnome Commander after &quot;make install&quot; failure"
date: 2008-08-12
forum: General Help
---

### Post by quadra on 2008-08-12
Hi there

I tried to build gnome-commander-1.2.7 from source on my ubuntu 8.04.
The first step (./configure) worked fine, it said it's ready to "make".
However, "make" and installing failed. 
WORSE: Now, my previous version of gcmd (official 1.2.5 from Ubuntu repositories) does no longer run, even after a complete removal and reinstall (using synaptic package manager). Help!

Make error:
make[2]: Entering directory `/home/myself/pending/gcmd127/po'
file=`echo ar | sed 's,.*/,,'`.gmo \
	  && rm -f $file &&  -o $file ar.po
/bin/sh: -o: not found
make[2]: *** [ar.gmo] Error 127
make[2]: Leaving directory `/home/myself/pending/gcmd127/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/myself/pending/gcmd127'
make: *** [all] Error 2

Error in system log when trying to relaunch the official gcmd (after complete removal & clean reinstall from Ubuntu repositories)
Aug 11 21:46:03 mbudell kernel: [ 2554.978124] gnome-commander[21899]: segfault at 0000000c eip 080968ea esp bfefe980 error 6

What should I try first to get any version of Gnome Commander running? Thanks for your help!

---

### Post by quadra on 2008-08-13
Hi
Still no solution found.
In the meantime, I had to abandon Gnome Commander. I discovered emelFM2, wich is amazingly fast and flexible.
But I hope somebody may help me to get my Gnome Commander back working...

---

### Post by fetzki on 2008-08-21
I think you are missing the package libgettext-ruby-util.
If you take a look at the po/Makefile you should see the variable MSGFMT undefined.

To compile gnome-commander 1.27 with all plugins and stuff, you can do an
apt-get install libglib2.0-dev libgtk2.0-dev libgnome2-dev libgnomeui-dev libgnomevfs2-dev libexiv2-dev libtag1-dev libgsf-1-dev python2.5-dev g++ libgettext-ruby-util

then repeat the configure / make / make install process.

Works for me on a fresh Ubuntu 8.04 install.

Hope this helps 

fetzki

---

### Post by iloutzu on 2008-11-02
Thanks, fetzki!

---

