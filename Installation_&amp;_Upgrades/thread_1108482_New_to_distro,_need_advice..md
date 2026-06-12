---
title: "New to distro, need advice."
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2009-03-27
Hi all.

I've been using Gentoo for the past several years.  I managed to get myself into a bit of library hell and decided I was spending too much time on a source-based distro to justify using it at work.

I came here because this is supposed to be the most trouble-free distro.  I need it to just work, but I also have some requirements.  I don't mind reading the manual, but I need to know where the latest copy of the manual is.  Technology has changed dramatically since I last did an install.

I need to do an install, and I don't have a way to hook up another PC in this location, so once I start I will be disconnected until back up again.

I have an older machine, a P4 with 40g drive and 1.2g RAM.  Here are my funky requirements:
[LIST=1]
[*]Must be desktop environment.  Don't know if KDE or Gnome is currently better, suspect it's 50/50.
[*]I intend to use an LVM for growable partitions.  I would like to boot from the logical partition, although a boot loader in ext2 or similar would be fine.
[*]I need to have files which are >4g, which means no EXT filesystems as far as I know.  I would also have the typical bunch of small files, so I would like to avoid a penalty for that.
[/LIST]

I have a typical battery backup, but nothing special.  This is not a server, in fact it's a developer machine and I will be running mysql and a web server on it, among other things.  This is actually what caused me to post here.  Most filesystems which accept large files want to be on a server last time I looked into it.  I don't want to lose all my data if I crash the system.

It would be workable to have a separate filesystem for most of the large files, but if I can I would like to avoid that.

Thanks.

---

### Post by kidux on 2009-03-27
> **1clue said:**
> Hi all.

I've been using Gentoo for the past several years.  I managed to get myself into a bit of library hell and decided I was spending too much time on a source-based distro to justify using it at work.

I came here because this is supposed to be the most trouble-free distro.  I need it to just work, but I also have some requirements.  I don't mind reading the manual, but I need to know where the latest copy of the manual is.  Technology has changed dramatically since I last did an install.

I need to do an install, and I don't have a way to hook up another PC in this location, so once I start I will be disconnected until back up again.

I have an older machine, a P4 with 40g drive and 1.2g RAM.  Here are my funky requirements:
[LIST=1]
[*]Must be desktop environment.  Don't know if KDE or Gnome is currently better, suspect it's 50/50.
[*]I intend to use an LVM for growable partitions.  I would like to boot from the logical partition, although a boot loader in ext2 or similar would be fine.
[*]I need to have files which are >4g, which means no EXT filesystems as far as I know.  I would also have the typical bunch of small files, so I would like to avoid a penalty for that.
[/LIST]

I have a typical battery backup, but nothing special.  This is not a server, in fact it's a developer machine and I will be running mysql and a web server on it, among other things.  This is actually what caused me to post here.  Most filesystems which accept large files want to be on a server last time I looked into it.  I don't want to lose all my data if I crash the system.

It would be workable to have a separate filesystem for most of the large files, but if I can I would like to avoid that.

Thanks.
1. Try XFCE, or Xubuntu as it is. Lightweight DE and still powerful enough to look pretty. Or you can eschew the DE altogether and go with a WM like openbox.

2. Not sure about this.

3. JFS might work for you. Check that out. I'm not sure of the file sizes, but it worked flawlessly for me.

---

### Post by upchucky on 2009-03-27
any ubuntu has the manual accessible in help on the title bar of the desktop

it is possible to set up a separate partition for home, this ensures that your files are kept separate from the core install and can be backed up saved in the unlikely even that a re-install is done. 

a typical ubuntu takes 10g for core, 500m for swap, and rest of drive for the home partition which is where all non system files go.

---

### Post by sam1948 on 2009-03-27
i'm using ubuntu 8.10
on an IBM T30 : 2Ghz processor, 512 Mb memory, 16 Mb radeon ati card 

it works perfect 
about file systems u should check the benefits of each type and just use it
ext3, fat, fat8,16,32,  ntfs , ...
for each file sizes
the root dir though must be ext3 or ext2

the computer can run the graphic effects but
i disabled them and the computer runs faster (i think..)

---

### Post by 1clue on 2009-03-29
I have been using Xfce as my primary WM for about 3 years.

Many of the tools I use seem to want either Gnome or KDE libraries.  I have been opting for the Gnome stuff, simply because of size.  I don't really need a full desktop environment, but I don't feel the need to fight the trend either.  Been there, done that and got the T-shirt.

Video speed is not so big a problem for me.  I'm mostly looking at text, some graphics but it is generally not animated unless it's youtube or some news service, or a WebEx.  I don't play games, don't sit there watching video all day, this is a programming work box not an entertainment center.  My iPod hooks up to the speakers directly with no intervening computer.  I need to HAVE video playback, but I don't live there.

What would be nice is to have my tilt-screen work in tilt fashion.  I have a Princeton SENergy 981 driven by a Radeon 7500.  Yes I know that's old, but it's what's there.

I was thinking to go with one of the main desktop environments in order to keep things as consistent as possible to a single environment this time.  I have no real preference, other than maybe to give Gnome another try to see if it got any more stable.

In other words, my Gentoo experience was maybe a bit too much immersion.  At home (when I have lots of time on my hands and way too much curiosity) Gentoo is great, because you can compile in the options you want in every package.  Tinkering with black box or Xfce is fun too.  I have hundreds or thousands of hours in each.

The control you get with Gentoo is great, but for this box I need extremely low maintenance and I need to let somebody else decide what works with what.  I've found that with this box, I have been ignoring much of the updates in favor of less maintenance time.  I don't like that.  I need a current stable box with the stable security fixes on it.

---

