---
title: "Problem installing language pack French"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by mcb CH on 2009-10-10
Following a re-install of OpenOffice (with 'apt-get), I've run into a problem re-configuring language support. The French language pack does not install (see terminal read-out below). Tried "sudo apt-get -f install" to fix the broken package, but that just runs through the same loop, complaining about unmet dependencies. How do I fix that?

dpkg: error processing /var/cache/apt/archives/language-pack-kde-fr_1%3a9.04+20090921_all.deb (--unpack):                                                 
 trying to overwrite `/usr/share/locale-langpack/fr/LC_MESSAGES/phonon_gstreamer.mo', which is also in package language-pack-fr                           
dpkg-deb: subprocess paste killed by signal (Broken pipe)                                                                                                 
Errors were encountered while processing:                                                                                                                 
 /var/cache/apt/archives/language-pack-kde-fr_1%3a9.04+20090921_all.deb                                                                                   
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks!

---

### Post by Partyboi2 on 2009-10-11
Open a terminal and try and overwrite the file
```
cd /var/cache/apt/archives
sudo dpkg --force-overwrite --install language-pack-kde-fr_1%3a9.04+20090921_all.deb
```
```
sudo apt-get -f install
```

---

### Post by mcb CH on 2009-10-11
Thank you, Partyboi (funny, we write that with two y's!). Having slept on it, the machine consented to remove the offending language-pack-French (which it had refused to do yesterday), so the conflict seems to be resolved.

---

