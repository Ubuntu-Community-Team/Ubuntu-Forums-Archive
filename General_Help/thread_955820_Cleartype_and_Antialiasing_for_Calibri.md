---
title: "Cleartype and Antialiasing for Calibri?"
date: 2008-10-22
forum: General Help
---

### Post by etienne@Rofti on 2008-10-22
Hi! I am running Ubuntu Hardy at the moment, and I have a nice new big LCD widescreen. I have been looking at the antialiasing and hinting so as to get the best resolution possible, but I have had one problem:

Whenever the microsoft font Calibri is used (which I have on my system) it comes out looking very bad. It is all boxy and pixel-ish, instead of nice and smooth like my other fonts. (See attached images...)

Does this have something to do with its ClearType properties? Is there a way I can get it looking as good as the other fonts I use just as often?

Any help would be greatly appreciated!

et

---

### Post by nikgare on 2008-10-22
Is calibri a cleartype/truetype font?

---

### Post by etienne@Rofti on 2008-10-23
It is a TrueType font, and when I was looking on the Internet for any clues as to why it looks so bad, I read that it is ClearType. Does that help?

---

### Post by BobCFC on 2008-11-13
The problem is because the Calibri fonts and other cleartype fonts have bitmap versions embedded in them which kick in at small sizes, so large fonts look OK but small fonts look oldfashioned.

To disable the bitmap fonts so that the small sizes look smooth follow the last post on this [thread]("http://ubuntuforums.org/showthread.php?t=724818&highlight=calibri").  

You have to create a **.fonts.conf** file in your home directory, paste in the xml code and logout.

---

### Post by etienne@Rofti on 2009-02-03
Thank you! However, I still did not manage to have any success. If anyone has any other suggestions, I would greatly appreciate it...

---

### Post by etienne@Rofti on 2009-02-03
No, actually, I solved it! I just didn't put it in the right place. The solution works! Thank you so much! I was so tired of the emails I received from all my friends in Calibri looking so bad!

Thanks again!

---

### Post by th3_survivor on 2010-11-07
> **BobCFC said:**
> The problem is because the Calibri fonts and other cleartype fonts have bitmap versions embedded in them which kick in at small sizes, so large fonts look OK but small fonts look oldfashioned.

To disable the bitmap fonts so that the small sizes look smooth follow the last post on this [thread]("http://ubuntuforums.org/showthread.php?t=724818&highlight=calibri").  

You have to create a **.fonts.conf** file in your home directory, paste in the xml code and logout.

That works great for me in Ubuntu but not in Kubuntu :( any idea why?

---

### Post by abdusamed on 2011-03-06
why did the Ubuntu stopped displaying cleartype in the first place?????

i am facing the same issue!

---

### Post by dawidmlyn on 2012-05-16
The thread mentioned above is available to registered ubuntuforums users only (why?), so I decided to cite the right solution here (I found it on [http://forums.fedoraforum.org/archive/index.php/t-191597.html](http://forums.fedoraforum.org/archive/index.php/t-191597.html) ):

To get Calibri (and Cambria, and the other Cleartype fonts) to hint correctly you need to disable embedded bitmaps within TrueType fonts. Disabling these allows the hinting and antialiasing to work like normal.

To do so, you put this block into your $HOME/.fonts.conf file:

    <match target="font" >
         <edit name="embeddedbitmap" mode="assign">
             <bool>false</bool>
         </edit>
    </match>

All the fonts should be antialiased now. I have also tested this on Kubuntu, which has the same problem (despite the *buntu family having the bytecode interpreter built-in by default), and this fixes it.

---

### Post by oldos2er on 2012-05-16
Old thread closed.

---

