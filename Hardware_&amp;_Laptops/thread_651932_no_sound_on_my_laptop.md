---
title: "no sound on my laptop"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by bo-bobo on 2007-12-28
Hi all.

My laptop doesn't play any sound, so I've downloaded drivers for my soundcard and I've tried to install it, but the lasts lines said that:

configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.
Remove Folder.....
./install: 100: alsaconf: not found 

I read in some forums, and I also dowloaded from alsa-proyect.org the following packages: alsa-utils, alsa-drivers and alsa-lib. I have installed the lib and drivers. When I try to compile alsa-utils, it says the following:

configure: error: this packages requires a curses library. 

But the library is already installed.

I read the Install notes, and I've found this:

If ./configure command complain that alsa-lib package isn't installed,
please, check if --prefix option is same for alsa-lib and alsa-utils
package. The configure script from alsa-utils package probably cannot find
header file asoundlib.h in $prefix/include/alsa directory (usually in
/usr/include/alsa directory). 

I'm new in Linux and I don't know what means that, so I don't know what I have to do.

Could anybody explain me what have I to do, or another solution? (I use ubuntu 7.10)

Thanks.

---

### Post by icheyne on 2007-12-28
It sounds like you are diving in to the command line and compiling new drivers too quickly. You should have those ALSA packages already. There are some great troubleshooting guides here:
[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)
[http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60)

---

### Post by Yellow Pasque on 2007-12-28
First, do you have basic software building packages like build-essential installed?

When you run into an error complaining that you're missing a package, it's very useful to plug the name into a search on [http://packages.ubuntu.com/](http://packages.ubuntu.com/)  So search for curses in the package name and make sure you have all the basic curses/ncurses library packages installed INCLUDING the developer's (-dev) packages. So, for example, you need to makes sure you have libncurses5-dev & lib32ncurses5-dev as well as the reguler lib packages. Understand?

> If ./configure command complain that alsa-lib package isn't installed,
please, check if --prefix option is same for alsa-lib and alsa-utils
package. The configure script from alsa-utils package probably cannot find
header file asoundlib.h in $prefix/include/alsa directory (usually in
/usr/include/alsa directory).

It means you should use the --prefix=/usr option when you ./configure those two packages.

And yes, if you can't get ALSA built/working, try OSSv4 as icheyne and my signature link to.

---

### Post by Rhyok on 2007-12-31
Let me guess: You have the Realtek HD sound card don't you?
I'm having the same problem, curses and all. 
I just installed build-essential (which I thought would fix it) and I think I installed an ncurses package as well. 
Is there a convenient way to get all the ncurses/curses packages in one go?
EDIT:
Wait, scratch that. I downloaded one of the older curses packages (4 I believe) and some of the related dev packages and it appears to have worked.
EDIT 2:
Nope, I lied. Still borked. I followed the CAG too and used the correct drivers for ALSA (intel8x0) but it doesn't show up at all in my Sounds preferences and doesn't show up when I use the modplug command either. Please help! Going to give OSS a try though, it appears to support this soundcard.

---

### Post by Rhyok on 2007-12-31
Alright! OSS works! The only thing is that the volume applet patch does not. I would really like to use that thing but any workaround is fine at this point.

---

