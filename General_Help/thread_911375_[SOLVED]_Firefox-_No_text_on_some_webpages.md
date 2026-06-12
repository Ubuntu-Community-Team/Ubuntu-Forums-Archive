---
title: "[SOLVED] Firefox- No text on some webpages"
date: 2008-09-05
forum: General Help
---

### Post by asilaydyingdl on 2008-09-05
Hey all, I have some experience with Ubuntu, and I am usually able to fix problems myself or find help in the forums, but this one I am not able to remedy.  I am using the newest version of Firefox for my web browsing, however on some web pages, such as facebook, I have no text.  I can see the frames, colors, and images, but no text.  I can access all web pages without trouble on Opera, and when I am using XP I can as well. Anyone have any idea what is wrong?  I am running Ubuntu 8.04.

---

### Post by asilaydyingdl on 2008-09-05
I just fixed it.  After coming back with fresh inspiration, I figured out the problem.  Thanks anyways.

---

### Post by editrix on 2008-09-06
I have the same problem. Could you tell us what you did to fix it, please?

---

### Post by asilaydyingdl on 2008-09-07
I just changed my fonts.  Go edit, preferences, click on the content tab, and under fonts and colors, select "advanced" and change your fonts.  Make them bigger or choose a different ones.  Don't let websites set their own fonts so make sure that option isn't selected.  Good luck!

---

### Post by kaminem64 on 2011-07-12
in some cases this is caused by Microsoft fonts, you should replace all of the fonts (microsoft fonts) in /usr/share/fonts/truetype/msttcorefonts with fonts in windows fonts folder ( for example c:\windows\fonts)

also this may be caused by access permissions:
you should open nautilus with su (super user) permissions in Terminal:
sudo nautilus
then go to  /usr/share/fonts/truetype/msttcorefonts
then select all of the files there; right click on them; properties->permissions, now change the access permissions from none to read only

---

### Post by Starminn on 2011-12-05
> **kaminem64 said:**
> in some cases this is caused by Microsoft fonts, you should replace all of the fonts (microsoft fonts) in /usr/share/fonts/truetype/msttcorefonts with fonts in windows fonts folder ( for example c:\windows\fonts)

also this may be caused by access permissions:
you should open nautilus with su (super user) permissions in Terminal:
sudo nautilus
then go to  /usr/share/fonts/truetype/msttcorefonts
then select all of the files there; right click on them; properties->permissions, now change the access permissions from none to read only

Thank you ever so very much! I had been searching for this for quite some time and saw this thread mentioning overriding all site-specified fonts. It worked, but I didn't want to do that as sites have a reason for styling the way they do.

I had just moved my fonts from C:\\WINDOWS\fonts and many strange things began to happen, with this being one of them. As per your suggestion, running Nautilus as root and setting "Others" permissions to "Read-only" solved the problem instantly!

Though as a side not: When launching graphical (GUI) aplications, "gksudo" should be used in lieu of plain "sudo." So, this would make the command, "gksudo nautilus."

Again, many thanks for solving the mystery of Firefox not displaying text or loading disproportionate artifacts all over certain webpages.

---

### Post by WillWoodhull on 2013-03-25
> **Starminn said:**
> Thank you ever so very much! ...  Though as a side not: When launching graphical (GUI) aplications, "gksudo" should be used in lieu of plain "sudo." So, this would make the command, "gksudo nautilus."  Again, many thanks for solving the mystery of Firefox not displaying text...  And I thank you as well. My problem was a little different: I had websites, both from Google and some of my own making, where the text disappeared on the computer that I had just done a clean install of Ubuntu 12.04. It was a head scratcher. Until in following your directions I found that the MS Core Web Fonts are no longer included in the Ubuntu installation. Synaptic found their package in the repositories by searching on "Microsoft". Installing them and making sure the permissions on them were right made everything all better again.

---

### Post by oldos2er on 2013-03-25
Old thread closed.

---

