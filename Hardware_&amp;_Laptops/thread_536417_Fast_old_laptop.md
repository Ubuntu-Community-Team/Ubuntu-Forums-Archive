---
title: "Fast old laptop"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by tgpfarm on 2007-08-27
Ok, this is my plan.
I want to buy a IBM Thinkpad T40 off of ebay, and upgrade to 2 gigs of ram.  Then I want to take out the laptop HD and replace it with a CF to IDE converter with 1 gig of harddrive space.  Then using this guide ([[COLOR="Blue"]Boot to Ram[/COLOR]]("https://wiki.ubuntu.com/BootToRAM")) I want to have Xubuntu or Ubuntu (from a custom live cd image, using [[COLOR="Blue"]Reconstructor[/COLOR]]("http://ubuntuforums.org/showthread.php?t=229625&highlight=create+a+live+cd")) boot into ram.  This should be ultra fast and increase the battery life.  It shouldn't hurt the CF to bad either because once its running it won't touch the CF again.

Then using Fuse and sshfs have a remote file system on a server I have be able to save things and have my firefox profile be saved on there,  so I can bookmark things.

Does this sound feasible?

Is there anything I should consider before doing this?

Note I will also have a USB hard drive with me that I am thinking about storing repos on that I might use from time to time that will be able to be install fast from the USB (OpenOffice, gimp, etc...)

---

### Post by kerry_s on 2007-08-27
sounds good, let me know how it go's. i was planning on doing the cf to ide conversion on my laptop, since the hd seems to be on it's way out, i bought my self some time by partioning off the bad section & i'm currently using the part that's still good. i was planning to just run off the cf, max ram on my laptop is 256mb, so the to ram option won't be feasible for me. good luck to ya

---

### Post by tgpfarm on 2007-08-27
kerry_s: that would be a bad idea, CF has a limited number of times it can be read and wrote to.

---

### Post by kerry_s on 2007-08-28
> **tgpfarm said:**
> kerry_s: that would be a bad idea, CF has a limited number of times it can be read and wrote to.

i know that, i've already know how to deal with that. mines going to be a custom setup, i been practicing different setups for months. :) 
it'll be something like this->

---

### Post by tgpfarm on 2007-08-28
no thats not it.  on a normal install of linux, the OS will be reading and writing to the disk at all times.  So you will not get much like out of a CF hard drive that way.  What I want to do is have the whole OS (ubuntu) read once and loaded into ram then it will never touch the CF hard drive again.  This is pretty much like using a live cd, but it is read from a CF harddrive.  Nothing can be saved unless you save to say a USB drive.

---

### Post by kerry_s on 2007-08-28
> **tgpfarm said:**
> no thats not it.  on a normal install of linux, the OS will be reading and writing to the disk at all times.  So you will not get much like out of a CF hard drive that way.  What I want to do is have the whole OS (ubuntu) read once and loaded into ram then it will never touch the CF hard drive again.  This is pretty much like using a live cd, but it is read from a CF harddrive.  Nothing can be saved unless you save to say a USB drive.

i know what you mean, like i said i don't have the ram for that kind of setup. what i plan on doing is modifying it to write less, for instance, my /var/log is read only, browser disk cache can be turned off or a ram disk used instead, other things i have simply pointed to /dev/null.
i don't really have the skills or want to try turning Ubuntu into that kind of setup. if i needed that kind of thing, i would use DSL instead, as robert is using almost the exact kind of setup in the new version as i use on my debian build up.

i think you really need to understand what the limitations are to the setup your thinking of, for instance if your going to try to load a full ubuntu 700mb into ram, it takes a while to copy that much into ram, so boot speed is out the door, like you said a system reads & writes all the time, if you don't change that on your build, your ram is going to fill up in a day. speed is only as good as your ram, you won't see no difference than if you were running from a hd. if you think the only purpose of loading into ram is for speed, you need to think again, you take a loss in other areas.

i recommend you actually use a ram loaded system, check it out see how they have it setup, read explore, try it first. DSL is 50mb a far cry from the 700mb your going to need, but it will give you a idea of what it will be like.
I used DSL for a long time loaded in ram on a laptop with no hd, so i've been there & done that.

so grab a copy, here's the new version-> [ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/release_candidate/dsl-4.0rc2.iso](ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/release_candidate/dsl-4.0rc2.iso)

use> dsl toram xsetup
and try it, get a idea of how it works feels. good luck to you

Oh, i just remembered Knoppix is a full distro that is ram load able, you might want to try that->
[http://distrowatch.com/?newsid=03956](http://distrowatch.com/?newsid=03956)

---

