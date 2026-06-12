---
title: "Install Packages without Network Using Aptoncd"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by RwandaTim on 2009-05-22
I am trying to install packages in Ubuntu Jaunty using Aptoncd on a computer without a network connection.  I have identified the packages I want on the computer _with_ network connection, selected them (along with dependencies) in Aptoncd.  After burning disk, I open Synaptic on the second computer (without network) and Add CD-ROM.  But, when I try to add those packages, Synaptic lists different dependencies, next to each saying "...but is not going to be installed."  I've tried going back to Aptoncd and selecting _every_ package on my computer with network connection, assuming that any possible dependency would be represented.  But, the problem persists.  Any advice?

---

### Post by RwandaTim on 2009-05-25
I'm replying to my own thread because I've found a very workable solution...  KERYX.  The steps are laid out very simply on the website ([www.keryxproject.org](www.keryxproject.org)).  Basically, you can use this little program to get a snapshot of your computer without network connection so that it will know what to look for when connected to the computer with a network connection.  I am using a USB memory stick.  You don't even have to have Ubuntu loaded on the other networked computer (i.e. it will download packages for Ubuntu using another OS).  

For me, this is the easiest thing I've found - very direct and helpful, considering I oversee thirty unnetworked computers in Central Africa.

---

