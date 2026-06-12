---
title: "Installing Gentoo from Ubuntu"
date: 2007-06-06
forum: Gentoo and derivatives
---

### Post by Lord Illidan on 2007-06-06
I didn't feel like downloading a gentoo live cd, so I just installed Gentoo from Ubuntu to see how it is like.

After spending a whole night..and most of the morning tinkering, I am now running emerge --update --ask world on the chrooted terminal on my Ubuntu desktop..after having recompiled the kernel because I left out the VIA Rhine drivers..

But I like it :) Dunno why..but I like it!:popcorn:

---

### Post by zaratustra on 2007-06-07
Portage is addiction my friend:) And pleasure of making your own, so **cking customized system is much bigger then clicking next while installing:) I don't have to mention amount of knowledge you acquire while doing things in DIY way

---

### Post by shane2peru on 2007-11-01
> **Lord Illidan said:**
> I didn't feel like downloading a gentoo live cd, so I just installed Gentoo from Ubuntu to see how it is like.

After spending a whole night..and most of the morning tinkering, I am now running emerge --update --ask world on the chrooted terminal on my Ubuntu desktop..after having recompiled the kernel because I left out the VIA Rhine drivers..

But I like it :) Dunno why..but I like it!:popcorn:

Can you give a brief description of how you did this?  I have a spare partition and  would like to do it from Ubuntu, mostly so I can work while things are working in the background.  Once I get the base installation I can chroot and emerge things, that isn't a problem, I need a little assitence in getting the base installed.  I already downloaded the stage3 and the portage things to save myself some time.  Those should be under step one so people can get them ahead of time and  cut install time down, by waiting on a 100MB download.  I'm may take a stab at it while waiting for a brief explanation.  But I'm not sure about chrooting into an empty partition. :D

Shane

---

### Post by rsambuca on 2007-11-01
> **shane2peru said:**
> Can you give a brief description of how you did this?  I have a spare partition and  would like to do it from Ubuntu, mostly so I can work while things are working in the background.  Once I get the base installation I can chroot and emerge things, that isn't a problem, I need a little assitence in getting the base installed.  I already downloaded the stage3 and the portage things to save myself some time.  Those should be under step one so people can get them ahead of time and  cut install time down, by waiting on a 100MB download.  I'm may take a stab at it while waiting for a brief explanation.  But I'm not sure about chrooting into an empty partition. :D

Shane

[This section of the handbook]("http://www.gentoo.org/doc/en/altinstall.xml#doc_chap5") is very easy to follow along.

---

### Post by Bachstelze on 2007-11-02
All you need is here.

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml)

Of course, you already have an installation environment, and your network is most likely already configured, so skip steps 2 and 3 ;)

---

### Post by shane2peru on 2007-11-02
Ok, this is getting on my nerves.  I have followed those instructions in the handbook, and keep running into this snag.  

```

!!! ARCH is not set... Are you missing the '/etc/make.profile' symlink?
!!! Is the symlink correct? Is your portage tree complete?

```
I made the symlink, so I know it is there here is the output of ls -l /etc/make.profile:

```
 
 ls -l /etc/make.profile lrwxrwxrwx 1 root root 60 2007-11-02 13:19 /etc/make.profile -> /usr/portage/profiles/default-linux/x86/2007.0/make.defaults

```
  My link is there.  Here is my make.defaults file:

```

# Copyright 1999-2007 Gentoo Foundation
# Distributed under the terms of the GNU General Public License v2
# $Header: /var/cvsroot/gentoo-x86/profiles/default-linux/x86/2007.0/make.defaults,v 1.2 2007/08/08 19:27:27 dev-zero Exp $

# We build stage1 against this
STAGE1_USE="nptl nptlonly unicode"

# These USE flags are what is common between the various sub-profiles. Stages 2
# and 3 are built against these, so be careful what you add.

USE="acpi alsa arts cairo cdr dbus dvd dvdr dvdread eds emboss encode esd evo fam firefox gif gnome gpm gstreamer gtk hal jpeg kde kerberos ldap mad mikmod mp3 mpeg ogg opengl oss pdf png qt3 qt3support qt4 quicktime sdl spell svg tiff truetype vorbis win32codecs unicode X xml xv"

```

And here is my /etc/make.conf
```

# These settings were set by the catalyst build script that automatically
# built this stage.
# Please consult /etc/make.conf.example for a more detailed example.
CFLAGS="-O2 -mtune=i686 -pipe"
CXXFLAGS="${CFLAGS}"
# This should not be changed unless you know exactly what you are doing.  You
# should probably be using a different stage, instead.
CHOST="i486-pc-linux-gnu"
MAKEOPTS="-j3"


GENTOO_MIRRORS="http://ftp.ucsb.edu/pub/mirrors/linux/gentoo/ ftp://gentoo.chem.wisc.edu/gentoo/ http://gentoo.mirrors.pair.com/ ftp://ftp.ndlug.nd.edu/pub/gentoo/ http://open-systems.ufl.edu/mirrors/gentoo http://mirror.fslutd.org/linux/distributions/gentoo/ ftp://mirror.fslutd.org/linux/distributions/gentoo/ http://gentoo.localhost.net.ar/ ftp://mirrors.localhost.net.ar/pub/mirrors/gentoo "

SYNC="rsync://rsync.samerica.gentoo.org/gentoo-portage"

```

