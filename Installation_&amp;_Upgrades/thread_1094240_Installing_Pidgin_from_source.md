---
title: "Installing Pidgin from source"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by TruthOrDare on 2009-03-12
I would like to install the latest version of Pidgin (2.5.5) which is not available in the repository. The reason I want to do this is because the repository version is 5 months and 3 versions out of date (2.5.2) (even after the update the other day).

Do I need to uninstall the current repository version before I install the new version I got from the Pidgin website? From what I can tell, the answer is no.

I downloaded the source as there was no Ubuntu version. Opened the install readme and it says I need to configure, make, then install. Sounds simple enough and I start following the instructions.

Getting it to actually compile and install though is impossible. I have tried all the commands stated in the install readme (and none of them exist, let alone give errors.

I have downloaded autoconf and tried that but that just spouts errors. I am in the directory with pidgin-2.5.5.tar.bz2 in it.

```
:~/Compile$ autoconf pidgin-2.5.5.tar.bz2
/usr/bin/m4:pidgin-2.5.5.tar.bz2:29757: ERROR: end of file in string
autom4te: /usr/bin/m4 failed with exit status: 1

```

Why can't people just make simple .deb files? :(

---

### Post by TruthOrDare on 2009-03-12
Ok, realised I had not unpacked it, so done that.

Now ./configure works however it comes up with an error:

```
configure: error:

You must have the GTK+ 2.0 development headers installed to compile Pidgin.
If you want to build only Finch then specify --disable-gtkui when running configure.

```

However, I have libglib2.0-dev installed, so I don't know what I am supposed to be missing.

---

### Post by Neo_The_User on 2009-03-12
sudo apt-get build-dep pidgin libglib2.0-dev xorg-dev qt3-dev-tools qt4-dev-tools

then browse through synaptic and select all GTK 2.0 dev tools you can find.

---

### Post by landaut on 2009-03-12
I just added the source files to a folder and double click the icon 'no name' or alt+f2 run pidgin, and that boots up Pidgin no problem. Add it to startup or a create a shortcut for it.  No problems so far.

---

### Post by TruthOrDare on 2009-03-12
It was so simple in the end...

extract pidgin-2.5.5.tar.bz2 using Archive Manager
sudo apt-get build-dep pidgin
./configure
make
sudo make install

Of course, this doesn't take into account the many options you have with configuring. However, if you just want a quick compile/install with all the options enabled, it is good.

Thanks everyone for your help.

---

