---
title: "Compile apps and install like synaptic"
date: 2008-08-28
forum: General Help
---

### Post by bardic on 2008-08-28
Hey all,
I have a question for ya's that I can't figure out. When I compile apps, I can't get them to act like the apps like I install from synaptic. They aren't in a 'default' spot since I compile them in my home folder. 

Just wondering how would I go about finding out where these apps 'properly' belong? Is there a guide or something? Thanks

---

### Post by Nythain on 2008-08-28
are you asking where they are installed to, or should be installed to, or are you just wanting them to show up in synaptic/apt like other packages.

A. when you ./configure most stuff, you can change where it gets installed with a flag usually like --prefix=PREFIX, by default most compiled apps like to install to /usr/local, but you could have them install anywhere, ahhh, the powers of comiling. if you are confused, cd into the untarred directory of the source you downloaded and run ./configure --help

B. if you wanted them to be treated like regular packages, you could consider making a deb out of the source, then installing with dpkg, that way it will show up in synaptic and also make things incredibly easier to remove later. cant help ya much here, but you could google something like "ubuntu make deb from srouce" and probably get some pretty good instructions

and a last note, where an app "properly" belongs, is anywhere on your system you want it... but usually anywhere within your $PATH if you want to be able to run said app from anywhere in a terminal or with a desktop icon or menu entry.

---

### Post by whitethorn on 2008-08-28
Hi there's a program called checkinstall which will make a .deb out of source for you.  Here's a howto I found which explains how to get it. It's a little old (written for warty) but it should still work for hardy.  So when it says enable universe/ multiverse, you can do that in synaptic you don't have to edit sources.list. You still have to compile and make the package. Pretty much all checkinstall does is replace the last step of the installing process.  Instead of 

sudo make install   you use

sudo checkinstall

then you'll see the program in synaptic and you can deal with it like any other app.



[http://ubuntuforums.org/showthread.php?t=2356](http://ubuntuforums.org/showthread.php?t=2356)

---