So this is really getting on my nerves.  Any help on this would be greatly appreciated.  

Shane

---

### Post by shane2peru on 2007-11-02
> **HymnToLife said:**
> All you need is here.

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml)

Of course, you already have an installation environment, and your network is most likely already configured, so skip steps 2 and 3 ;)

Thanks!  Been all over that handbook, a few times now.  :)  I'm stuck on the above error, and need to 1.  Update (emerge portage) portage  2.  emerge gentoo-sources for my kernel.  I checked the md5sums of all my downloads and checked them and they were all good.

Shane

---

### Post by rsambuca on 2007-11-02
You haven't said what stage of the installation you are having these problems with.

---

### Post by Bachstelze on 2007-11-02
The symlink is wrong :

```
lrwxrwxrwx 1 root root 54 2007-10-14 18:06 /etc/make.profile -> /usr/portage/profiles/default-linux/x86/2007.0/desktop
```

---

### Post by shane2peru on 2007-11-02
> **rsambuca said:**
> You haven't said what stage of the installation you are having these problems with.

Just got portage installed and finally updated, and am wanting to build my kernel.  Guess I should have mentioned that.

> **HymnToLife said:**
> The symlink is wrong :

```
lrwxrwxrwx 1 root root 54 2007-10-14 18:06 /etc/make.profile -> /usr/portage/profiles/default-linux/x86/2007.0/desktop
```

Thanks!  It just occurred to me to check out the Gentoo forums and search for that error, and I realized it is supposed to be pointed to a folder not a file.  :)   Got it!  I had some serious problems getting my make.conf right, the mirrorselect thing doesn't work if you are not in the live CD, and I found a file on the gentoo wiki to copy how to put it in, but it was wrong!  So finally I booted into the minimal install CD of Gentoo, and got my mirror setup correctly.  Now we are moving!  Thanks for the help.

Shane

---

### Post by American_Outcast on 2007-11-02
> **Lord Illidan said:**
> I didn't feel like downloading a gentoo live cd, so I just installed Gentoo from Ubuntu to see how it is like.

After spending a whole night..and most of the morning tinkering, I am now running emerge --update --ask world on the chrooted terminal on my Ubuntu desktop..after having recompiled the kernel because I left out the VIA Rhine drivers..

But I like it :) Dunno why..but I like it!:popcorn:

I played around with Gentoo a couple of years ago. I decided that I want to give it another try. I am currently downloading the x86_64 DVD.

If this goes well Ubuntu may loose me ;) Ok, maybe not :lolflag:

---

### Post by rsambuca on 2007-11-02
> **American_Outcast said:**
> I played around with Gentoo a couple of years ago. I decided that I want to give it another try. I am currently downloading the x86_64 DVD.

If this goes well Ubuntu may loose me ;) Ok, maybe not :lolflag:

I really wouldn't bother downloading the DVD.  Why not just do a stage3 tarball installation?

---

### Post by American_Outcast on 2007-11-02
> **rsambuca said:**
> I really wouldn't bother downloading the DVD.  Why not just do a stage3 tarball installation?

I was just in the mood to do the DVD download, lol.

---

### Post by shane2peru on 2007-11-05
I highly recommend installing via Ubuntu, or any other distro as it is very easy to do.  The biggest problem that I had was getting my mirrorselect setup correctly.  Now I have the proper setup and can help post if you need help.  Installing stage 3  from Ubuntu was a great and easy learning experience.  They have great documentation.  And best of all, you can continue doing other things with your computer while waiting for a download, or compile to complete!

Shane

---

### Post by rsambuca on 2007-11-05
> **shane2peru said:**
> I highly recommend installing via Ubuntu, or any other distro as it is very easy to do.  The biggest problem that I had was getting my mirrorselect setup correctly.  Now I have the proper setup and can help post if you need help.  Installing stage 3  from Ubuntu was a great and easy learning experience.  They have great documentation.  And best of all, you can continue doing other things with your computer while waiting for a download, or compile to complete!

Shane

Yeah, the gentoo handbook really does make the installation from Ubuntu a piece of cake.  With the mirrorselect thing, I just skipped it and picked a site on my continent and had no problems.  You really don't need to use the mirrorselect at all.

---

### Post by shane2peru on 2007-11-05
> **rsambuca said:**
> Yeah, the gentoo handbook really does make the installation from Ubuntu a piece of cake.  With the mirrorselect thing, I just skipped it and picked a site on my continent and had no problems.  You really don't need to use the mirrorselect at all.

Yeah, in my case I had the wrong word that I got off a wiki or something for my make.conf for the mirror setup. It didn't allow me to connect.  Once I got that straight it was not a problem at all.  I even spent three days compiling a bunch of stuff before I ever logged into my Gentoo.  So when I did it was all setup!  Chrooting is great!

Shane

---

