---
title: "[SOLVED] Install conky from source: Can't locate your X11 installation"
date: 2008-09-26
forum: General Help
---

### Post by Asham on 2008-09-26
Hi

I am trying to install conky from source in order how to get a grip on how this manual installation procedure is done. I already found out I had to install the build-essentials and the pkg-config packages. Done and done, but the next problem that comes up during ./configure is this message that I do not understand:

> checking for X... no
configure: error: Can't locate your X11 installation

How do I get past this? Google didn't find any useful pages or I used the wrong terms.

TIA,
Adam

---

### Post by nikgare on 2008-09-26
You probably need to install the X11 dev files, probably this:
libx11-dev

---

### Post by Asham on 2008-09-27
Thanks for the help. It helped, I got past the missing x11-thing but got a few other dependency problems. However I go past them too! :D

The output messages "missing xyz" is quite helpful if you know how to interpret them. Most of the times it seems you can prepend "lib" and append "-dev" to the package name and find it through apt-cache search. When not, Google can sometimes find help but when that's not the case - this forum is great! :cool:

---

### Post by SaffronB77 on 2009-03-27
Sorry to resurrect a long dead post. 

I have run into the same problem as the OP. I first had to grab build essentials (no problem), then I hit the X11 error. I installed the X11 package through add programs but I still get the message that it's missing. I'm running some much needed updates right now but scanning through the list I did not see any reference to x11 or libx11-dev. 

Could it be I need to add another repository to find it? 

Any help is greatly appreciated.

---

### Post by cailamaia on 2009-05-07
@SaffronB77:

To find the files you want, you simply have to open the synaptic package manager and type libx11-dev into the search (or a portion of the filename works too), then select libx11-dev for installation and agree to all of the other dependencies it warns you about.

And then you're done. That's all there is to it.

---

