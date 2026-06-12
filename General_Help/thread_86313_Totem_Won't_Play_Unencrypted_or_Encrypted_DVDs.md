---
title: "Totem Won't Play Unencrypted or Encrypted DVDs"
date: 2005-11-04
forum: General Help
---

### Post by semilemon on 2005-11-04
Hello. I've just come from a fresh installation of Breezy. Everything works perfect, except for Totem Movie Player.

When I insert a DVD, Totem pops up and says it is playing the DVD, however nothing is happening, and it is an unencrypted DVD. When I try selecting options from the "Go" menu, such as "DVD Menu", the problem continues with no error. Also, the DVD drive is not active. Any ideas?

Also, I'm trying to get libdvdcss 1.2.9 to install, because I thought maybe it would help. When I run ./configure, here is what I get:

> checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Any and all help is greatly appreciated!

---

### Post by trigg on 2005-11-04
Which version of Totem do you have installed?  Totem-gstreamer or Totem-xine?  There are problems with Totem-gstreamer, so it would be a good idea to switch versions.  Secondnly, if you interested in playing restricted formats - here is a great article on how to do it: 

[Restricted Formats Wiki Entry]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs")

*edited for typos

---

### Post by eyebrowman92 on 2005-11-04
try installing libdvdcss2 on synaptic. just search it and install it. and i agree the with the comment above.

---

### Post by nightfly on 2005-11-05
libdvdcss2 is no longer available from Synaptic.

To install libdvdcss2, install libdvdread first (installed by default) and then run
# sudo /usr/share/doc/libdvdread3/examples/install-css.sh

---

### Post by el toro on 2005-11-05
You can fix the error about the compiler by installing the build-essential package from Synaptic.

---

### Post by speckman on 2005-11-06
I installed everything mentioned above.  My totem-xine will now play the first logo screen of the DVD, but 14 seconds later, it'll have the "no libdvdcss" error window.
I had this working before I installed breezy.  I had a lot of things working... :)

---

### Post by trigg on 2005-11-09
[QUOTE=speckman]I installed everything mentioned above.  My totem-xine will now play the first logo screen of the DVD, but 14 seconds later, it'll have the "no libdvdcss" error window.
I had this working before I installed breezy.  I had a lot of things working... :)[/QUOTE]

The only time I have seen this since I upgraded  was when the DVD was scratched.  Took me a while to figure out why the hell it kept saying I didn't have libdvdcss - maybe it is just less fault tolerant than some licensed players (i.e. interprets defects in disc as mangled CSS)

---

