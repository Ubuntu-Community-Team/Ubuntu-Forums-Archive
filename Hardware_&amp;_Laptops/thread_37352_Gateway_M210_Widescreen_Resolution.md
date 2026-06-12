---
title: "Gateway M210 Widescreen Resolution"
date: 2005-05-26
forum: Hardware &amp; Laptops
---

### Post by wreckingcru on 2005-05-26
I have the above mentioned laptop with the widescreen resolution of 1280x768.

But using Hoary  - the resolution is set by default to 1024x768. 

I did some research and downloaded the 855resolution program which helps adjust the resolution to 1280x768. 
But when I run the script, I need to restart Gnome. 
I'm trying to figure out how to make that script run at startup. I tried adding to the startup menu, but it screwed things way up and the computer started hanging up. 

How can I make that script run before gnome loads (i presume) so that it will adjust the screen res to 1280?

Thanks.

---

### Post by kb00heda on 2005-05-27
I'm not sure how to answer your question... but it is not possible just to add that resolution in your /etc/X11/xorg.conf to make the 1280x768 default? (Then there would be no need for running that script I guess.)

---

### Post by wreckingcru on 2005-05-27
Well, I have added to my conf file - but it doesn't work because of the 855 intel chipset.

Essentially I run this script called "855resolution" with 2-3 parameters. Then I need to restart gnome to have the resolution changed.

I'm trying to figure out how I can run this script before Gnome loads on startup.

---

### Post by Speex on 2006-05-07
Here's how I solved this issue:  Fortunately I wrote down everything I did. :)

The 855GM graphics chipset that this computer uses has an issue with
X, because the video bios doesn't include a mode for 1280x768, which
is the correct resolution for the widescreen.

Get 855resolution from [http://perso.wanadoo.fr/apoirier/](http://perso.wanadoo.fr/apoirier/) 

This program modifies the video bios in memory, replacing the
resolutions there with alternatives you specify.  I added this to my
/etc/rc.local using the line:

855resolution 58 1280 768

Everything in rc.local runs when the computer is first booted, so you'll easily avoid the problem of having to restart gnome or X.  

Hope this is helpful.

---

