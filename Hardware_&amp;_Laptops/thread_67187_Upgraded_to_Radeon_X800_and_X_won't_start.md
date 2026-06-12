---
title: "Upgraded to Radeon X800 and X won't start"
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by wombat20 on 2005-09-19
Hi,

I've only been using Ubuntu a short while, but would really rather avoid a full reinstall.  Here's my problem.

I recently upgraded my motherboard, CPU and graphics card to the following:
GA-K8NF-9 nforce4-4X  PCI-E
Athlon 64 3000+
ATI Radeon X800 (according to the reconfigure process it's R430 UO)

Also using a ViewSonic VX910 19" LCD DVI - which worked fine with my AGP Radeon 9600 card.  Should I try plugging into my d-sub instead of DVI, would it make any difference?

My WinXP system boots ok (so I can write this), but cuts out intermittently when I turn up the resolution in HL2 or Planetside.

However, X won't start at all, so I end up at the command prompt.  I've tried running: "sudo dpkg-reconfigure xserver-xorg" several times and accepted most of the default options as it looks like it detected the right card.  However I still can't start X.   :-| 

I've managed to download the ATI proprietary driver which I'll try to install, but I'm not sure if I can do so from the command line.

I've included my config and log files, but the main error it gives me is "no screens found".

Any help appreciated.   :smile:

---

### Post by mlomker on 2005-09-19
> : "sudo dpkg-reconfigure xserver-xorg" several times and accepted most of the default options as it looks like it detected the right card.  However I still can't start X.   :-| 


Run it again and select VESA as the driver.  It'll be slow and ugly but it'll work.

> 
I've managed to download the ATI proprietary driver which I'll try to install, but I'm not sure if I can do so from the command line.


[My how-to](http://www.ubuntuforums.org/showthread.php?p=348911) would work fine from the command-line.  Just use the **nano** editor instead of gedit and do the reconfigure instead of using the online fglrxconfig.

You're better off using VESA, though.   :)

---

### Post by wombat20 on 2005-09-20
Thanks mlomker you're a genius!  At least I can now start X and get my emails, etc.

I did the first part of the how-to with the graphical install and it seemed to work and I had fglrx in the modules file (although I seem to remember adding it before when fiddling around anyway).

However, when I run make.sh I get a "FATAL: Module fglrx not found", but carry on and then I get:

"Kernel includes at /usr/src/linux/include not found"

Any idea what's gone wrong here?

Thanks again!   :)

edit:  Hmm, was actually looking at the wrong How-to that I printed out yesterday. I'll use the one you referenced later and see if that works.

---

### Post by mlomker on 2005-09-20
> edit:  Hmm, was actually looking at the wrong How-to that I printed out yesterday. I'll use the one you referenced later and see if that works.

You don't have the kernel headers downloaded.  That's one of the first steps in my how-to.

---

### Post by wombat20 on 2005-09-20
Hehe, RTFM...  I'll try that later.  :)

---

### Post by wombat20 on 2005-09-30
Hmm Followed the HOW-TO you referenced for fglrx.
The first bit (fglrxconfig) didn't have X800 drivers, only older cards, so I carried on with the next bit...
But then...
```

# dpkg -i --force-overwrite fglrx-6-8-0_8.16.20-2_i386.deb
(Reading database ... 120034 files and directories currently installed.)
Unpacking fglrx-6-8-0 (from fglrx-6-8-0_8.16.20-2_i386.deb) ...
dpkg: error processing fglrx-6-8-0_8.16.20-2_i386.deb (--install):
unable to create `./usr/X11R6/lib/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
fglrx-6-8-0_8.16.20-2_i386.deb

```
I found a "FGL.renamed.libGL.so.1.2" which I tried renaming to "libGL.so.1.2", but no luck.  I even tried moving the file away in case it wanted to create a new one.
Any ideas appreicated.  :???:

---

### Post by mlomker on 2005-09-30
> 
I found a "FGL.renamed.libGL.so.1.2" which I tried renaming to "libGL.so.1.2", but no luck.  I even tried moving the file away in case it wanted to create a new one.


Try **apt-get install --reinstall xlibmesa-gl**

It sounds like you damaged that package somehow on previous installation attempts.  After that's back in place you should be able to proceed.

---

### Post by wombat20 on 2005-10-03
Oh dear, must've messed things up properly!  When I do that I'm getting:

```
Unpacking replacement xlibmesa-gl ...
dpkg: error processing /var/cache/apt/archives/xlibmesa-gl_6.8.2-10.1_i386.deb (--unpack):
 unable to create `./usr/X11R6/lib/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xlibmesa-gl_6.8.2-10.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Do I need to create/purge that file or something?   I went to '/usr/X11R6/lib' and created a blank file called libGL.so.1.2 and it didn't like it.  I deleted it and tried again, but no luck.

---

### Post by mlomker on 2005-10-03
> 
 /var/cache/apt/archives/xlibmesa-gl_6.8.2-10.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Try a manual extraction and then copy the file to the right place:

```

su
cd /tmp
cp /var/cache/apt/archives/xlibmesa-gl_6.8.2-10.1_i386.deb .
dpkg -x xlibmesa-gl_6.8.2-10.1_i386.deb .
cp ./usr/X11R6/lib/libGL.so.1 /usr/X11R6/lib/libGL.so.1

```

Hopefully that'll allow you to continue with the installation of the fglrx package.

---

### Post by wombat20 on 2005-10-05
Apparently the file (xlibmesa-gl_6.8.2-10.1_i386.deb) does not exist in the archives at /var/cache/apt/archives/ so I copied it (or the previous version) across from the Ubuntu Install CD (.../pool/x/xorg/*) with all the other .debs in that dir and carried on from there.

Must've been a bad move on my part as OO.org crashed and wouldn't reopen a document, and now I can't even get into Gnome...

... all I can get is a failsafe terminal!!  :confused:

---

### Post by mlomker on 2005-10-05
> all I can get is a failsafe terminal!!  

Then delete the file again, I guess.  I don't know what all is wrong/missing on your machine at this point.  It may be time to start fresh or wait until Breezy is released and then do a fresh reload.

---

### Post by wombat20 on 2005-10-10
OK, my last chance before I have to reinstall from scratch... maybe someone can help me  :confused: 

It seems that my mistake was removing the beligerant package xlibmesa-gl - it wouldn't upgrade or downgrade, so I removed it so I could do a reinstall.

But now it's telling me it can't create a file...

During the install (apt-get and dpkg) I am getting:
```

unable to create: './usr/X11R6/lib/libGL.so.1.2' : No such file or directory.

```

Is that because it shouldn't start with a '.' ?  Normally that would indicate it being relative to the CURRENT directory, wouldn't it?  Is this package just shafted or am I actually DOING SOMETHING WRONG??? :confused: 

As root I can't create a file with nano at './usr/X11R6/lib/libGL.so.1.2' - but I can if I miss off the leading dot.

I've tried backing up my firefox and thunderbird settings so if I have to reinstall completely (what a shit) I won't have wasted quite so many hours!  ](*,)

---

### Post by mlomker on 2005-10-10
> I won't have wasted quite so many hours!

If you have a place to save it to you could [use tar]("http://www.ubuntuforums.org/showpost.php?p=361622&postcount=4") to back up your /home and /etc to save most of your settings.

---

