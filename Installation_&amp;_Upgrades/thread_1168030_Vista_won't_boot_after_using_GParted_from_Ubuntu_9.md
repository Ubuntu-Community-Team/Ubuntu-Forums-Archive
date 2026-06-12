---
title: "Vista won't boot after using GParted from Ubuntu 9.04 LiveCD"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by caysyka on 2009-05-23
I had some unallocated space on my disk, and the Ubuntu installer wouldn't let me use it for the installation. So I used GParted to expand my Vista partition to include that space. After that, I tried running the Ubuntu installer, but it wouldn't do the automatic partitioning thing any more, and now Vista won't boot. I would like to have my system dual-boot properly, preferably without having to re-install Vista, as I don't have the recovery disks handy.

---

### Post by coffeecat on 2009-05-23
> **caysyka said:**
> So I used GParted to expand my Vista partition to include that space.

Oops! You weren't to know of this foible of Vista, but have a look at [this page]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/"). It's to do with shrinking a Vista partition, but any resizing of a Vista partition not using Vista's own resizing tool is problematic.

> **Using Linux to Resize**

You can also use the [gparted live cd]("http://gparted.sourceforge.net/livecd.php") to resize your partitions. The problem with this is that it will definitely cause your system to not boot anymore unless you follow some [very specific steps]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/"), because Vista can't handle it.That second link is [here]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/"). It looks as though you need a proper Vista installation disc to repair the Vista C:\ partition. Your recovery discs probably wouldn't have been of help anyway. Do you know anyone you could borrow a Vista disc from? You only need the recovery console.

---

### Post by coffeecat on 2009-05-23
Just to add to my earlier post above...

If you can't get hold of a Vista installation DVD, but have access to a running version of Vista SP1 (a friend's perhaps), apparently you can make yourself a recovery console disc with it. See...

[http://www.howtogeek.com/howto/windows-vista/how-to-make-a-windows-vista-repair-disk-if-you-dont-have-one/](http://www.howtogeek.com/howto/windows-vista/how-to-make-a-windows-vista-repair-disk-if-you-dont-have-one/)

However, the next link below says that you need to do a small hack first - follow the link in the update paragraph ...

[http://www.istartedsomething.com/20070929/vista-sp1-recovery-disc/](http://www.istartedsomething.com/20070929/vista-sp1-recovery-disc/)

And failing that, the recovery console disc is available for download here...

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by caysyka on 2009-05-23
> **coffeecat said:**
> And failing that, the recovery console disc is available for download here...

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

So, I downloaded that recovery disc and burned it, but Vista is still having the same issues, even when I boot from the disc. (Yes, I checked that I really was booting from the disc). It has the "Windows is loading files..." loading bar, then the green loading bar thing with the copyright message appears, and when that goes away, the screen is blank and stays that way for at least five minutes.

---

### Post by coffeecat on 2009-05-24
> **caysyka said:**
> So, I downloaded that recovery disc and burned it, but Vista is still having the same issues, even when I boot from the disc. (Yes, I checked that I really was booting from the disc).

But that won't be your hard disc installation of Vista having the issues. When you boot from a Vista DVD, whether the full install version or this special recovery console CD, you're booting into the cut down Windows PE. It must be the disc version of Vista having issues this time.

> **caysyka said:**
> It has the "Windows is loading files..." loading bar, then the green loading bar thing with the copyright message appears, and when that goes away, the screen is blank and stays that way for at least five minutes.

I would guess the disc image might be corrupt. I see they don't publish a md5sum for you to check the integrity of the image - or isn't that function built into torrents? Or perhaps a bad burn. Try to burn it again, but at a slower speed. What about the CD you used? Was that new of a good make, or a well-used CD-RW that might be faulty? Did you download the correct version? There are 32-bit and 64-bit versions.

Whatever - I have an install of Vista that I installed from a 'proper' Vista install DVD, not a pre-installed OEM version. I hadn't bothered to make a recovery console CD for myself because I have the DVD if I ever need the recovery console. When I get time later today, I'll try the first link I gave to see whether you can do this from Vista without the little hack described in the second link. I'll post back with my findings. In the meantime, do you know anyone with Vista SP1 so that you could prepare your own recovery CD? That might be more reliable than the download.

---

### Post by coffeecat on 2009-05-24
Apologies - I misread the first link I posted, thinking it was a howto to make the recovery CD, when all it did was to link you through to my third link.

Anyway - I tried the howto in the second link.

The good news - I made myself a recovery CD which boots up fine and offers to repair my Vista partition. I didn't proceed because it's not broken - yet.

The bad news - the howto is incomplete. What it doesn't tell you is that once you got the earlier version of recdisc.exe copied over and running, it prompts you for the install DVD to copy stuff off it so that it can make the repair CD. So you need the install DVD before you can make the repair CD, and if you've got the install DVD you don't really need the repair CD.

Hmmm.

---

### Post by caysyka on 2009-05-25
I don't know what's going on anymore with this thing. I re-burned the disc at a slow speed and had the same issue, I re-downladed the iso and then re-burned the disc at a slow speed, and it still does the same thing. I think I'll try calling tech support unless someone here has a brilliant idea.

EDIT: I'm just giving up and installing Ubuntu (Xubuntu, actually, but same difference) on the whole hard drive. I got all the important files off, and it's not like Vista could run at a reasonable speed anyway (Hence the original desire for Linux on it). If I really, really want Vista back, I can always call Toshiba and get the restore discs from them.

---

