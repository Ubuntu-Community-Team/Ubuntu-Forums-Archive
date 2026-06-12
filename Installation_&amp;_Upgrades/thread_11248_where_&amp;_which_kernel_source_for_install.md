---
title: "where &amp; which kernel source for install"
date: 2005-01-15
forum: Installation &amp; Upgrades
---

### Post by fsman on 2005-01-15
I've got the install CD but my adsl modem is internal (Conexant), so I need to download the kernel source from windows to use with my new install.

Question is. Where and what files do I need to download in advance in order compile the driver in conjunction with the install CD.

Plus I need pppoatm - is this installed by default or do i need to download the .deb as well?

---

### Post by word_virus on 2005-01-15
[QUOTE=fsman]I've got the install CD but my adsl modem is internal (Conexant), so I need to download the kernel source from windows to use with my new install.

Question is. Where and what files do I need to download in advance in order compile the driver in conjunction with the install CD.

Plus I need pppoatm - is this installed by default or do i need to download the .deb as well?[/QUOTE]

Kernel source can be installed with:
apt-get install linux-source-2.6.8.1

but from what I understand this is generally not recommended.  Instead just install the kernel header files with (I think.  Might use Synaptic for this one just to be safe):
apt-get install linux-headers

Also, I think Linuxant ([http://www.linuxant.com](http://www.linuxant.com)) provides binary drivers for the Conexant chipset that don't need to be compiled (just download the .DEB package from the website), but I don't have one of these so I'm not 100% sure.

Not at my box so I don't know if pppoatm is installed by default, but, again, it's easy to check for in Synaptic, just do a search.

---

### Post by fsman on 2005-01-15
I need to download the .deb files in advance apt-get/synaptic won't work as I can't connect to the internet until I've compiled the conexant pci adsl driver and got pppoatm working.

which kernal source/header files are compatable with the install CD? 
many thanks.

---

