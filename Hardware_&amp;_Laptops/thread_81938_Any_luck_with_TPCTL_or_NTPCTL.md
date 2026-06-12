---
title: "Any luck with TPCTL or NTPCTL?"
date: 2005-10-25
forum: Hardware &amp; Laptops
---

### Post by NMUrugbysteve on 2005-10-25
Has anyone had any luck running tpctl on breezy on any type of thinkpad? I can't get the dev/thinkpad to be created.

---

### Post by emendelson on 2005-10-25
TPCTL never seems to run under Ubuntu. What tasks are you trying to perform? There are other ways of accomplishing most of what it does.

---

### Post by rawler on 2005-11-17
For me, I'd like to try to have tpctl activate the TV-out-port on my laptop. Running on a T42, I haven't managed to get TV-out working at all. :(

---

### Post by Jarrod-AU on 2007-08-30
Just in case anyone comes looking for information on configure-thinkpad or tpctl on Feisty, here are some things I've found...
This URL has some details to get the /dev/thinkpad device up and running:
[http://www.linuxjournal.com/comment/reply/8462](http://www.linuxjournal.com/comment/reply/8462)

 you'll need to install the thinkpad-source package. 

This puts the tarball in /usr/src/, you'll then need to untar it there.
sudo tar xzvf thinkpad.tar.gz
You'll also need the linux kernel source e.g. linux-source package.

The thinkpad module can apparently be built just by using 'make; make install' in the /usr/src/modules/thinkpad/2.6/drivers/ directory, but there are two problems with that, at least with the packages I downloaded in Feisty.
1. Build fails complaining of ')' characters in thinkpad.c. This was reported in the Debian upstream package:
[http://lists.alioth.debian.org/pipermail/pkg-tpctl-devel/2006-October/000102.html](http://lists.alioth.debian.org/pipermail/pkg-tpctl-devel/2006-October/000102.html)
The poster in that thread Franklin Piat, kindly provided a patch which can workaround this problem.
2. The build then fails with a Makefile error "No rule to build target". This time Eric Cooper has the workaround - rename smapi_call.s to smapi_call.S
[http://lists.alioth.debian.org/pipermail/pkg-tpctl-devel/2006-December/000114.html](http://lists.alioth.debian.org/pipermail/pkg-tpctl-devel/2006-December/000114.html)

Once that's done the module should build and install properly.
Then you can modprobe thinkpad and... uhoh. Error. dmesg shows:
[11329.740000] thinkpad: Unknown symbol inter_module_get_request
[11329.740000] thinkpad: Unknown symbol inter_module_put

I think I read something about this, needs a special kernel compile option... I'll add it later when I can find it.

---

### Post by Jarrod-AU on 2007-08-30
OK, I found it in /usr/share/doc/thinkpad-source/README-Debian.gz
"Kernels 2.6.16 and up must be built with CONFIG_OBSOLETE_INTERMODULE=y. "
I think this is what needs to be done.

---

### Post by moore.bryan on 2007-08-30
[I]alright, this is really pissing me off.  why the hell would anyone make it so difficult to get this frickin' module loading?  i'm not usually critical of the "powers that be" when it comes to this kind of stuff, but come on, this is RIDICULOUS.  no matter what i do, i can't get this to work.  my "make" brings up errors, none of which are discussed anywhere else in the known universe (according to google).

is there any simple, easy way to do this or should i just give-up on getting configure-thinkpad to work?
[/I]

---

