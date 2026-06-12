---
title: "No X-windows"
date: 2006-02-17
forum: Hardware &amp; Laptops
---

### Post by Eric the Grey on 2006-02-17
I thought I'd try to dual-boot on my new laptop, a Copmpaq Presario, but X will not start.

I've used the command line configuration tools in the past to overcome this, but cannot find them on Ubuntu 5.10.4.  

Could someone point to their location and/or name?  It used to be xf86configurator or xf86config.


:cool: Eric the Grey

---

### Post by christhemonkey on 2006-02-17
```
sudo dpkg-reconfigure xserver-xorg
```
That sould give you lots of multichoice questions about your setup.

---

### Post by heimo on 2006-02-17
Correct way to reconfigure Xorg in Ubuntu is to use this command:
```
sudo dpkg-reconfigure xserver-xorg

``` 

More info:
[http://www.ubuntuforums.org/showthread.php?t=83973]("http://www.ubuntuforums.org/showthread.php?t=83973")

---

### Post by Eric the Grey on 2006-02-17
Thank you both.

After doing some more digging, and finally attempting to start X from the command line, I got more information. Seems there is a problem with the default Raidon drivers.  Several others have reported the same error (DRIScreennit failed)

There are several threads I'll have to look into at home.  I can't connect the laptop to the work network (they're picky about things like that for some reason).


:cool: Eric the Grey

---

### Post by ronhawker on 2006-02-17
We may have the same unit. Mine is the Compaq M2105us. I had the same issue of can't run xwindows after install. I did see one link on xorg setup on a v2000 model when I googled. I have not tried it yet. I think the v2000 is about the same inside. My son has one of those but have not tried anything on that. Mine is upgrade to XP Pro, 512mb more memory and a firewire pcmcia card to run a 80gb hardrive externally. Excellent laptop. Let us know if you get it running and I'll do the same.

---

### Post by Eric the Grey on 2006-02-18
Well, I did come across this thread over on a Gentoo forum and am currently downloading the kernel source (2.6.12) and will attempt to rebuild the kernel (something I've not done before) with the indicated modules built in.

[http://forums.gentoo.org/viewtopic.php?t=105524&highlight=radeon+2+6+x](http://forums.gentoo.org/viewtopic.php?t=105524&highlight=radeon+2+6+x) 

use: [COLOR="Blue"]sudo apt-get install linux-source-2.6.12[/COLOR] to get them.

I'm not sure about the ati drivers because they do not show up in apt. I suspect that is because they are binary only.  I'm going to have to find out where they can be obtained from.

Now to play with make menuconfig

Edit:  After getting into menuconfig, I discover that the indicated option IS actually selected by default as a module.  Guess Im back to square one.


:cool: Eric the Grey

---

### Post by Eric the Grey on 2006-02-21
Any luck yet ronhawker?  

It seems like the Ubuntu (and Kubuntu) distros, or perhaps Debian itself is the problem.  Something in the way X is set up under this distro is causing a problem.

I've tested a couple of different live CDs, including the Kubuntu Live) and they all work, except for kubuntu.

So it seems to me that the solution is another distro. :(  It's too bad, because I do like the Ubuntu setup.

I'm trying Suse 10.0 now, but I'm on the third installation attempt (I haven't gotten Suse to install on ANY machine since 7).  If that fails again, I'll wait until Debian finishes downloading and give that a try.

:cool: Eric the Grey

---

### Post by slavik on 2006-02-22
I used the command mode and simply changed the "ati" to "vesa", then installed ati's drivers and it all works. :)

---

### Post by Eric the Grey on 2006-02-22
[QUOTE=slavik]I used the command mode and simply changed the "ati" to "vesa", then installed ati's drivers and it all works. :)[/QUOTE]


What package did you use to get the ATI drivers?  The package used in the thread I mentioned above don't seem to exist in apt.

Edit/Update:  I switched to vesa and it still did not work.  However, in another thread, someone mentioned rebooting to get the drivers out of memory.  Once I did that, all was golden! \\:D/ 
 
To you, sir Slavik:  =D>  Thank you!

:cool: Eric the Grey

---

