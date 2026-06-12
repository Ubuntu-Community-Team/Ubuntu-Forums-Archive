---
title: "not for me"
date: 2008-08-09
forum: General Help
---

### Post by jorj82 on 2008-08-09
Well, I finally got it up and running.  I downloaded Linux ports of the only two programs I ever use (epsxe and zsnes), but I can't get them to work.  I can't even reformat my drive to go back to Windows, I'm completely stuck.  Help?

---

### Post by Vivaldi Gloria on 2008-08-09
> **jorj82 said:**
> Well, I finally got it up and running.  I downloaded Linux ports of the only two programs I ever use (epsxe and zsnes), but I can't get them to work.  I can't even reformat my drive to go back to Windows, I'm completely stuck.  Help?

For installing programs use

system menu > admin > synaptic

Also enable restricted and multiverse repositories from the repository settings to get a more complete list. Then click refresh.

Now you can search and install whatever you want in synaptic. zsnes is available in synaptic.

It seems that epsxe is not available from synaptic. But I downloaded and unzipped it. When I double-click epsxe it works.

---

### Post by kahlil88 on 2008-08-09
Define "downloaded" and "can't get them to work" - did you download the source code or install them from .DEB packages (or Synaptic)?

---

### Post by jorj82 on 2008-08-09
I use someone else's pc for downloading, mine has no connection.  I unzipped espxe and it won't work for me.  Arrg I'm new to this, its kinda frustrating/confusing.

---

### Post by zxscooby on 2008-08-09
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

everything takes some getting used too

---

### Post by jorj82 on 2008-08-09
> **kahlil88 said:**
> Define "downloaded" and "can't get them to work" - did you download the source code or install them from .DEB packages (or Synaptic)?

download: zip files from zophar's domain
can't get them to work: doubleclick does nothing, right click-open does nothing

---

### Post by Vivaldi Gloria on 2008-08-09
> **jorj82 said:**
> I use someone else's pc for downloading, mine has no connection.  I unzipped espxe and it won't work for me.  Arrg I'm new to this, its kinda frustrating/confusing.

Try starting espxe from a terminal to see if you get an error. Probably you don't have a dependency of it so it doesn't work.

I suggest you connect your computer once to the internet to install all the programs you need using synaptic (including zsnes). Synaptic is good because it automatically installs all dependencies as well. 

You can try downloading the .deb file of zsnes and the .deb files of all its dependencies from

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

A deb file is equivalent of an exe in windows. You double click to install it.

---

