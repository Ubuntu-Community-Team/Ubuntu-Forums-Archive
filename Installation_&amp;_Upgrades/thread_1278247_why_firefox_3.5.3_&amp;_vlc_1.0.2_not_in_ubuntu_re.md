---
title: "why firefox 3.5.3 &amp; vlc 1.0.2 not in ubuntu repos..."
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by prakreet on 2009-09-29
this is really strange... latest versions of two of the most widely used opensource softwares are not available in ubuntu repos... the latest version of firefox there is 3.0.14 and vlc is 0.9.8. i don't understand.. why are we stuck back with old versions.... is it because of some ubuntu policy....

---

### Post by brallan on 2009-09-29
no, it's because the ubuntu distribution freezes at each release. if you want to install later versions, you can try:

a) add a repository if mozilla or vlc supplies them for ubuntu. from synaptic>settings>repositories>other software
b) enable the backports, from  synaptic>settings>repositories>updates. this will require a big download since many programs are going to get updated.
c) go to the websites and download the DEB files.
d) update from within firefox and vlc, if they allow you to.

let us know how it goes!

---

### Post by thomasboleyn on 2009-09-29
Even with the PPA's, you will still only get the beta 'shiretoko' build. If you use a python script called 'Ubuntuzilla' from here [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Welcome_to_Ubuntuzilla](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Welcome_to_Ubuntuzilla) you can upgrade your exisiting firefox to 3.5.3. Very handy tool!

---

### Post by prakreet on 2009-09-29
t think all this prob are due to the gnome packages depending on gecko rendering engine. gnome could just have packaged their own version of gecko and let firefox use its own latest version. simple solution for all this fuss. 

i see that gnome 2.28 is changing to webkit. i hope then we would be able to update and use the latest firefox like we want...

but what about vlc. no gnome packages depend on that... we can use the ppc repos to update to the latest version. [i have done so]. why wouldn't ubuntu have the latest vlc in their repos...

---

### Post by oldos2er on 2009-09-29
Oops, should've read all the posts.
[]("https://launchpad.net/%7Ec-korn/+archive/vlc")

---

