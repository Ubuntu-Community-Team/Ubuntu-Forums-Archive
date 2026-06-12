---
title: "Installing latest sane-backends"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by ChrisTheGeek on 2005-10-14
Hi,

Does anybody know how I can install the latest sane backends on breezy? According to their website my scanner is only supported in cvs at the moment.

I tried a .deb file from their website but it had conflicts with some libs in ubuntu.

I could try and install from source but I'm a little unsure how to do this - in particular, if I installed from source, could I still use synaptic to install xsane or would I have to try and make that from source as well because of dependencies?

This is the only show stopper for dumping Windows at the moment, so any help is really appreciated!

---

### Post by darknuala on 2005-10-14
If you find the answer to this, I would like to know as well.  My scanner is only supported in cvs backends as well.  I don't know how to use that information to get it to work in ubuntu with SANE

---

### Post by Pablo_Escobar on 2005-10-14
Try to install the cvs version.

1. "sudo apt-get checkinstall"
2. get sane source
3. try to "./configure" it (You'll probably have lots of dependecy errors, but just install the dev packages through synaptic that ./configure spits out)
4. if "./configure" completes -> "make"
5. then instead of "sudo make install" type "sudo checkinstall" - it'll make install the file but it'll make also a deb package and install it, then You can delete it from synaptic anytime You want it.

Hope this will help.

---

### Post by ChrisTheGeek on 2005-10-14
Thanks for the replies.  I've been reading more about SANE than I care to know and think I am slowly beginning to understand.

After much googling, I think that it may be possible to keep the versions of sane backends and xsane in the breezy repositories and just upgrade the particular backend driver I need (in my case the plustec backend for the Canon LiDE 25).

I'm still a bit confused about if/how to mix and match repositories and self-compiled stuff.  It would be nice to be able to say "Install this package but don't worry about *that* dependency cos I already have my own version".

Another possability seems to be ignoring the packages altogether and compiling the backend and xsane yourself so they are all out of package management control.  I have tried to do this but unfortunately xsane seg faulted at me and I have no idea how to begin fixing that!

I did manage to get the backend installed though and I got a picture out of the scanner using the command line tool 'scanimage'

Will post back when I've tried out your suggestion :) Thanks again.

---

### Post by ChrisTheGeek on 2005-12-01
Well I got it working! I've posted instructions here:

[http://www.ubuntuforums.org/showthread.php?t=72498&page=2](http://www.ubuntuforums.org/showthread.php?t=72498&page=2)

Basically You need to make sure the package libusb-dev is installed first, then:

./configure --prefix=/usr --sysconfdir=/etc
make
sudo make install

For my scanner (canoscan Lide 25) I then had to mess with the hotplug files to get the permissions to be set right.

---

