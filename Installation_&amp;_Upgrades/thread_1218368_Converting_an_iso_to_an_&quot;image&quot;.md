---
title: "Converting an iso to an &quot;image&quot;"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by PhoHammer on 2009-07-20
I've been looking for a small linux distro that could work like **Splashtop** on my notebook
 (you can read about Splashtop here if you don't know what it is: 
[http://www.splashtop.com/](http://www.splashtop.com/) , it's essentially a very fast booting linux distro built into the 
motherdrive) 

So I found **xPUD** ([http://www.xpud.org/index.en.html](http://www.xpud.org/index.en.html)) and found that I could install it 
quite easily to my HDD following the directions on the "Install on Hard Drive" tab on this 
page:
[http://www.xpud.org/download.en.html](http://www.xpud.org/download.en.html). 

This image installed so easily-- I just put the image file in my root directory and put an 
entry for it in my grub's menu.lst-- that I want to see if I can convert other isos to this
format. Can I do this with some program or did the developers of xPUD do this by 
themselves? I tried putting an iso in my root and it didn't boot-- rhymage:D. 

There's probably a downside to "installing" distros this way, but maybe it will be 
irrelevant in light of what I want to use the fast booting distro for (merely surfing
the web).

---

### Post by hellmet on 2009-07-20
That is certainly a neat idea!  So the distro unpacks the .iso and then boots it?

I've been thinking of creating a distro extremely basic and fast for my graduate project.. It would be awesome if one could just unpack a .iso or .zip onto a flash drive, plug it in and then boot in a few seconds to a minimal desktop. 

Thanks for sharing the info, amigo!

---

### Post by PhoHammer on 2009-07-20
> **hellmet said:**
> That is certainly a neat idea!  So the distro unpacks the .iso and then boots it?

I've been thinking of creating a distro extremely basic and fast for my graduate project.. It would be 
awesome if one could just unpack a .iso or .zip onto a flash drive, plug it in and then boot in a few seconds to 
a minimal desktop. 

Thanks for sharing the info, amigo!

Yeah, it is a really cool idea! I know ubuntu and moblin have both been working towards faster boot times, 
but a stripped down OS that boots this fast (xPUD boots in about 3 seconds from grub on my laptop) is 
really interesting. Google's Chrome OS is also aiming for sub-10 second boot times.

That is my question though, how does this "image" file boot? My intention is to find another quick booting 
distro (one that supports my wireless card, as xPUD is in beta and only the hardwired ethernet appears to 
work...) and install it the way i mentioned in the original post.

---

### Post by PhoHammer on 2009-07-20
So I figured out that you can look at and extract files from an ISO using ubuntu's archive
manager. I looked in the xPUD iso (not the image file) and found a file of the exact same
size as the image file that grub is able to boot from my HDD (both are 50.7 MB)

So I started thinking this might be the same exact file and I tried to boot it just like
the image file provided for the manual HDD install. And it did boot just like the other file.

If you follow what I have done, this means that the ISO contains the image file that
is bootable on its own.

Taking this further, I downloaded the Damn Small Linux ISO and extracted what appeared
to be its image file (it takes up the majority of the space in the ISO) which is called
KNOPPIX-- I'm assuming this is because the distro is based on Knoppix. Well, attempting
to boot from this file does not work... I'm going to try a couple of other distros (again
looking for the large file in the ISO) to see if they will boot like this.

Anyone else have an idea?

---

