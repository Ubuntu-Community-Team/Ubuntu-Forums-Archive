---
title: "kdenlive 0.7 crashes on startup"
date: 2008-11-22
forum: General Help
---

### Post by patmalcolm91 on 2008-11-22
I've installed kdenlive  0.7 from debian-multimedia.org, and on startup it crashes and gives the following backtrace


```
Application: Kdenlive (kdenlive), signal SIGSEGV
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb52566c0 (LWP 1148)]
[KCrash handler]
#6  mlt_properties_fetch (this=0x0, name=0x828af57 "resize")
    at mlt_properties.c:285
#7  0xb7f62a0f in mlt_properties_set_int (this=0x0, name=0x828af57 "resize", 
    value=1) at mlt_properties.c:591
#8  0xb7f45d74 in Mlt::Properties::set () from /usr/local/lib/libmlt++.so.1
#9  0x080d600c in Render::buildConsumer ()
#10 0x080ddf6c in Render::Render ()
#11 0x080d107b in Monitor::Monitor ()
#12 0x080b02a1 in MainWindow::MainWindow ()
#13 0x0809e212 in main ()
#0  0xb7fb1430 in __kernel_vsyscall ()
```

the terminal output (with --nocrashhandler flag) is:

```
kdenlive(1692) MainWindow::parseProfiles: RESULTINGÂ*MLT PATH:  "/usr/share/mlt/profiles/"
kdenlive(1692) initEffects::parseEffectFiles: //  INIT EFFECT SEARCH
kdenlive(1692) Render::Render: //////////  USINGÂ*PROFILE:  hdv_1080_50i
Segmentation fault
```

I've tried using the automated builder, but that doesn't work either (fails during ffmpeg install).

I've also tried installing from everything from svn, but i can't get mlt to compile.

Any help would be greatly appreciated. Thank you.

---

### Post by cariboo on 2008-11-22
If you installed from the Debian repository, you may not get a file that is exactly the same as the one in the Ubuntu repositories. Kdenlive is in the ubuntu repositories and you can use Add/Remove Programs, Synaptic Package Manager, and of course the command line to install it.

Jim

---

### Post by patmalcolm91 on 2008-11-22
The version of Kdenlive in the repos is 0.5. 0.7 is a major rewrite, and I need some of the new features in this release. As some of 0.7's dependencies are not "stable" releases, I imagine that it will be a while before this release appears in the repos. I would like to get this running in the next few weeks as i have a few projects that need finished, so I can't wait.

---

### Post by cignale on 2008-12-14
Try packages i made.

They are built from jaunty/debian-multimedia

[http://blog.linux-fueled.com/2008/12/14/deb-kdenlive-07-per-ubuntu-810-i386-impacchettato-per-voi/](http://blog.linux-fueled.com/2008/12/14/deb-kdenlive-07-per-ubuntu-810-i386-impacchettato-per-voi/)

leave some feedback of course :)

---

