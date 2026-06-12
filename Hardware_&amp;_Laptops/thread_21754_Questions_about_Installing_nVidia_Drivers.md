---
title: "Questions about Installing nVidia Drivers"
date: 2005-03-23
forum: Hardware &amp; Laptops
---

### Post by audax321 on 2005-03-23
Hello,

   I have a GeForce 6600GT that I'm trying to install the 7167 drivers (from nVidia)  and I have two questions regarding this:

1. To install the kernel-source package I installed the linux-source package and then did the following:

#cd /usr/src
#tar xjvf blah_blah.tar.bz2
#ln -s blah_blah linux

Is this right?

2. I need to get into init 3 (text mode with no X) in order to install the drivers, but I can't. I tried doing sudo init 3 and I tried editing a line in /etc/inittab from 

            id:2:initdefault:
            to
            id:3:initdefault:

But that didn't work either. Any idea how to do this.

Also if anyone else tried installing these drivers on Ubuntu (I'm using Warty) and ran into any problems, let me know.

Thanks.

---

### Post by wylfing on 2005-03-23
Don't follow the directions provided by nVidia. The post I've linked below gives good advice on installing the nVidia drivers by compiling a custom kernel, and although it says it's for hoary it looks to me like it would work fine for warty as well.

[http://www.ubuntuforums.org/showpost.php?p=100460&postcount=1](http://www.ubuntuforums.org/showpost.php?p=100460&postcount=1)

---

### Post by audax321 on 2005-03-23
That how-to seems to only want you to do that if you have the ubuntu nvidia drivers (v6111) installed (because the nVidia drivers mess up the config) and if you want the driver managed by apt. I'd rather manage the video card driver myself, so is it still okay to install them using nVidia's directions. I like to keep my drivers up to date and I like having the control that nVidia's installer provides. I'd rather not depend on packages to install up to date drivers for my video card and I really don't mind having to compile new drivers when my kernel changes. I've done so on SuSE for years.

The only real problem I am having as far as the driver install goes is getting into init 3 and installing the sources correctly... I think I did that correctly above, but not sure because ubuntu calls its sources linux-source and most other distros call their packages kernel-source.

---

### Post by audax321 on 2005-03-24
Okay, got it to work.

The sources were installed fine, but just had to move over a config file and run make on them. Then to get the driver installed, I just told XF86Config to load up the nv driver (which I knew wouldn't work)... so X crashed and gave me a console. Then I installed the nVidia drivers, editing the X config, and it works. :)

Debian based distros definitely needs to include a way to get into init 3 (text mode with no X). From what I've read, they completely start on init 2, which I think is kind of retarded because you end up losing the functionality that the text console provides.

If it helps anyone else, info on installing the kernel sources/driver in Debian is here: [DEBAIN "Nvidia Driver installation "](http://www.highend2d.com/boards/showflat.php?Cat=&Board=linuxforum&Number=200542&page=0&view=collapsed&sb=5&o=&fpart=) 

For Ubuntu its the same thing, just make sure to install the linux-source package instead of kernel-source.

 8)

---

### Post by mercurus on 2005-03-26
Easiest way I've found to do this ... I also have an nVidia chip with up to date drivers :)

0. Logout of your working desktop (save session if need be)
1. Ctrl-Alt-F1 (to switch to a tty terminal)
2. Login as normal user
3. sudo /etc/init.d/gdm stop (stops the GNOME display manager and kills X)
4. make the necessary config changes, install kernel modules etc
5. /etc/init.d/gdm restart (restarts GDM and X, if there are any problems it shows you the relevant portions of the logfiles, and you get dumped at the commandline again - until the config loads fine)
6. Repeat as necessary :)

Cheers
mercurus

---

