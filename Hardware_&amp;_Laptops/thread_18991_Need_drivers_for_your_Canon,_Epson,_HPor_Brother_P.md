---
title: "Need drivers for your Canon, Epson, HPor Brother Printer? Free Turboprint!"
date: 2005-03-09
forum: Hardware &amp; Laptops
---

### Post by landotter on 2005-03-09
Silly bunnies at Turboprint want you to pay $30/year to use their drivers. That's outrageous for private use!!

I installed Turbo print for my i475 to check it out, and indeed the quality was great! You ran their little installer script and followed the simple instructions. But with the free edition, they print a huge logo on every page...

So I did some research on the Turboprint site on how to get it to work with Gimp. Right there on their own website, they told me to install the .ppd driver directly from the /usr/share/turboprint/ppd directory. Sure enough, in there were every single driver listed on the site.

So I did an experiment and used Gnome-cups-manager under Computer/System configuration, and added another printer--there already was one created by Turboprint. This "other" printer of course was the same Canon i475. I pointed it directly at the .ppd file, and ran a test page. No logos this time.

So I pulled up the properties of these two queues and behold:

[img]http://photos7.flickr.com/6224391_602cb87d9d_o.jpg[/img]

check out the license type. Apparently it IS FREE FOR PERSONAL USE! I wish they'd said so on the website.

So feel free to do as I did if you use your printer at home and not for business.

Supported models:
[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

---

### Post by mac57 on 2005-03-11
Interesting. I just tried this exact procedure on my Mandrake 10.1 system (just got Ubuntu 5.04 today and started reading these forums - haven't managed to get Ubuntu installed yet, and so tried it on my Mandrake) and it didn't work. After creating the second printer, by pointing directly at the /usr/src/turboprint/ppd folder, and picking my Canon i950 driver, I still got the big logo in the middle of each page.

Is there anything else you needed to do to make it work? Thanks.

---

### Post by landotter on 2005-03-11
Well, I do have a regular "license key" installed, but I was simply using the .ppd file straight. for the top half of the screendump above. Perhaps it checks the license, but I doubt it as it's a plain text file that you could edit yourself. It does say "Free Edition for Private Use", which seems pretty clear to me. Otherwise I would't go posting it on a public forum such as this.

PM me and I'll send you the corresponding .ppd file by email if you want and we can see if it works better than yours.

---

### Post by hector on 2005-03-14
any luck with this? I have a Canon i950 and I'm recently moving from windows to Linux Ubuntu (I'm so happy up to now). I found in a forum a link to a free japanese driver for the i950 (canon japan ftp). I haven't tryed it yet...


hector.

---

### Post by trigg on 2005-03-15
[QUOTE=hector]any luck with this? I have a Canon i950 and I'm recently moving from windows to Linux Ubuntu (I'm so happy up to now). I found in a forum a link to a free japanese driver for the i950 (canon japan ftp). I haven't tryed it yet...


hector.[/QUOTE]

Okay, so turboprint costs money.  I agree that it is not the best solution - but it is a solution that works, and I frankly don't have the free time to spend trying out free driver after free driver, so I pay for turbprint and I am very happy that at least it works.  I have a Canon i850s. With Ununtu, it is still cheaper than shelling out the bucks for Win XP pro and dealing with the security nightmare and lack of a good terminal. ;)

---

### Post by rykel on 2005-03-15
no, sorry, it does NOT work... e logo is still there, thanks for e effort.

---

### Post by landotter on 2005-03-15
[QUOTE=trigg]Okay, so turboprint costs money.  I agree that it is not the best solution - but it is a solution that works, and I frankly don't have the free time to spend trying out free driver after free driver, so I pay for turbprint and I am very happy that at least it works.  I have a Canon i850s. With Ununtu, it is still cheaper than shelling out the bucks for Win XP pro and dealing with the security nightmare and lack of a good terminal. ;)[/QUOTE]
 Look I'm all for people making money from good honest proprietary software.

But the TurboPrint people aren't terribly decent in my opinion.

A printer driver is a simple plain text 20kb file that a competent coder should be able to flesh out in an evening.

