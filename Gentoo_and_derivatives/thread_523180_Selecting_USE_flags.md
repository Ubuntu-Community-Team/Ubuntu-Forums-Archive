---
title: "Selecting USE flags"
date: 2007-08-11
forum: Gentoo and derivatives
---

### Post by rsambuca on 2007-08-11
Does anyone here know of a site for good descriptions for the USE flags?  I am starting a gentoo installation, and am at the stage where I am supposed to set the USE flags before compiling the kernel (I am doing the installation via chroot from ubuntu).

I understand why the USE flags are there and how this enables you to configure your system to your own specs and uses, but I can't find any good descriptions of what the flags do.  I have found a ton of sites that provide the standard description of the flag, but they do not give enough info to tell me if I need it for something.  I have spent a few hours googling the first bunch of flags to figure it out, but there are hundreds of possible flags and at this rate, I won't finish this century.

I obviously could just go with the default desktop config, but isn't that kinda defeating the purpose of this excellent tool?

For example, from the Gentoo Linux Use Variable Descriptions:

acl - Adds support for Access Control Lists.

fine, but now I have to find out what an Access Control List is, etc.

Another question.  If I think I have them set up the way I want and set up my rig, will I have to start from scratch and re-compile everything if I later find out I missed a crucial flag?

---

### Post by termite on 2007-08-11
Good luck.  USE flag documentation is absurdly lacking.  Read [http://forums.gentoo.org/viewtopic-p-4183042.html](http://forums.gentoo.org/viewtopic-p-4183042.html)

You could start from the Desktop profile and slim down, but it'll take lots of recompiling.  The default profile isn't bad, but you need to add all the desktop stuff you need (X, qt3, qt4, gnome, etc).  If you don't want both KDE and gnome, you can do without the respective flags (qt3/4=KDE).

---

### Post by termite on 2007-08-11
If you miss out some flags, you can add them later and recompile.  It won't recompile everything, just the packages that use that flag, plus any new ones your new flags pull in.

---

### Post by rsambuca on 2007-08-11
Thanks termite.

I think what I will probably end up doing is start from the desktop default profile, and then trim down stuff from there, or add what I need.  For instance, I am pretty much a gnome guy, so I will "-kde".  Do I still have to -qt* as well?  Also, if I do this and I still want to use a specific qt application like skype or amarok, do I have to change these flags back before compiling these, or does the fact that they are qt specific mean that they will be compiled correctly regardless of the flags?

---

### Post by termite on 2007-08-11
flags are independent of each other.  You will need to do -qt3 -qt4 if you don't want any qt.

If you want any qt apps, you can just emerge them and it will pull in what it needs, regardless of your flags.  What flags do is enable optional (though sometimes near-essential) options in programs.  They really just pass on options to ./configure so you don't have to mess with that.

---

### Post by Bachstelze on 2007-08-11
If you ant to re-emarge only the packages whose flags have changed :

```
sudo emerge -avDN world
```

To change your USE flags, you can use either the USE variable in make.conf or define them on a per-package basis in /etc/portage/package.use.

Tip : always do *emerge -av package* instead of just *emerge package*, it will show all the USE flags for that package and ask if you really want to emerge it. That way, if you find something wrong with the USE flags, you can correct it before emerging the package.

---

### Post by termite on 2007-08-11
Anytime I use emerge for anything but emerging a specific package, I always do ```
emerge -avutND world
```

---

### Post by Bachstelze on 2007-08-11
Same here, though without the "t" unless I really need to track dependencies.

---

### Post by rsambuca on 2007-08-11
Thanks everyone, you are providing me with lots of good input.

One more question:  What is the difference between having "-useflag" or not having the "useflag" option listed at all?  ie, is "-kde -qt3 -qt4 -arts" much different than just leaving them out entirely?

I guess what I am trying to say is, why are the minus signs necessary if you have to first put the option into the config file in the first place?  If I want "gnome" entered, I put it as an option in the USE flags.  If I don't want gnome, can't I just leave it out of the config, or do I have to enter -gnome?

I don't think this is coming out very clearly!  but I hope you catch my drift.

---

### Post by termite on 2007-08-11
If you're using a profile, some USE flags are set in the profile.  You then have to do   -myuseflag in your /etc/make.conf to override it.  If a flag isn't in your profile, you put myuseflag in /etc/make.conf to enable it.

So, for example, if you're using the 2007.0 desktop profile, it you have to put -gnome in your /etc/make.conf to get rid of the gnome USE flag.  However, the 2007.0 desktop profile doesn't have the hardened USE flag, so if you wanted it enabled you'd have to add hardened to your make.conf.

Short answer: for each flag that's in your profile that you want to disable, add a -myflag to your make.conf.

I hope that isn't too unclear....

---

### Post by Bachstelze on 2007-08-12
To put it a bit more clearly :

For each USE flag, you have a default. If the default is yes and you do not want it, add -useflag. If the default is no and you want it, add useflag. If the default is what you want, add nothing :)

