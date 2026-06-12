---
title: "Wacom Bamboo Fun"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by munchy on 2008-03-21
Hi,
I have a Wacom Bamboo Fun tablet and would like to get it running on Ubuntu 8.04. I've tried various guides such as this one...
[http://ubuntuforums.org/showpost.php?p=4253232&postcount=133](http://ubuntuforums.org/showpost.php?p=4253232&postcount=133)
but they're aimed at Ubuntu 7.10/older Xorg/older kernel. I installed 8.04 with the tablet connected hoping that something might at least appear in xorg.conf....but nothing.....so i'm a bit stuck as to where to start really. Any ideas? Is there a revised version of the above howto in the pipeline?

---

### Post by oldsoundguy on 2008-03-21
since 8.04 is not officially released until April and is still in Beta, you will be hard pressed to get the pad to work.  Once the release is official, changes will, most likely, be set up for the new kernel and Wacom will write the new drivers.  Until then .. that "how to" functions quite well in 7.10 for me!  add to that this:
[http://ubuntuforums.org/showthread.php?t=553573&highlight=wacom](http://ubuntuforums.org/showthread.php?t=553573&highlight=wacom) 
to get the keys functioning.

---

### Post by Hmarroqu on 2008-03-22
YEp... me and you are basically skrewed until the drivers are set up for the new kernel...which i feel will be a little later than april...

back to Gutsy anyone?

---

### Post by ubunyou on 2008-03-25
Hey, 

I just purchased a wacom bamboo CTE450K1, I'm using Hardy, and all the tablet basics are working for me. I followed (with interpretation) the steps in this _***[how to]("http://ubuntuforums.org/showthread.php?t=631881&highlight=wacom+bamboo+howto")***_.

The only step where I deviated was taking the development version of the wacom drivers ( version 0.7.9-8, released Feb 29, 2008, and includes **2.6.24** support).

Now since Im new with the tablet I'm only doing basic stuff with it (so far ...), so two questions:
1) What features weren't working for you guys, and 
2) What ubuntu applications really take advantage of tablets?

---

### Post by oldsoundguy on 2008-03-25
I use in Intuos 3 pad.  It has an additional tool, an air brush, and that does not work YET (my understanding is that they are working on that issue.)  Although I have not tried to re-map the keys on the pad, I have read that there are a few issues with that, but I am using the default key setup and it functions just fine.

As to program

Original intent of Wacom pad was to be an editor for Photo Shop in the Mac environment.  They moved into the Windows environment with the same objective and then added full illustrator capabilities with Adobe Illustrator.  I am not a graphic artist .. so do not know what program in Linux would be an equivalent, but GIMP is the photographers choice.  It too offers an "illustrator" type of program within, but my experiences thus far have been just in the photo editing area.  In that area they are EXCELLENT and so close to Photo Shop, that if they were not FREE, Adobe would have them in court!

(and the documentation for GIMP is outstanding.  AND FREE vs paying 30 bucks for the Adobe books on Amazon!)

And I am sure that others have found additional uses for the pad within other programs. (other than just creating a touch screen for navigation.)

---

### Post by munchy on 2008-03-25
In Hardy, it seemed to screw up X and I couldn't even boot. I'm back on Gutsy and everything's working fine...might try ubunyou's suggestion with Hardy though, as the older driver is obviously what screwed things up for me.

One great app I've been using is ArtRage. ArtRage is Windows or Mac only and the version bundled with the tablet wouldn't work through Wine, however the latest version from the ArtRage site works great. To get it up and running, i'll assume you're already familiar with Wine, if not then go [here]("http://www.winehq.org/site/download-deb") first.
Download the latest free Windows version of ArtRage [here.]("http://www2.ambientdesign.com/files/artrage2.5starteredition_win.msi")
Because it's a .msi file you can't do the usual 'wine abc.exe' command to install it, you need to use the following command...
wine msiexec /i artrage2.5starteredition_win.msi
You will also need to copy gdiplus.dll (can be downloaded [here]("http://www.dll-files.com/dllindex/dll-files.shtml?gdiplus")) to C:/windows/system32, otherwise Art Rage wont run. ArtRage is a great little app, well worth this small installation hassle and doesn't have any ugly Windows dialogs/fonts so looks great too.

There's also a handy little program for adjusting pressure sensitivity, including an applet for the gnome panel [here.]("http://www.alexmac.cc/tablet-apps/") (look for the Ubuntu deb on the right)

---

### Post by perixx on 2008-03-25
*Moved to separate thread*

---

### Post by FreeDisk.NL on 2008-03-27
I really haven't tried it yet, but I think that in Ubuntu 8.04, you should just follow the steps described in the README-file, that comes with/in the file you can download here:

[http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.7.9-8.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.7.9-8.tar.bz2)

Let us know if it works. :)

---

