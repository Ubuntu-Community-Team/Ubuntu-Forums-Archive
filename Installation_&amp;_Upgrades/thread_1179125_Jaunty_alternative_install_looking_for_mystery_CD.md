---
title: "Jaunty alternative install looking for mystery CD"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by taylorkh on 2009-06-05
I am trying to install from the Alternative CD (to build a LAMP server for testing - yes I know about the Server CD but I want gui tools installed).  Anyhow the install starts, I answer questions, it chugs along for a while then asks me to insert the disk "Ubuntu 9.04 _Jautny Jackalope_ - Release i386 (20090420.1".  The CD I made from the ISO is named simply "Ubuntu 9.04" which apparently does not meet the installers requirements.

Any ideas?

TIA,

Ken

---

### Post by zvacet on 2009-06-05
Did you check [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") and aftrer burning on CD did you check [CD integrity?]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

If you have Ubuntu installed you can install LAMP by going to the **synaptic> package>mark package by task>LAMP**.

---

### Post by taylorkh on 2009-06-05
Thanks zvacet.  I did run the CD integrity check and is said the CD was fine.  The install process begins and in the middle of installing base configuration (I think that is what is said) it came up looking for the mystery CD.  I tried replacing the Alternative CD with the regular CD.  That did not do the trick.

I will try the LAMP install in Synaptic.  I was not aware of that trick.

To make the whole thing messier... It seems that VMWare tools are not available for 9.04 yet so I may end up just upgrading MySQL to 5.2.x on my 8.04LTS LAMP VM as that is how I got started on this path.

Thanks again,

Ken

---

