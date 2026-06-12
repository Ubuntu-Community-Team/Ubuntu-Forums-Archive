---
title: "cant upgrade from repositories"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by Shpongle on 2009-02-26
when i try i keep gettin a failed hash sum check
 
the progress bar keeps jumping back,

i havn't done anything that i can think of that would have caused this,

any ideas any one?


heres the output after it fails



Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.22.87-2intrepid1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.22.87-2intrepid1_i386.deb) Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.6.3-1ubuntu1~intrepid1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.6.3-1ubuntu1~intrepid1_i386.deb) Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.3-1ubuntu1~intrepid1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.3-1ubuntu1~intrepid1_i386.deb) Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.3-1ubuntu1~intrepid1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.3-1ubuntu1~intrepid1_all.deb) Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kde-icons-oxygen_4.2.0-0ubuntu1~intrepid2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kde-icons-oxygen_4.2.0-0ubuntu1~intrepid2_all.deb) Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime-data_4.2.0-0ubuntu1~intrepid2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kdebase-runtime/kdebase-runtime-data_4.2.0-0ubuntu1~intrepid2_all.deb) Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5-data_4.2.0-0ubuntu2~intrepid2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5-data_4.2.0-0ubuntu2~intrepid2_all.deb) Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/v/vlc/vlc-nox_0.9.4-1ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/v/vlc/vlc-nox_0.9.4-1ubuntu3.1_i386.deb) Hash Sum mismatch

---

### Post by CiaoCiao on 2009-02-26
I'm no expert so here is the results of a quick google to help get you started...

From this link [here]("http://www.neowin.net/forum/index.php?showtopic=596516&pid=588946108&st=0&#entry588946108")

"disable the cdrom as a repository in synaptic. "

It worked for someone else 2 years ago... :)

---

### Post by cariboo on 2009-02-26
I would suggest trying a different server. Go to System-->Administration-->Software Sources, click the download from dropdown and select Other, then click the Select Best Server Button, once it has finished clcik the Choose Server button. Reload the repositories and try to upgrade.

Jim

---

### Post by Shpongle on 2009-02-27
thanks for that it was the server , it must have been down or something, any way the best server option worked,


another example of how helpful the ubuntu community is:mrgreen:

thanks again

---

