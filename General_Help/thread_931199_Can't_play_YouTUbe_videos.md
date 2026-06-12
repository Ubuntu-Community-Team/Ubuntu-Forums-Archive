---
title: "Can't play YouTUbe videos?"
date: 2008-09-27
forum: General Help
---

### Post by NintendoTogepi on 2008-09-27
I can't play them, it tells me to enable javascript 
9which there is no option to do so on FF) or download the next version of flash player, but there's 3 kinds, and I've tried all three, none of which install right.

---

### Post by ad_267 on 2008-09-27
Uninstall the flash plugins from firefox then go to System - Administration - Synaptic Package Manger. Search for ubuntu-restricted-extras and install it. That will give you other things like mp3 codecs too. If you just want the flash player it's flashplayer-nonfree I think.

---

### Post by NintendoTogepi on 2008-09-27
Is that the only way? I enabled javascript now that I found the option to do so.

---

### Post by zzzzz1 on 2008-09-27
downlaod the tar.gz from here [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

than unpack it.

double click the flashplayer-installer  file 

select "run in terminal"

close FF 

should look like this

----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/ubuntu/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.

---

### Post by ad_267 on 2008-09-27
> **NintendoTogepi said:**
> Is that the only way? I enabled javascript now that I found the option to do so.

Javascript should have already been enabled. No that's not the only way but it's the best way and the recommended way.

---

### Post by la souris on 2008-09-28
I can't play videos too.

> **zzzzz1 said:**
> downlaod the tar.gz from here [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

than unpack it.

double click the flashplayer-installer  file 

select "run in terminal"

close FF 

should look like this

----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/ubuntu/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.

I have done it but videos on youtube still don't run. (And there is no xpti.dat on my computer at all)
What should I do?

---

### Post by zzzzz1 on 2008-09-28
Open FireFox and go to about: plugins.
See if you have swfdec or gnash (or both) there.
What you want to see is something like Shockwave Flash.
If you have the others installed they will conflict, so uninstall them.

this was originally posted by   
Sorivenul  in this post 
[http://ubuntuforums.org/showthread.php?t=931908&highlight=gnash](http://ubuntuforums.org/showthread.php?t=931908&highlight=gnash)

---

