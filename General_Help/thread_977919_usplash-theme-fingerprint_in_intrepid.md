---
title: "usplash-theme-fingerprint in intrepid"
date: 2008-11-10
forum: General Help
---

### Post by qwertymodo on 2008-11-10
I've been using the fingerprint usplash theme found here [http://u-fingerprint.sourceforge.net/]("http://u-fingerprint.sourceforge.net/") on ubuntu hardy with no problems.  After upgrading to intrepid however, the theme no longer works.  I have completely removed it and reinstalled using the instructions in the readme.  However, nothing displays on startup or shutdown, only the verbose, text-only boot info.  The default ubuntu usplash theme works just fine, so it's not a usplash problem, so it's specific to the theme, so has anyone gotten this successfully working?  I'm using version 0.1 stable for amd64 on intrepid 64-bit.  Thanks

[UPDATE]
I tried running usplash from terminal and it returns the following error
usplash: can't get console font: Invalid argument
usplash: No usable theme found for 1024x768
                                           screen init failed

This is strange because part of the installation instructions for the fingerprint theme explicitly say to set the resolution to 1024x768.  Also strange is that I get this error even when I have the default ubuntu splash screen selected, although that splash works when starting up and shutting down.  Odd...

[UPDATE 2]
After doing some research, I realized that the command vga=791 in the menu.lst meant 1024x768 16-bit (I don't believe the instructions indicated the bit-depth, just the resolution, I had it set at 24-bit).  However, after properly setting that, now my screen hangs at a black screen that says "Starting..."  ...only it never does start :(

anybody know if this problem is with usplash, intrepid, or just the theme itself?

I'm going to try the latest alpha version to see if there's any change.

---

### Post by xantham on 2008-11-11
I'm having a similar issue.  It's driving me mad.  Still investigating...

Regards.

---

### Post by TKMR on 2008-11-17
Same issue here. I've tried all of the installation instructions that the author of the theme provided, and others provided as well, and no luck.

---

### Post by ferda on 2008-11-21
install the startupmanager GUI utility (just for comfort :)): [http://web.telia.com/~u88005282/sum/downloads.html](http://web.telia.com/~u88005282/sum/downloads.html)
set your resolution, 24bit depth and the right *.so file. If it didn't work with downloaded (precompiled) *.so file, you should try downloading current cvs version ```
cvs -d:pserver:anonymous@u-fingerprint.cvs.sourceforge.net:/cvsroot/u-fingerprint co u-fingerprint u-fingerprint
```
and compile&install it:
```
make
make install
```
**warning: this will overwrite your normal ubuntu usplash theme, so that it's good idea to backup it somewhere first, or you can move the created *so file manually - that's all the target "install" does**

You may have to install additional packages: apt-egt install imagemagick usplash-dev

you can try it by sudo usplash -c and CTRL+ALT+F8

After this it should work. I've got still two problems: at 1280x1024 the image isn't quite good-looking and the progressbar shows in wrong place - these problems have to be repaired in the theme.

---

### Post by qwertymodo on 2008-11-23
Also, I noticed on Wikipedia that Linux uses its own VESA codes, or at least it DID.  Apparently the new version of the kernel uses the "normal" standards (or at least some of them are the same, it seems to be random on that point...)  In any case, apparently you need to replace the "vga=791" with "vga=279".  I will try to compile for myself and post my results.

[EDIT]
No good.  If it makes any difference I'm on an HP Pavilion dv2840se notebook.

---

### Post by trendyabinash on 2008-12-08
Here is the updated version which U can NOW load on Intrepid also

and it is working fine
[LINK]http://www.gnome-look.org/content/show.php/USplash+Theme+Fingerprint?content=93826[/LINK]

---

### Post by mcarni on 2009-02-02
sorry for the question, I have a couple of .so usplash themes that I used on Hardy, but I cannot use on Interpid, I seem to understand this is due to something different between usplash version on HH and on II...
I have seen that old themes need to be recompiled, like it has been done for the fingerprint them but I have no idea on how to do it, can anyone shed some light on this?
Thanks

M

---

### Post by Andy06 on 2009-02-02
Use the lastest 0.12 version. Download the .deb package off gnome look. Set the resolution to 1024x768 in start up manager and your good to go.

Simple right? Took me over 2 days of continuous tweaking to get to it:)

Instructions were never complete in one place, the packages I used dint mention resolution, SUM is buggy as it is and stuff off gnome-look is a bit hit and miss. Try and stay away from manual config and menu.1st tweaking as far as possible, I had problems with it.

---

### Post by mcarni on 2009-02-04
Thank you very much Andy06,

I will try to stay away from tweaking things, but sometimes the tentation is too strong....  

thanks

m

---

### Post by adroitster on 2009-09-24
> **trendyabinash said:**
> Here is the updated version which U can NOW load on Intrepid also

and it is working fine
[LINK]http://www.gnome-look.org/content/show.php/USplash+Theme+Fingerprint?content=93826[/LINK]

Thanks for the updated .deb , that saved a lot of time searching for a workaround and doing it yourself. Also now I can again fool my nephew that my screen reads my fingerprints:guitar:

---

