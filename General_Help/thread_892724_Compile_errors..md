---
title: "Compile errors."
date: 2008-08-17
forum: General Help
---

### Post by Demios101 on 2008-08-17
I've been trying to compile a plugin for gmpc, but i keep getting errors after ./configure I've taken care of as many as I can the last one i got told me i didnt have pkg-config, so i installed it via synaptic now i get this [http://pastebin.com/m4f17f6d9](http://pastebin.com/m4f17f6d9)

pretty sure i have pkg-config installed. It's listed in my synaptic.

---

### Post by Naatan on 2008-08-17
You need to have the development packages installed for the required libraries (packages with -dev at the end). This is what the ./configure command needs.

---

### Post by Demios101 on 2008-08-17
I was told I needed

>    * gcc compiler
   * libtool
   * intltool Version 0.21 or higher
   * glib
   * libcurl
   * gobject
   * gtk+-2.0
   * gmodule
   * libglade
   * gthreads
   * libmpd
   * gob 2.0


Somethings do not show up in synaptic when I search for them, and I can't seem to be able to find the dev versions of some of them.

---

### Post by mali2297 on 2008-08-17
Have you installed **build-essential**?

---

### Post by Demios101 on 2008-08-17
I didn't I just did though, I am now getting, [http://pastebin.com/mb1b241b](http://pastebin.com/mb1b241b)


> Requested 'libmpd >= 0.15.98' but version of libmpd is 0.14.0
No package 'gmpc' found
configure:19964: error: Package requirements (	glib-2.0 >= 2.10
	gobject-2.0 >= 2.4
	gtk+-2.0 >= 2.8
	gmodule-2.0
	libxml-2.0
	gthread-2.0
	libmpd >= 0.15.98
	gmpc	>= 0.15.98
) were not met:

Requested 'libmpd >= 0.15.98' but version of libmpd is 0.14.0
No package 'gmpc' found

---

### Post by mali2297 on 2008-08-17
> **Demios101 said:**
> I didn't I just did though, I am now getting, [http://pastebin.com/mb1b241b](http://pastebin.com/mb1b241b)

Well, it seems like you need to compile the latest libmpd and gmpc as well.
The source can be found here:
[http://download.sarine.nl/Programs/gmpc/0.16.0-beta1/](http://download.sarine.nl/Programs/gmpc/0.16.0-beta1/)

Perhaps you should ask yourself if it is worth the trouble.

---

### Post by Demios101 on 2008-08-17
That was the problem, i removed the synaptic installed libmpd and compiled a new one... yes, it is so very worth it right now. Thanks for all your help guys.

---

