---
title: "How to reinstall Adobe Reader 9.0 without causing more problems?"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by ubantuwannabe on 2009-04-21
Hi all,

I follow [http://ubuntu-tutorials.com/2008/11/15/install-adobe-reader-813-on-ubuntu-810-intrepid-ibex/](http://ubuntu-tutorials.com/2008/11/15/install-adobe-reader-813-on-ubuntu-810-intrepid-ibex/) and install Adobe Reader. I install the debian package as what is being written.

It all works fine initially. Until I encounter the following error when I try to download a pdf from dba-village

"could not launch adobe reader 9.0. please make sure it exists in path variable in the environment. if the problem persists please reinstall the application."

so I try to resolve this issue. I get to know this url [http://ubuntuforums.org/archive/index.php/t-830178.html](http://ubuntuforums.org/archive/index.php/t-830178.html)

so I install sudo apt-get install mozplugger

to get rid of this issue(could not launch ....)

more problems ensue.

next I encounter 

"fail to execute child processes acroread."

so I'm forced to do the following

sudo apt-get remove mozplugger.

problem not resolved.

so I'm forced to remove Adobe Reader 9(debian)

Here's how I remove it.

System->Administration->Synaptic Package Manager.
I search for Adobe Reader 9.0 (debian)

Right now If I were to follow [http://ubuntu-tutorials.com/2008/11/15/install-adobe-reader-813-on-ubuntu-810-intrepid-ibex/](http://ubuntu-tutorials.com/2008/11/15/install-adobe-reader-813-on-ubuntu-810-intrepid-ibex/)

and reinstall again, I would encounter the following error when I double clicked the downloaded file. (debian package)

"/tmp/AdbeRdr9.1.0-1_386linux_enu.deb could not be saved. because you cannot change the contents of that folder.

change the folder properties and try again, or try saving in a different directory."

so could any one help me on this? thanks a lot!

---

### Post by lemming465 on 2009-04-23
I get my acrobat reader (and other stuff) from the 3rd party quasi-official [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories.  Just follow the directions.

---

### Post by tcfan on 2009-04-23
I downloaded it from here: [http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/)

Select Linux - x86 (.deb) and then run the installer.  Worked flawlessly for me.

---