As termitesaid, the defaults are stored in your profile. Do *not* edit it directly, as your changes will be overwritten when you update your portage tree. Use the make.conf to define your USE flags globally (i.e. for all packages) or /etc/portage/package.use to define them locally (i.e. on a per-package basis).

Also, remember that what you put in make.conf, you can override using package.use. For example, if I have a Gnome desktop, I will surely have the gtk USE flag enabled. But now I want to install mplayer, and I want only the console version, not the GTK GUI. I could either edit my make.conf, disable the gtk USE flag, install mplayer and edit my make.conf again to re-enable the gtk USE flag, but that's really too much hassle and it will be even more when the time will come to update my mplayer. So instead, I add

```
media-video/mplayer -gtk
```

to my /etc/portage/package.use and voilà, the gtk USE flag is disabled *only* for mplayer :)

---

### Post by rsambuca on 2007-08-12
Thanks.  This is actually starting to make some sense to me now.  For better or for worse, I ended up putting this into my make.conf file:```
USE="acpi alsa -arts cairo cdr dbus dvd dvdr dvdread eds -emboss encode esd evo fam firefox gif gnome gpm gstreamer gtk hal jpeg -kde kerberos ldap mad mikmod mp3 mpeg ogg opengl oss pdf png -qt3 -qt3support -qt4 quicktime sdl spell svg tiff truetype vorbis win32codecs unicode X xml xv a52 aac aalib adns bonobo exif ffmpeg flac ieee1394 imagemagick java javascript matroska mime mmx mozilla multilib musepack nsplugin scanner sse sse2 theora usb cups x264 xcomposite xinerama xscreensaver xvid"
```

I have compiled the kernel (gentoo-sources), but am stuck on the modules.autoload.d thing.  The gentoo manual says to run "modprobe -l" to see what modules are available, but it doesn't work from the chroot environment.  A little bit each day, I guess!

---

### Post by rsambuca on 2007-08-12
I also noticed when I looked at the make.conf file from my sabayon installation that there were a number of flags that were not listed on the gentoo site.  Are these possibly sabayon specific, or just obscure enough to not matter for most people?

---

### Post by Bachstelze on 2007-08-12
> **rsambuca said:**
> I have compiled the kernel (gentoo-sources), but am stuck on the modules.autoload.d thing.  The gentoo manual says to run "modprobe -l" to see what modules are available, but it doesn't work from the chroot environment.  A little bit each day, I guess!

Another way to list all the installed modules - and one that works in chroot - is

```
find /lib/modules/_kernel version here_/ -name "*.ko"
```

About the "obscure" Sabayon USE flags, could you give a few examples ?

---

### Post by rsambuca on 2007-08-12
Thanks for that command.  I actually found them in a file called modules.dep in that folder.

If the module is a big long name, do I add the whole thing, including the path, or just the last part.  ie.```
/lib/modules/2.6.22-gentoo-r2/kernel/drivers/net/s2io.ko
```Do I add that entire line, or just the s2io.ko part into the modules.autoload.d...?

