---
title: "[SOLVED] cairo problem"
date: 2008-10-16
forum: General Help
---

### Post by christophermluna on 2008-10-16
Hey there,

I have installed Cairo as per the instructions here [http://ubuntuforums.org/showthread.php?t=878603](http://ubuntuforums.org/showthread.php?t=878603)

Now, Cairo Dock shows up as expected in Applications > System Tools, but when I click on it nothing happens.

I'm wondering if anyone knows why this might be?

---

### Post by Atsuko on 2008-10-16
Start a terminal and start the dock from that and see what the errors are and why it is not starting.

---

### Post by christophermluna on 2008-10-16
Thanks.  I am still getting used to Ubuntu, and I realized shortly that when something doesn't work you should try to run it in terminal.

Here's the error:

```

cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory
```

Now, I'm going to go out on a limb and say that I con probably answer this question myself.  I need the specified library.

I guess, being somewhat new to Ubuntu, I don't know if I should just go out and try to find this library (as I am not entirely sure what a library is, though I have an idea), or whether it should be on my system already.  A Google search indicates that this library is for OpenGL, which I thought I would already have on my system, given that I've got Compiz Fusion running smoothly.

I will do a forum search and see if I can solve this on my own, but thanks for the pointer that I can find out why a program doesn't run by trying to run it in the terminal!  I have to get into a Linux mindset again.

---

### Post by christophermluna on 2008-10-16
Okay.  After searching the forums, I found people with a similar problem on this thread:

[http://ubuntuforums.org/showthread.php?t=613087](http://ubuntuforums.org/showthread.php?t=613087)

I followed the instructions, getting getlibs, etc., then getting the libraries that the error report claims are missing.  But still no dice on getting cairo-dock to run, and I get the same error message:

```
luna@ubuntu:~$ sudo getlibs -l libglitz.so.1
libglitz.so.1: libglitz1
The following i386 packages will be installed:
libglitz1
Continue [Y/n]? y
Downloading ...
Installing libraries ...
luna@ubuntu:~$ cairo-dock
cairo-dock: error while loading shared libraries: libglitz-glx.so.1: cannot open shared object file: No such file or directory
```

I do apologize if I'm making a terrible newbie error, here, and again thanks for taking the time to read and help.

---

### Post by fabounet on 2008-10-17
there is libglitz and libglitz-glx (so 2 packages)
you did the first one, you have to do the other too ;-)

---

### Post by christophermluna on 2008-10-17
Aha!  Well, next time I'll pay more attention to the fine print.

Thanks for helping out, everyone.  I got that library and one more, and now Cairo Dock is running beautifully.

Thanks again!

---

### Post by Atsuko on 2008-10-17
Sorry didn't get back to help you, i was gone  and just got back now.

---

### Post by ruipalmeira on 2008-10-17
he could also saved the trouble just by installing .debs of cairodock... it downloads dependencies automatically

---

### Post by nIsmoAddict on 2008-10-21
Hi I'm experiencing the same problem as op described but even with all the instruction posted I still can't get my cairo-dock to open even when I Applications > System ToolsApplications > System Tools and click on it.  I look at my system monitor and it says the application is running and in sleep mode please help.

this is the code i get when i try to run the program in terminal

edit: ps. It was working fine in the beginning and when I tried to switch theme to the translucent one that's when it bugged out and stopped working and I installed the program through the repository method and I've reinstalled it many times since then and I'm finally lost and again please help.

Many thanks in advance

```
john@john-laptop:~$ cairo-dock
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:263)  
  while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:123)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:123)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:123)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:123)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
 friend : File Browser (16778852)
window pixmap : 800x550
window pixmap : 800x550
new backing pixmap (bis) : 60817420
window pixmap : 800x550
window pixmap : 800x550
 friend : Pidgin Internet Messenger (35651670)
window pixmap : 340x390
window pixmap : 340x390
window pixmap : 1280x728
window pixmap : 1280x728

```

---

### Post by loomsen on 2008-10-21
If you're using amd64 you can download them here:

[http://ubuntuforums.org/showthread.php?t=954474](http://ubuntuforums.org/showthread.php?t=954474)

I compiled them yesterday with all options enabled.

---

### Post by nIsmoAddict on 2008-10-22
I tried loading the Deb files you've posted but it says error wrong architecture amd64' does this mean I'm not running amd 64?  I know this is a very noob question.

---

### Post by loomsen on 2008-10-22
Yup, I think it does :)

Do you have a single core CPU then? Otherwise you might want to consider upgrading to 64bit when Intrepid launches in a couple of days. 

You shouldnt run an upgrade earlier tho, as it will most likely break your dependencies.

---

### Post by nIsmoAddict on 2008-10-22
Thanks again for taking your time for to answer my questions.
I'm currently running a dual core xp2 amd64 and I used the Wubi installer so I was never exactly sure whether or not it was installed in the 64bit version or the 32bit.  I've read around and was told that wubi would just installed whatever was optimal to your computer so I'd just assumed that it would have been 64bit version.  I guess I'll just wait for the new version and do a fresh install then.  But this problem is still a thorn in my backside

---

