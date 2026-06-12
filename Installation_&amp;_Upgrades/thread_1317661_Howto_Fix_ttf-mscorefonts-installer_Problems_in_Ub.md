---
title: "Howto: Fix ttf-mscorefonts-installer Problems in Ubuntu 9.10 Karmic Koala"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by jonathank89 on 2009-11-06
I wrote up a pretty detailed howto on getting around this problem, in short you uninstall the ttf-mscorefonts-installer and then use my script to download and install the fonts if you so choose to.

My script is pretty basic i just use standard bash commands to get/extract/rename and install the fonts in the correct place.

Here's my howto: [link]("http://friendlytechninja.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/")

[http://friendlytechninja.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/]("http://friendlytechninja.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/")

Hope it helps some people out.

---

### Post by tomsp on 2009-11-07
Thanks, I took a couple of runs at it to get all fonts to download and install but a great and easy to follow work around workaround!

(only thing to add is use "chmod" instead of "chmon" when converting to executable file)

Thanks again :D

---

### Post by jonathank89 on 2009-11-07
> **tomsp said:**
> Thanks, I took a couple of runs at it to get all fonts to download and install but a great and easy to follow work around workaround!

(only thing to add is use "chmod" instead of "chmon" when converting to executable file)

Thanks again :D

Glad to help, it was driving me mad and was so happy when I found a work around hopefully they ubuntu team fix the bug.

Also, yes it should be chmod, i had a small typo, but it's fixed now thanks.

---

### Post by Fuith on 2009-11-09
Seems to be working again :D. I just installed wicd with fonts.

---

### Post by ParadoX_89 on 2009-11-14
Thanks man this really helps.I hope you dont mind that I translated your How-to into Bulgarian for the Bulgarian users.THANK YOU!;)

---

### Post by drpjkurian on 2009-11-15
> **jonathank89 said:**
> I wrote up a pretty detailed howto on getting around this problem, in short you uninstall the ttf-mscorefonts-installer and then use my script to download and install the fonts if you so choose to.

My script is pretty basic i just use standard bash commands to get/extract/rename and install the fonts in the correct place.

Here's my howto: [link]("http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/")

[http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/](http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/)

Hope it helps some people out.

Hi Jonathan

Thanks a lot. I will definitely inform everyone who has this problem

Thanks once again

With regards
Dr Kurian:P

---

### Post by squiddy on 2009-11-15
hi, how do i cange the mirror on the script to cdnetworks-kr-1.dl.sourceforge.net ? 

coz nchc.dl.sourceforge.net isn't loading on my connection

---

### Post by squiddy on 2009-11-15
nevermind, i got it

add this '?use_mirror=cdnetworks-kr-1' 

thx for the resolution bro, u saved my time (and my work) :D

---

### Post by Golem XIV on 2009-11-17
I recently replied to a similar problem [here]("http://ubuntuforums.org/showthread.php?t=1329225").

The problem is that in some configurations (usually involving wireless routers) there is a considerable time delay until Ubuntu manages to contact the correct DNS and resolve the IP address.  The problem is compounded by Ubuntu not having a local, persistant DNS cache.  This causes wget in the install script to time out (the default time is too low) and return a "URL not found" error.

The solution to this problem can be found in [this thread]("http://ubuntuforums.org/showthread.php?t=331850"), but more specifically for Jaunty/Karmic in [this specific post]("http://ubuntuforums.org/showpost.php?p=7902019&postcount=33") of that thread.

This should solve the problem underneath the ttf-mscorefonts issue and also improves your browsing experience ;.)

---

### Post by mario0318 on 2009-11-19
Awesome, Golem. Youre the man. Setting up the DNS caching on ubuntu did the trick with the ttf-mscorefonts issue.

:popcorn:

---

### Post by dr_twinsen on 2009-11-20
Yes, Golem, this fixed my problem.
I'm a newbie on Linux, so any help is good.
Thanks!

---