For the Sabayon use flags, there are a bunch of examples that I couldn't find listed anywhere, such as:  moznocompose moznoirc zeroconf css povray asterisk mbrola ... plus a bunch more.  The use flag list is quite large in sabayon.

cs

---

### Post by termite on 2007-08-12
Put just ```
s2io
``` in the modules.autoload.d/kernel-2.6 files to load the s2io module.

---

### Post by rsambuca on 2007-08-12
Thanks everyone!  i can't wait to see if it boots up!

---

### Post by termite on 2007-08-12
Good luck!

---

### Post by rsambuca on 2007-08-13
Well, kernel seems to work so far, it booted up, anyways!

I have emerged xorg-x11, and am now doing the long gnome compilation now.

---

### Post by rsambuca on 2007-08-14
Thanks for all your help!  I have everything up and running (no programs yet, though!), and am starting to compile some programs now.  I must say, now that I have installed it once (with your help), if I do it again it will actually go quite quickly.

We'll see how system maintenance goes!

---

### Post by termite on 2007-08-15
Enjoy :)

I'm termite on Gentoo Forums as well, by the way.

---

### Post by jaydoc on 2009-01-06
Can Someone help me here...? 

I have been trying to do a chrooted install of gentoo from Arch Linux... Now I am no linux geek, and I have come this far only by standing on the shoulders of giants... all over the WWW!

But I am stuck at the same situation as the OP in the modprobe -l command stage... 

What exactly does that command mean...? 

Also this is my partition table...

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  65.8MB  65.8MB  primary   ext2         boot
 2      65.8MB  20.5GB  20.5GB  primary   ext3         arch root 
 3      20.5GB  46.1GB  25.6GB  primary   ext3       gentoo root
 4      46.1GB  160GB   114GB   extended         
 5      46.1GB  48.2GB  2048MB  logical   linux-swap
 6      48.2GB  160GB   112GB   logical   ext3       arch home

The current GRUB menu is on /dev/sda1, my boot partition. How do I modify the GRUB that gentoo is going to produce, so that I can successfully dual boot...?

Help please..! I am really excited - never thought such things like Virtualization and chrooted installs were true, until I came to see them in action..!

---

### Post by Bachstelze on 2009-01-06
> **jaydoc said:**
> 
But I am stuck at the same situation as the OP in the modprobe -l command stage... 

What exactly does that command mean...?

It lists all the modules that are currently loaded and, as was said earlier, cannot be used in a chroot.

> **jaydoc said:**
> 
The current GRUB menu is on /dev/sda1, my boot partition. How do I modify the GRUB that gentoo is going to produce, so that I can successfully dual boot...?

You have two approaches to choose from:

1. Install a second GRUB on the boot sector of Gentoo's root partition, and chainload it from Arch's GRUb

2. Do not reinstall GRUB at all, and modify the menu of your existing GRUB so you can use it to boot both distros.

I think you should go with 1., it might be a bit more complicated to install, but it will be easier to manage afterwards.

---

### Post by jaydoc on 2009-01-07
> 
find /lib/modules/2.6.27-gentoo-r7/ -type f -iname '*.o' -or -iname '*.ko'

These were the results of the above command. I don't know whether that is the rught command.

> /lib/modules/2.6.27-gentoo-r7/kernel/arch/x86/kernel/test_nx.ko                                   
/lib/modules/2.6.27-gentoo-r7/kernel/drivers/scsi/scsi_wait_scan.ko

How can I choose my modules from this...?

They seem to be ko files, and i don't know what these are.

---

### Post by kk0sse54 on 2009-01-07
> **jaydoc said:**
> These were the results of the above command. I don't know whether that is the rught command.



How can I choose my modules from this...?

They seem to be ko files, and i don't know what these are.

Follow the Gentoo handbook [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=7](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=7) and you'll see you need to edit the kernel-2.6 and add the modules you want
> nano -w /etc/modules.autoload.d/kernel-2.6


---

