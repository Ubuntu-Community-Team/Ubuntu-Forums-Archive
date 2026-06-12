---
title: "[SOLVED] java 7 needed, not in the repos"
date: 2008-10-02
forum: General Help
---

### Post by JC Cheloven on 2008-10-02
Hi all, I need to install java 1.6.0_07 to use in it firefox (for the sake of a particular web page using digital cetificates ... doesn't matter really). Synaptics has versions 05 and 06 only. 

Regarding current version 07, I saw at java.com a ".rpm" package and and ".bin" to install in linux, this one with a rather complicated installation procedure. I never used "alien", and I'm afraid of doing a bad install (I really need this for my business). So my question:

Does anyone know an easier procedure to install java07 in ubuntu?


(PS: I find a bit disappointing the absence of the current version of java in the repos.)

---

### Post by JC Cheloven on 2008-10-02
Well, self-answer (perhaps someone can benefit from it):

I had a look, and fortunately java 6 version 07 is already in the Intrepid's repository. The easiest way to get it from Hardy (I think) is:

system -> administration -> software sources
pick the actualizations tab
tick the "hardy proposed" box
close the window
system -> administration -> synaptic
search for the following packets and install them:
[INDENT]sun-java6-bin
sun-java6-jre
sun-java6-plugin
[INDENT][# you should see that now these three are version 07][/INDENT]
gsfonts-x11[/INDENT]

That should be it. At least it was for me. Please be aware that you also should install the following if not already installed: 

java-common
odbcins1debian1
unixodbc
xutils-deb

You can test that you're running the current java version at [www.java.com](www.java.com). Simply click on the "Do I have java?" link.

Oh... I can't thank myself, what a pity ... :-D

EDIT: If you leave "software sources" with the "hardy proposed" (or the "hardy backports" for that matter) box enabled, Synaptic will attempt to update many other packages that you probably don't want to update, as they may be not enough tested (yet). To avoid this, untick the related box in "software sources" when you're done updating java. This will not affect your java update, while preventing for other unwanted updates.

---

### Post by justleen on 2008-10-02
no, you cant thank your self.. but you COULD follow your own signature advice..

---

### Post by JC Cheloven on 2008-10-02
> **justleen said:**
> no, you cant thank your self.. but you COULD follow your own signature advice..

Hey man, I was just doing it, what a hurry !!  :-)

In fact I was unsure if I could mark it as solved having no answers from other people ...

---

### Post by skunkTrader on 2008-10-13
1.6.0_07 was added to the Hardy repositories today

---

