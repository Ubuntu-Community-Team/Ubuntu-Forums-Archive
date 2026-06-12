---
title: "[SOLVED] Font problems with Fluxbox styles"
date: 2008-10-27
forum: General Help
---

### Post by oleander on 2008-10-27
Hi! 

I am using Fluxbox and I have been editing one of the default styles (green_tea) to suit my needs but I can't seem to get it to display the Hooge 05_53 font. Every time I set it to Hooge, it just displays Sans. 

I attached the style .txt file to this post. I'm not quite sure what I'm doing wrong...I thought maybe the name should be spelled differently or I should use quotes but I have tried all those things and no luck! 

Any help would be greatly appreciated as I am kind of stuck...:confused:

Thanks!
Oleander

---

### Post by kerry_s on 2008-10-27
looks okay to me, try using "xfontsel" to get the whole font name.
you might also want to try the overlay, if your using the newer: [http://fluxbox-wiki.org/index.php?title=Style_overlay](http://fluxbox-wiki.org/index.php?title=Style_overlay)

---

### Post by oleander on 2008-10-27
Thank you for your suggestion. For some reason it wasn't listed in xfontsel. I tried the command to reinstall the fonts in the /home/user/.fonts folder. After doing that, for some strange reason :confused: the Hooge font still didn't show up in xfontsel. I tried to view the properties with FontForge (Element>Font Info>TTF Names) and tried the Fullname without spaces (hooge05_53) and then it decided to work! It's really strange that it didn't show up in xfontsel -- the family name was listed as "hooge 05_53" in FontForge but that family name didn't show up in xfontsel. Strange...:-k

Well, I'm glad it's solved now and thanks for your help! :D :D

---

### Post by kerry_s on 2008-10-27
> **oleander said:**
> Thank you for your suggestion. For some reason it wasn't listed in xfontsel. I tried the command to reinstall the fonts in the /home/user/.fonts folder. After doing that, for some strange reason :confused: the Hooge font still didn't show up in xfontsel. I tried to view the properties with FontForge (Element>Font Info>TTF Names) and tried the Fullname without spaces (hooge05_53) and then it decided to work! It's really strange that it didn't show up in xfontsel -- the family name was listed as "hooge 05_53" in FontForge but that family name didn't show up in xfontsel. Strange...:-k

Well, I'm glad it's solved now and thanks for your help! :D :D

well if you have it in your home folder you probably didn't run:

sudo fc-cache -vf

to search and cache all fonts.

---

