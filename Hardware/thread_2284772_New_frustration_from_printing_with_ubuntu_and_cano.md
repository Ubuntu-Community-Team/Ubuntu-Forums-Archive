---
title: "New frustration from printing with ubuntu and canon pixma ip4300"
date: 2015-07-01
forum: Hardware
---

### Post by mikebellamy2k on 2015-07-01
I have been bashing my head against the wall trying to get Ubuntu 12.04 to print on the above printer as the colours are on the screen. I have managed to print colour photos by tweaking the colour channels but don't want to have to do this for every image I print. Black and white always seems to come out the same also with a green yellow colour and not true black and white. I have set the printing to cymk and have tried the grayscale addition button to the print options. I have looked on some forums for fixes and haven’t found a simple or workable one. This would have worked with windows (pah) Not so with Ubuntu as the canon software is not compatible. Any help please as I keep on coming up against problems when only trying to do normal tasks with Ubuntu i.e. connecting phones etc!!

---

### Post by weatherman2 on 2015-07-01
I have a couple of Pixma printers too.  Built-in drivers in 12.04 did not work so well for them.  I was able to use drivers from Canon instead and they fixed some problems but also left me without certain features e.g. the ability to print greyscale/B&W.

Then I tried Ubuntu 14.04 and found the built in drivers worked quite well.  I was able to download and build a newer version of Gutenprint in 12.04 - same version used in 14.04 I think - and now I'm much happier printing with native drivers to my Pixma printers.

So...I'd try booting 14.04 live USB and seeing if built-in printer drivers work better for you.  If so, you can try to do exactly what I did and built the latest Gutenprint in 12.04.  Of course, you'd also have the option to upgrade to 14.04 as well.

---

### Post by mikebellamy2k on 2015-07-03
Solved!!! Hopefully. After hours of looking for an easy fix and messing about with every setting possible it seems installing the canon driver from the terminal after removing the auto detected ip4300 printer from the printer dialogue it now prints as is seen on the screen. or good as so far. heres the link if any one needs it and it will hopefully work for other models as loads are listed. just follow the instructions. I don't post much on the forums but this is a good result and hope it solves other peoples issues too so thought would. :P

[http://ubuntuhandbook.org/index.php/2013/07/canon-drivers-for-ubuntu-and-linux-mint/](http://ubuntuhandbook.org/index.php/2013/07/canon-drivers-for-ubuntu-and-linux-mint/)

---