It simply does not warrant a payment of $30 (usd) per year.

If anybody from TurboPrint is reading this: I am not advocating stealing your software for commercial purposes--but you should be ashamed of yourselves for charging such an outrageous lisence fee and only limiting it to a year. May your business fail, and if that doesn't happen, may monkeys fly out of your anus.

---

### Post by photoworks on 2007-05-07
> **landotter said:**
> Silly bunnies at Turboprint want you to pay $30/year to use their drivers. That's outrageous for private use!!

I installed Turbo print for my i475 to check it out, and indeed the quality was great! You ran their little installer script and followed the simple instructions. But with the free edition, they print a huge logo on every page...

So I did some research on the Turboprint site on how to get it to work with Gimp. Right there on their own website, they told me to install the .ppd driver directly from the /usr/share/turboprint/ppd directory. Sure enough, in there were every single driver listed on the site.

So I did an experiment and used Gnome-cups-manager under Computer/System configuration, and added another printer--there already was one created by Turboprint. This "other" printer of course was the same Canon i475. I pointed it directly at the .ppd file, and ran a test page. No logos this time.

So I pulled up the properties of these two queues and behold:

[img]http://photos7.flickr.com/6224391_602cb87d9d_o.jpg[/img]

check out the license type. Apparently it IS FREE FOR PERSONAL USE! I wish they'd said so on the website.

So feel free to do as I did if you use your printer at home and not for business.

Supported models:
[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

hello,
i just tried the steps you explained and it still print the logo in the middle of the page.
i have a canon i950.

i tried then to look for the ppd file for my printer that some says is located on the manufacturer cd or in the windows partition. however,did not have any success either.

THis is quite annoying, especially since everybody wants to promote linux as the perfect alternative to windows. 

While i do not deny that linux is impressive, by and large, there are still some stuff one cannot do (case in point,  trying to find a damned driver for a printer or having your graphic tablet working perfectly on linux) 

i tried turboprint but i am not ready to pay $30. can't believe you have to pay for a simple printer driver when you can have complex softwares such as gimp, inkscape or blender for free (after all those softwares must have requires more hours of development than a simple driver.

Would very much like to know either where to find a i950 canon ppd file or how to fiddle with the one from turboprint so that i could print without the logo.

Help would be very much appreciated.

---

### Post by Erlander on 2007-05-08
Have a look at:

[http://ubuntuforums.org/showthread.php?t=10540&highlight=canon+i865](http://ubuntuforums.org/showthread.php?t=10540&highlight=canon+i865)

Drivers are at:

[ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)

Rob

---

### Post by robenroute on 2007-05-08
> **photoworks said:**
> hello,
i just tried the steps you explained and it still print the logo in the middle of the page.
i have a canon i950.

i tried then to look for the ppd file for my printer that some says is located on the manufacturer cd or in the windows partition. however,did not have any success either.

THis is quite annoying, especially since everybody wants to promote linux as the perfect alternative to windows. 

While i do not deny that linux is impressive, by and large, there are still some stuff one cannot do (case in point,  trying to find a damned driver for a printer or having your graphic tablet working perfectly on linux) 

i tried turboprint but i am not ready to pay $30. can't believe you have to pay for a simple printer driver when you can have complex softwares such as gimp, inkscape or blender for free (after all those softwares must have requires more hours of development than a simple driver.

Would very much like to know either where to find a i950 canon ppd file or how to fiddle with the one from turboprint so that i could print without the logo.

Help would be very much appreciated.


I've been using TurboPrint for a few years now and their drivers are top notch. The only gripes I have with TurboPrint is the fact that they're still using GTK1 instead of GTK2. Developing and testing drivers costs time/money. These people have decided to ask for money. Nothing wrong with that. The choice is yours. If you don't like forking out money you can try the drivers from Canon (as referred to by the previous poster) or go with an HP printer. Brother also has proper Linux drivers/support.

Linux is becoming more mature and a more interesting choice for many a person and/or company. With this, commercialization of Linux software will also increase. Better get used to it! ;-)

---

