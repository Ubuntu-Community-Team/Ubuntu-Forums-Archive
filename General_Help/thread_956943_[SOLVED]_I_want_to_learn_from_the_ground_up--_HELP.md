---
title: "[SOLVED] I want to learn from the ground up-- HELP!"
date: 2008-10-23
forum: General Help
---

### Post by bcn17 on 2008-10-23
I have been using ubuntu for almost a year now and have been very happy. However, I continually run into problems that I manage to manufacture myself because I am changing things or testing something etc. A lot of the times my fixes have led me to learn something new. However, I still don't understand what I'm doing if I'm typing ```
make <something>
``` or where packages are installed to- it seems they are everywhere. I was thinking maybe I could sort of "build" my own linux distribution or ubuntu from the ground up so that I would learn how it is pieced together. I don't know any programming. I was considering something like Gentoo- but am not sure if this is actually what I am looking for. If I could start with the linux kernel and start adding stuff in a way that I had to configure some stuff that would be great. Or maybe that sounds completly crazy- I don't know enough to be a good judge- Maybe I need to start with an easier task. Like, the kernel, with x, y, and z. And only add j-t. I just don't know so any ideas would be appreciated!

---

### Post by oldos2er on 2008-10-23
Take a look at [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by MaxIBoy on 2008-10-23
You want to be VERY familiar with compiling first. I'll borrow from one of my other posts:
> **MaxIBoy said:**
> A little bit more of an explanation:
[LIST]
[*]A ".tar.gz" file, otherwise known as a "tarball," is an archive (a ".tar") which has been compressed (a ".gz.") "gz" stands for GNU Zip. You may also see .tar.7z or .tar.bz2 files. 
[*]"cd" means "change directory." It's like clicking on an icon in the folder browser. "cd .." will take you to the parent directory. "cd ~" will take you to your home directory. "cd /" will take you to the root directory (think "my computer" mixed with "c drive.") "cd /whatever" will take you to a folder called "whatever" inside of the root directory. "cd ." will loop back to the current directory.
[*]"./configure" is a program that sets up a few files for "make," and customizes them for your specific computer setup. They're not always needed, but if your tarball comes with one, you should always run it. A different one has to be written for every program. It could be called something else, but it's always called "configure" for the same reason that there's always a file called "README." It's what people expect.
[*]"make clean" gets rid of older versions of the program you might have already compiled so they won't mess with the new version. You don't need to do this if you're installing something for the first time.
[*]"make" takes the code that the programmer wrote (which is basically in a human-readable text file) and translates it into ones and zeroes that the computer will understand.
[*]"make install" takes the newly translated stuff and puts it in the right directory (basically it moves into the program files, which in Linux is the "/usr" directory.)
[/LIST]



I'd suggest trying Arch Linux, then Gentoo, *then* Linux from Scratch.

---

### Post by bcn17 on 2008-10-31
Thanks guys!

---

### Post by loomsen on 2008-10-31
```
"make install" takes the newly translated stuff and puts it in the right directory (basically it moves into the program files, which in Linux is the "/usr" directory.)

```

Actually make install will install to 
/usr/local 
unless anything else was specified as prefix while configuring.

You feel like it just goes everywhere, because it actually can go everywhere. 
For instance, I have a dir ~/bin where I install manually compiled applications to. My icons are placed in ~/.icons and my themes in ~/.themes.

This was you'll have to leave your $HOME only very rarely.
No SUper(ab)using, no corruptions, just good clean fun :)

---

