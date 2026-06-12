---
title: "Openoffice 2.4 in Hardy unable to play movies"
date: 2008-08-27
forum: General Help
---

### Post by Fardilha on 2008-08-27
Hello All.

I'm trying to insert a movie on Openoffice under Ubuntu 8.04 (Hardy Heron) without any luck.

My sequence was:
° Fresh install of Ubuntu 8.04 fully updated.
° Medibunt rep added to allow the installation of Sun's Java jre thru the "Ubuntu restricted extras".
° OpenOffice couldn't see the JRE so I had to go to Synaptic and install openoffice.org-java-common.
° Now OOo allowed me to select my jre under Tools -> Options -> java

After restart OpenOffice I tried to insert both a MPEG-1 and a MPEG-4 in a Impress presentation, but all I've got was a non functonal grey icon with a sound symbol.

° I installed the JMF .jar files on the proper jre folder and add them on OpenOffice to the java classpath.

Again no luck.

I really just don't know what else I should do.
Can anyone, please, give me a help here before my wife kills me for not using the "regular" office :) ?

Thank you!
Pedro Fardilha

---

### Post by Briga on 2008-11-11
AFAIK if you install OO from the Ubuntu repositories (an Ubuntu patched version) multimedia is rendered through the gstreamer layer and not JMF (which is very tricky to install). 

But if you want to go for JMF look for HowTos there are many tips (including moving .so and .jar).

---

