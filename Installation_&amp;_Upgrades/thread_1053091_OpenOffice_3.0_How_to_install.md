---
title: "OpenOffice 3.0 How to install?"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by ChrisR1982 on 2009-01-28
I was rather annoyed to discover that Kubuntu did not come with the latest OpenOffice3 but figured no big deal as I could simply just update it in the adept installer... however OpenOffice3 has not been added yet so I can't upgrade.. how do I get the latest OpenOffice3 to install on Kubuntu?

I went to the OpenOffice website and downloaded 

**OOo_3.0.1_LinuxIntel_install_en-US_deb.tar.gz**

I then uninstalled my current version of OpenOffice... but how do I install from that file?

---

### Post by icheyne on 2009-01-28
The deb package has been compressed by tar.gz.
If you double click the file, it should let you decompress it to a deb file.
Double click on the deb file, input your password and the installation will start.

---

### Post by ChrisR1982 on 2009-01-28
I have extracted the files and theres over 48 DEB files... do I have to double click on all of them!?!


Also inside that file is a whole bunch of **ooobasis3.0** files as well as the **OpenOffice.org3** files..

e.g.
ooobasis3.0-writer_3.0.1-15_i386.deb

what are those? Do I need them as well?

**edit:**
I double clicked:
openoffice.org3-writer_3.0.1-15_i386.deb

and got "Error Dependency is not satisfiable"

---

### Post by slick666 on 2009-01-28
Instead of installing the .debs I recommend adding open office 3 to your repos. It has worked great for me, and I've even gotten some updates since installing. The how-to isn't loading for me but there is the link to the Google cache of the web page.

[http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a]("http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a")

I hope this works for you

---

### Post by ChrisR1982 on 2009-01-28
Followed the step by step guide and it seems to be working.. just downloading the 57 updates hahaha

cheers for your help mate :)

---

### Post by ChrisR1982 on 2009-01-28
All downloads complete... installed.. and I just checked and yup its workin. Cheers mate!! :)

---

### Post by slick666 on 2009-01-28
I'm glad it worked I hope the links comes back

---

### Post by stchman on 2009-01-28
> **ChrisR1982 said:**
> I was rather annoyed to discover that Kubuntu did not come with the latest OpenOffice3 but figured no big deal as I could simply just update it in the adept installer... however OpenOffice3 has not been added yet so I can't upgrade.. how do I get the latest OpenOffice3 to install on Kubuntu?

I went to the OpenOffice website and downloaded 

**OOo_3.0.1_LinuxIntel_install_en-US_deb.tar.gz**

I then uninstalled my current version of OpenOffice... but how do I install from that file?

I have a script that will uninstall OO2.4 under Hardy and Intrepid and install OO3.0

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

In the Scripts section.

---

### Post by NetworkGuy on 2009-01-29
> **stchman said:**
> I have a script that will uninstall OO2.4 under Hardy and Intrepid and install OO3.0

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

In the Scripts section.

Works perfectly.   Great job.

---

### Post by slick666 on 2009-01-29
I appreciate the script you made stchman but one of the things I was trying to point out to ChrisR1982 was that if you add the OpenOffice repo you can get updates to open office 3 as they come out. If you use your war you install the current deb but then you have to manually check and install updates. I think the repo way is better because it keeps you current with Open Office.

---

### Post by stchman on 2009-01-29
> **slick666 said:**
> I appreciate the script you made stchman but one of the things I was trying to point out to ChrisR1982 was that if you add the OpenOffice repo you can get updates to open office 3 as they come out. If you use your war you install the current deb but then you have to manually check and install updates. I think the repo way is better because it keeps you current with Open Office.

I agree, I wrote this script a while back.  I was not aware that there was an Openoffice.org 3.0 repo available for Ubuntu.

---

