---
title: "Problem with HP Photosmart D5160"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by nabuchodonozor on 2007-04-28
I have got a serious problem with my printer.

I installed HPLIP drivers  ([http://hplip.sourceforge.net/install/index.html]("http://hplip.sourceforge.net/install/index.html")) without any errors. My printer prints correctly on a paper, but I can't print on CD/DVD.

My printer wokrs with CD tray ( I can see movement ). When I try to print something (on CD), D5160 reports an error (red light). Ubuntu 6.06 doesn't report any errors. 

An image is putting on a queue (something like "System->printers"). 

I made a CD cover in "cdlabelgen". I tried to print it using KGhostView and Gwenview. (Properties : "CD or DVD 120mm" ; "CD or DVD tray" ).

Have you ever seen something like that ??   
What I should to do ??
Can I print on CD by Gwenview?

I think my computer sends a bad data to printer - but it may be wrong idea 

Sorry for my english...

---

### Post by PrivatePickle on 2007-05-05
I have an HP D5160, I haven't tried cdlabelgen but I have printed directly onto one cd using
gimp as described in the following link.

[http://ubuntuforums.org/showthread.php?t=180580&page=2](http://ubuntuforums.org/showthread.php?t=180580&page=2)

The only thing I did different than listed in the thread was open up the HP Device
Manager under Applications - Accessories and select the page size and media source
there as well as in the gimp printing options just to make sure.  It worked great except
that the image was about .25 inches to low and to the left so I will have to play with the 
adjustments.  I wonder if I can clean the disc off and print again?

Other than the alignment being further off than when printing in a couple of windows 
programs I have tried it worked very well.

Also I am running Ubuntu 7.04 and using the latest hplip (1.7.4a) driver installed using the
automated installer from here ([http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)) not the
one found in Synaptic.

---

