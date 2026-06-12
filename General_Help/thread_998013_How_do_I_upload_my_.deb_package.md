---
title: "How do I upload my .deb package?"
date: 2008-11-30
forum: General Help
---

### Post by bgs100 on 2008-11-30
Hi, I have made a program for linux, then made a .deb package for it.  It is written in FreeBASIC (just a side note).  How do I get it to GetDeb, a repository, or wherever?  


My deb is a text calculator.  You can run it alone with icalc or in a terminal with icalc-term. It does adding, subtracting, multiplying, dividing, exponents, natural logs, many conversions, percentages, memory, and has Pi and Pi*2 recognition.

Edit: I am abandoning this project.  I found some bugs, and didn't know about bc at the time of making it.  Now I am going to this project :  [ATTACH]101343[/ATTACH]
It is a GUI zenity shell script that lets you backup and restore your hard drive.

By the way, iCalc (although now abandoned) is at GetDeb

---

### Post by soro2005 on 2008-11-30
Why would anybody trust you enough to install your binary if you don't even tell what it does?

---

### Post by StOoZ on 2008-11-30
I think he just want to know what is the procedure to have your deb file in getdeb...

---

### Post by soro2005 on 2008-11-30
Well, I guess you PUBLISH THE SOURCE CODE and send it to the people who run Getdeb. To get it into the repositories, you PUBLISH THE SOURCE CODE and propose it for inclusion. I'm sure he's a genius and producing some seriously useful software. But this is not some warez site where people can package their viruses give them some fancy name, and go fishing.

---

### Post by wersdaluv on 2008-11-30
You can make a deb but you don't know how to upload it. hehe. It's kinda ironic. You can upload it somewhere like rapidshare and tell people who will likely trust you to download and install it. :)

---

### Post by Tobster on 2008-11-30
I would forward it to Launchpad - They deal with all that kind of stuff.

The Link is:

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by bgs100 on 2008-11-30
I have upgrade my deb package and edited my post to tell you what it does.  Here is a screenshot of it.  You can examine it with the package installer, which tells you all files.  You can unzip it and look through, if you want.
[ATTACH]94755[/ATTACH]

---

### Post by bgs100 on 2008-12-01
Upgrade.  Now has memory, help, and pi recognition.

---

### Post by kostkon on 2008-12-01
You can have your own repository (called *PPA*, i.e. *Personal Package Archive*) on *Launchpad* for free. You only need to upload the source package and the rest is done by *Launchpad*.

Check [here]("https://help.launchpad.net/Packaging/PPA") for info.

Hope that helps :)

---

### Post by bgs100 on 2008-12-03
well, even before you posted (person above) I had tried, but I am clueless as how to make a source package.  I know, its stupid; I can make a .deb but not a source package.  I read a ubuntu howto but it didn't help much.  And, my source code is in FreeBASIC.  Can Launchpad compile that?  By the way:
  Upgrade.  Now at version 0.30

---

### Post by bgs100 on 2008-12-05
Sort of Solved.  I made a project on launchpad for it.  I am now developing v0.32.  Unfortunately, I can still not add it to my PPA :-(.  I hope to get someone working on the project who can create a REAL source package (I have made a crude one with only source that cannot install).  Any volunteers with a launchpad account?

[https://launchpad.net/icalc]("https://launchpad.net/icalc")

---

### Post by bgs100 on 2008-12-06
bump

---

### Post by bgs100 on 2008-12-08
Through launchpad, SOFTPEDIA got my program. 17 Downloads!  A softpedia guy downloaded it and took a screenshot.
[http://linux.softpedia.com/get/Science-and-Engineering/Mathematics/iCalc-43564.shtml]("http://linux.softpedia.com/get/Science-and-Engineering/Mathematics/iCalc-43564.shtml")

---

### Post by bgs100 on 2008-12-09
Has anyone tried it?

---

### Post by karlr42 on 2008-12-09
Interesting niche. I guess dc and bc are the only other CLI calculators out there. Though to be honest, I'd personally just use perl or python to get the same functionality(I use gnome-calculator mainly, never needed a CLI calc).

---

### Post by bgs100 on 2008-12-09
(replying to above)
Well, iCalc has built in conversions and percentage functions (more than the gnome calc), which save more time than looking up or googleing the conversions

---

### Post by Technoviking on 2008-12-09
I would suggest talk the Ubunru MOTUs, they can help you with packaging, using PPAs, and even getting your program included in the Ubuntu universe repository.

[https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

---

