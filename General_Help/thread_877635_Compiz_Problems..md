---
title: "Compiz Problems."
date: 2008-08-02
forum: General Help
---

### Post by sunburstgl on 2008-08-02
I recently tried using this link 
[http://maketecheasier.com/make-your-ubuntu-desktop-rotate-as-a-cylindersphere/2008/07/28](http://maketecheasier.com/make-your-ubuntu-desktop-rotate-as-a-cylindersphere/2008/07/28)
To update compiz so i could use the rotating cylinder. Somewhere in the process I messed up I guess because now I can't open advance desktop settings. That's not even the worst part, I can't switch to other workspaces and I have no window border or menus. I can't figure out how to fix it so could someone pleace help me out?

I'm running gnome mostly stock.

---

### Post by sunburstgl on 2008-08-02
I tried running 'ccsm' from the command line and got the following error

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: /usr/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsEdgesToStringList

---

### Post by NickZA on 2008-08-02
Hi,


I'm also having those problems, no cube, no window controls, nothing. I use ```
metacity --replace
``` to get back to normal, but when I try ```
compiz --replace
``` it outputs the following:
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:0d.0 0300: 10de:03d1 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: no 'core' plugin with ABI version '20080424' loaded

/usr/bin/compiz.real (ccp) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'
```

Thing is, that (probably like the n00b I am) I installed the new compiz (see [http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/](http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/)), it messed up somewhat, and I then uninstalled everything from my 8.04 install that related to compiz to remove Compiz 0.7.6. I then reloaded all 0.7.4 Compiz stuff in Synaptic. And now I have the above problems.

---

### Post by overdrank on 2008-08-02
moved to Desktop Effects & Customization :)

---

### Post by sunburstgl on 2008-08-02
I get pretty much the exact same thing there. At least with the 'metacity --replace' I can get back to looking normalish. But when I try 'compiz --replace' I get the same error message

---

### Post by sunburstgl on 2008-08-02
I fixed it on my computer. What I did was I went into synaptic package manager and searched for 'compiz'. One by one I checked the version of each installed package (highlight and press Ctrl+E). I also downgraded a few of them and now compiz seems to work. I can't remember exactly which packages I had to change, but try going through and making sure you have the same versions selected for each package. If you don't, make sure you are selecting the same versions and then initiate a force.

---

### Post by cdtech on 2008-08-02
Try this thread, it may help you out.

[http://ubuntuforums.org/showthread.php?t=799070&highlight=compiz-check](http://ubuntuforums.org/showthread.php?t=799070&highlight=compiz-check)

A script to see what could be the problem with your hardware and video.

Hope this helps.....

---

### Post by sdowney717 on 2008-08-02
[http://ubuntuforums.org/showthread.php?t=781218&highlight=compiz](http://ubuntuforums.org/showthread.php?t=781218&highlight=compiz)

This is what I followed to get the latest and greatest compiz. I have the cylinder working.

---

### Post by NickZA on 2008-08-02
I also got it fixed, but what I did was to simply use the Add/Remove package manager rather than the standard one found under System->Administration. I had also tried the removal of all the wrongly-versioned packages in standard Synaptic, but no luck. However, as soon as I installed Compiz as a program from Add/Remove, things went back to working again.

---

