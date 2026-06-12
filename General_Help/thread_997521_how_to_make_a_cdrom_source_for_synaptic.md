---
title: "how to make a cdrom source for synaptic?"
date: 2008-11-29
forum: General Help
---

### Post by ramaswamyps on 2008-11-29
i have got package files .deb ubuntu
i have installed (upgraded to 8.10 from 8.04
i have saved kde-3.5 files in a folder.
how can i install kde-3.5.10 from this source/folder?
i have lot of difficulty in usyng kde4 with my slow laptop.
need help and instructions.
thanks in advance

---

### Post by drs305 on 2008-11-29
To add a CDROM source to the sources.list/synaptic:
Open synaptic or Software Sources, repositories, third party software, Add CDROM.

---

### Post by ramaswamyps on 2008-11-29
it is not recognising the cd as debian source.
only the copy of apt/archives/* is there with me.
it needs to be in a certain format.
like debian cdrom

---

### Post by drs305 on 2008-11-29
You can't just put deb files on a cd and make it a repository. The appropriate file structure must be built and include .gz files.

If you do a search for: *.gz deb cdrom create source  * and variations
you can probably find a good guide on how to build it.

Section 2.2 of the following link provides an example, but there are undoubtedly better ones out there:
[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html]("http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html")

---

