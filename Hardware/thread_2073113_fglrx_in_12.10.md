---
title: "fglrx in 12.10"
date: 2012-10-19
forum: Hardware
---

### Post by novafluxx on 2012-10-19
I ran lshw after getting a notice that I was running in software rendering mode, which isn't a surprise to me. I went to software sources and activated fglrx. I applied it and restarted. Logging in was no problem, LightDM seemed to work just fine.

After logging in I was presented with a blank desktop, nothing but the background loaded. I was able to access the context menu via right click, and able to access settings from there and change back to the open source driver, so I'm back to 'normal' now.

Before I did that I ran lshw to get some info:

```

*-display UNCLAIMED
       description: VGA compatible controller
       product: PITCAIRN PRO [Radeon HD 7800 Series]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff memory:f7e00000-f7e3ffff ioport:e000(size=256) memory:f7e40000-f7e5ffff
```

Configuration shows nothing for a driver!

When I run this using the radeon driver it shows the radeon driver there like this:
```

  *-display
       description: VGA compatible controller
       product: PITCAIRN PRO [Radeon HD 7800 Series]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:45 memory:e0000000-efffffff memory:f7e00000-f7e3ffff ioport:e000(size=256) memory:f7e40000-f7e5ffff

```

Anyone know what I can do to get this working? Unity does not run very well at all, in my experience, using software rendering via llvmpipe.

Thanks!

Edit:

I've discovered that the fglrx version ins 12.10 is 12.8, which doesn't work with this version of X or the kernel, not entirely sure. Does anyone know if the repo's will be updated when 12.9 is released by AMD or will I need to get the driver manually?

---

### Post by mwolfe on 2012-10-19
I'm having this same problem. I installed fglrx-updates after doing a clean install. I tried using regular fglrx as well with a different install and no luck. I

[rant]It seems radeon graphics cards  are really a lost cause in linux.. You either get a crappy proprietary driver or an open source driver that is inefficient and runs the fans full speed (and yes, I know how to slow the fans down but that causes poor performance). Also, with the open source driver, unity search was really slow after just a little while of using the system.. In fact it was so slow it was barely usable. Restarting compiz fixes the issue but it's a pain to do all the time. These are the same issues that plauged 12.04 and it looks like no progress was made in that department! [/rant]

---

### Post by novafluxx on 2012-10-19
> **mwolfe said:**
> I'm having this same problem. I installed fglrx-updates after doing a clean install. I tried using regular fglrx as well with a different install and no luck. I

[rant]It seems radeon graphics cards  are really a lost cause in linux.. You either get a crappy proprietary driver or an open source driver that is inefficient and runs the fans full speed (and yes, I know how to slow the fans down but that causes poor performance). Also, with the open source driver, unity search was really slow after just a little while of using the system.. In fact it was so slow it was barely usable. Restarting compiz fixes the issue but it's a pain to do all the time. These are the same issues that plauged 12.04 and it looks like no progress was made in that department! [/rant]

A pitty I enjoy using Windows and playing games on Steam, or I'd stick with my CPU's Intel HD 4000 graphics. I bet that would run Unity like a charm on the open source driver.

Here's hoping 12.9 works out for us! It'll hopefully be released soon!

---

### Post by mwolfe on 2012-10-19
So according to this thread, the fix is to do the following:


```
sudo apt-get install linux-headers-generic
```

What ended up working for me was installing that and fglrx-updates

Finally ubuntu works! I despise booting windows!

BTW, I put a small blog about this on my site to help others find this information when googling: [http://wolfewebservices.com/blog/how-get-amd-drivers-catalyst-fglrx-working-ubuntu-1210](http://wolfewebservices.com/blog/how-get-amd-drivers-catalyst-fglrx-working-ubuntu-1210)

---

### Post by novafluxx on 2012-10-19
> **mwolfe said:**
> So according to this thread, the fix is to do the following:


```
sudo apt-get install linux-headers-generic
```

What ended up working for me was installing that and fglrx-updates

Finally ubuntu work; I despise booting windows!

BTW, I put a small blog about this on my site to help others find this information when googling: [http://wolfewebservices.com/blog/how-get-amd-drivers-catalyst-fglrx-working-ubuntu-1210](http://wolfewebservices.com/blog/how-get-amd-drivers-catalyst-fglrx-working-ubuntu-1210)

yes I saw that too and I will try it when I get home

Just got home and installed linux-headers-generic

fglrx now loading properly and being used for video!

Woohoo!

---

### Post by kwanylongy on 2012-10-21
I tried that, it returns the below error. Any thoughts?

carlos@asurada:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libcdt4 libgraph4 libgvc5 libpathplan4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
19 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up dictionaries-common (1.12.10) ...
Install dictionaries-common for xemacs21
install/dictionaries-common: Byte-compiling for emacsen flavour xemacs21

WARNING:
Couldn't find obvious defaults for:
data-directory
mule-lisp-directory
lisp-directory
Perhaps some directories don't exist, or the XEmacs executable,
/usr/bin/xemacs21
is in a strange place?Symbol's function definition is void: batch-byte-compile
xemacs exiting
.
ERROR: install script from dictionaries-common package failed
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of aspell:
 aspell depends on dictionaries-common (>> 0.40); however:
  Package dictionaries-common is not configured yet.

dpkg: error processing aspell (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of aspell-en:
 aspell-en depends on aspell (>= 0.60.3-2); however:
  Package aspell is not configured yet.
 aspell-en depends on dictionaries-common (>= 0.49.2); however:
  Package dictionaries-common is not configured yet.

dpkg: error processing aspell-en (--configure):
 dependency problems - leaving unconfigured
Setting up emacsen-common (2.0.3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Install emacsen-common for xemacs21
emacsen-common: Handling install of emacsen flavor xemacs21

WARNING:
Couldn't find obvious defaults for:
data-directory
mule-lisp-directory
lisp-directory
Perhaps some directories don't exist, or the XEmacs executable,
/usr/bin/xemacs21
is in a strange place?Loading /usr/share/emacs/site-lisp/debian-startup...
Loading 00debian...
Error while loading 00debian: Symbol's function definition is void: loop
Loading 00debian-vars...
Loading 50a2ps...
Loading 50autoconf...
Error while loading 50autoconf: No /usr/local/ prefixed paths in load-path
Loading 50dictionaries-common...
Error while loading 50dictionaries-common: No /usr/local/ prefixed paths in load-path
Loading 50emacs-goodies-el...
Package emacs-goodies-el not fully installed.  Skipping setup.
Loading 50ess...
Package ess not fully installed.  Skipping setup.
Loading 50pspp...
Symbol's function definition is void: batch-byte-compile
xemacs exiting
.
ERROR: install script from emacsen-common package failed
dpkg: error processing emacsen-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of emacs23-common:
 emacs23-common depends on emacsen-common (>= 1.4.10); however:
  Package emacsen-common is not configured yet.

dpkg: error processing emacs23-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs23-bin-common:
 emacs23-bin-common depends on emacs23-common (= 23.4+1-4ubuntu1); however:
  Package emacs23-common is not configured yet.

dpkg: error processing emacs23-bin-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of emacs23:
 emacs23 depends on emacs23-bin-common (= 23.4+1-4ubuntu1); however:
  Package emacs23-bin-common is not configured yet.

dpkg: error processing emacs23 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs:
No apport report written because MaxReports is reached already
                                                               emacs depends on emacs23 | emacs23-lucid | emacs23-nox; however:
  Package emacs23 is not configured yet.
  Package emacs23-lucid is not installed.
  Package emacs23-nox is not installed.

dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-mule:
 xemacs21-mule depends on emacsen-common; however:
  Package emacsen-common is not configured yet.

dpkg: error processing xemacs21-mule (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21:
 xemacs21 depends on xemacs21-mule (>= 21.4.22-3.2ubuntu2) | xemacs21-mule-canna-wnn (>= 21.4.22-3.2ubuntu2) | xemacs21-nomule (>= 21.4.22-3.2ubuntu2); however:
  Package xemacs21-mule is not configured yet.
  Package xemacs21-mule-canna-wnn is not installed.
  Package xemacs21-nomule is not installed.

dpkg: error processing xemacs21 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-support:
 xemacs21-support depends on emacsen-common; however:
  Package emacsen-common is not configured yet.
 xemacs21-support depends on xemacs21 (= 21.4.22-3.2ubuntu2); however:
  Package xemacs21 is not configured yet.

dpkg: error processing xemacs21-support (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of emacs-goodies-el:
 emacs-goodies-el depends on emacs23 | emacsen; however:
  Package emacs23 is not configured yet.
  Package emacsen is not installed.
  Package xemacs21-mule which provides emacsen is not configured yet.
  Package emacs23 which provides emacsen is not configured yet.

dpkg: error processing emacs-goodies-el (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ess:
 ess depends on emacs23 | emacs22 | emacs21 | emacsen; however:
  Package emacs23 is not configured yet.
  Package emacs22 is not installed.
  Package emacs21 is not installed.
  Package emacsen is not installed.
  Package xemacs21-mule which provides emacsen is not configured yet.
  Package emacs23 which provides emacsen is not configured yet.

dpkg: error processing ess (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of hyphen-en-us:
 hyphen-en-us depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.

dpkg: error processing hyphen-en-us (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ispell:
 ispell depends on dictionaries-common; however:
  Package dictionaries-common is not configured yet.

dpkg: error processing ispell (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ienglish-common:
 ienglish-common depends on dictionaries-common (>= 1.10.6~); however:
  Package dictionaries-common is not configured yet.
 ienglish-common depends on ispell (>= 3.3.02); however:
  Package ispell is not configured yet.

dpkg: error processing ienglish-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of iamerican:
 iamerican depends on dictionaries-common; however:
  Package dictionaries-common is not configured yet.
 iamerican depends on ienglish-common (= 3.3.02-5build1); however:
  Package ienglish-common is not configured yet.
 iamerican depends on ispell; however:
  Package ispell is not configured yet.

dpkg: error processing iamerican (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up pspp (0.7.9+git20120620-1) ...
Install pspp for emacs
Install pspp for xemacs21
install/pspp: Handling install for emacsen flavor xemacs21

WARNING:
Couldn't find obvious defaults for:
data-directory
mule-lisp-directory
lisp-directory
Perhaps some directories don't exist, or the XEmacs executable,
/usr/bin/xemacs21
is in a strange place?Loading /usr/share/emacs/site-lisp/debian-startup...
Loading 00debian...
Error while loading 00debian: Symbol's function definition is void: loop
Loading 00debian-vars...
Loading 50a2ps...
Loading 50autoconf...
Error while loading 50autoconf: No /usr/local/ prefixed paths in load-path
Loading 50dictionaries-common...
Error while loading 50dictionaries-common: No /usr/local/ prefixed paths in load-path
Loading 50emacs-goodies-el...
Package emacs-goodies-el not fully installed.  Skipping setup.
Loading 50ess...
Package ess not fully installed.  Skipping setup.
Loading 50pspp...
Symbol's function definition is void: batch-byte-compile
xemacs exiting
.
ERROR: install script from pspp package failed
dpkg: error processing pspp (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-bin:
 xemacs21-bin depends on xemacs21-support (= 21.4.22-3.2ubuntu2); however:
  Package xemacs21-support is not configured yet.

dpkg: error processing xemacs21-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 dictionaries-common
 aspell
 aspell-en
 emacsen-common
 emacs23-common
 emacs23-bin-common
 emacs23
 emacs
 xemacs21-mule
 xemacs21
 xemacs21-support
 emacs-goodies-el
 ess
 hyphen-en-us
 ispell
 ienglish-common
 iamerican
 pspp
 xemacs21-bin

---

### Post by novafluxx on 2012-10-21
> **kwanylongy said:**
> I tried that, it returns the below error. Any thoughts?

```

carlos@asurada:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libcdt4 libgraph4 libgvc5 libpathplan4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
19 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up dictionaries-common (1.12.10) ...
Install dictionaries-common for xemacs21
install/dictionaries-common: Byte-compiling for emacsen flavour xemacs21

WARNING:
Couldn't find obvious defaults for:
data-directory
mule-lisp-directory
lisp-directory
Perhaps some directories don't exist, or the XEmacs executable,
/usr/bin/xemacs21
is in a strange place?Symbol's function definition is void: batch-byte-compile
xemacs exiting
.
ERROR: install script from dictionaries-common package failed
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of aspell:
 aspell depends on dictionaries-common (>> 0.40); however:
  Package dictionaries-common is not configured yet.

dpkg: error processing aspell (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of aspell-en:
 aspell-en depends on aspell (>= 0.60.3-2); however:
  Package aspell is not configured yet.
 aspell-en depends on dictionaries-common (>= 0.49.2); however:
  Package dictionaries-common is not configured yet.

dpkg: error processing aspell-en (--configure):
 dependency problems - leaving unconfigured
Setting up emacsen-common (2.0.3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Install emacsen-common for xemacs21
emacsen-common: Handling install of emacsen flavor xemacs21

WARNING:
Couldn't find obvious defaults for:
data-directory
mule-lisp-directory
lisp-directory
Perhaps some directories don't exist, or the XEmacs executable,
/usr/bin/xemacs21
is in a strange place?Loading /usr/share/emacs/site-lisp/debian-startup...
Loading 00debian...
Error while loading 00debian: Symbol's function definition is void: loop
Loading 00debian-vars...
Loading 50a2ps...
Loading 50autoconf...
Error while loading 50autoconf: No /usr/local/ prefixed paths in load-path
Loading 50dictionaries-common...
Error while loading 50dictionaries-common: No /usr/local/ prefixed paths in load-path
Loading 50emacs-goodies-el...
Package emacs-goodies-el not fully installed.  Skipping setup.
Loading 50ess...
Package ess not fully installed.  Skipping setup.
Loading 50pspp...
Symbol's function definition is void: batch-byte-compile
xemacs exiting
.
ERROR: install script from emacsen-common package failed
dpkg: error processing emacsen-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of emacs23-common:
 emacs23-common depends on emacsen-common (>= 1.4.10); however:
  Package emacsen-common is not configured yet.

dpkg: error processing emacs23-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs23-bin-common:
 emacs23-bin-common depends on emacs23-common (= 23.4+1-4ubuntu1); however:
  Package emacs23-common is not configured yet.

dpkg: error processing emacs23-bin-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of emacs23:
 emacs23 depends on emacs23-bin-common (= 23.4+1-4ubuntu1); however:
  Package emacs23-bin-common is not configured yet.

dpkg: error processing emacs23 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs:
No apport report written because MaxReports is reached already
                                                               emacs depends on emacs23 | emacs23-lucid | emacs23-nox; however:
  Package emacs23 is not configured yet.
  Package emacs23-lucid is not installed.
  Package emacs23-nox is not installed.

dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-mule:
 xemacs21-mule depends on emacsen-common; however:
  Package emacsen-common is not configured yet.

dpkg: error processing xemacs21-mule (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21:
 xemacs21 depends on xemacs21-mule (>= 21.4.22-3.2ubuntu2) | xemacs21-mule-canna-wnn (>= 21.4.22-3.2ubuntu2) | xemacs21-nomule (>= 21.4.22-3.2ubuntu2); however:
  Package xemacs21-mule is not configured yet.
  Package xemacs21-mule-canna-wnn is not installed.
  Package xemacs21-nomule is not installed.

dpkg: error processing xemacs21 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-support:
 xemacs21-support depends on emacsen-common; however:
  Package emacsen-common is not configured yet.
 xemacs21-support depends on xemacs21 (= 21.4.22-3.2ubuntu2); however:
  Package xemacs21 is not configured yet.

dpkg: error processing xemacs21-support (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of emacs-goodies-el:
 emacs-goodies-el depends on emacs23 | emacsen; however:
  Package emacs23 is not configured yet.
  Package emacsen is not installed.
  Package xemacs21-mule which provides emacsen is not configured yet.
  Package emacs23 which provides emacsen is not configured yet.

dpkg: error processing emacs-goodies-el (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ess:
 ess depends on emacs23 | emacs22 | emacs21 | emacsen; however:
  Package emacs23 is not configured yet.
  Package emacs22 is not installed.
  Package emacs21 is not installed.
  Package emacsen is not installed.
  Package xemacs21-mule which provides emacsen is not configured yet.
  Package emacs23 which provides emacsen is not configured yet.

dpkg: error processing ess (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of hyphen-en-us:
 hyphen-en-us depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.

dpkg: error processing hyphen-en-us (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ispell:
 ispell depends on dictionaries-common; however:
  Package dictionaries-common is not configured yet.

dpkg: error processing ispell (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ienglish-common:
 ienglish-common depends on dictionaries-common (>= 1.10.6~); however:
  Package dictionaries-common is not configured yet.
 ienglish-common depends on ispell (>= 3.3.02); however:
  Package ispell is not configured yet.

dpkg: error processing ienglish-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of iamerican:
 iamerican depends on dictionaries-common; however:
  Package dictionaries-common is not configured yet.
 iamerican depends on ienglish-common (= 3.3.02-5build1); however:
  Package ienglish-common is not configured yet.
 iamerican depends on ispell; however:
  Package ispell is not configured yet.

dpkg: error processing iamerican (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up pspp (0.7.9+git20120620-1) ...
Install pspp for emacs
Install pspp for xemacs21
install/pspp: Handling install for emacsen flavor xemacs21

WARNING:
Couldn't find obvious defaults for:
data-directory
mule-lisp-directory
lisp-directory
Perhaps some directories don't exist, or the XEmacs executable,
/usr/bin/xemacs21
is in a strange place?Loading /usr/share/emacs/site-lisp/debian-startup...
Loading 00debian...
Error while loading 00debian: Symbol's function definition is void: loop
Loading 00debian-vars...
Loading 50a2ps...
Loading 50autoconf...
Error while loading 50autoconf: No /usr/local/ prefixed paths in load-path
Loading 50dictionaries-common...
Error while loading 50dictionaries-common: No /usr/local/ prefixed paths in load-path
Loading 50emacs-goodies-el...
Package emacs-goodies-el not fully installed.  Skipping setup.
Loading 50ess...
Package ess not fully installed.  Skipping setup.
Loading 50pspp...
Symbol's function definition is void: batch-byte-compile
xemacs exiting
.
ERROR: install script from pspp package failed
dpkg: error processing pspp (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xemacs21-bin:
 xemacs21-bin depends on xemacs21-support (= 21.4.22-3.2ubuntu2); however:
  Package xemacs21-support is not configured yet.

dpkg: error processing xemacs21-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 dictionaries-common
 aspell
 aspell-en
 emacsen-common
 emacs23-common
 emacs23-bin-common
 emacs23
 emacs
 xemacs21-mule
 xemacs21
 xemacs21-support
 emacs-goodies-el
 ess
 hyphen-en-us
 ispell
 ienglish-common
 iamerican
 pspp
 xemacs21-bin
```

What I did was return to the open source driver in Software Sources, then restart. After the restart I then installed the linux-headers-generic package from the command line.

Then I went to software sources and activated the fglrx-updates driver.

The reason for doing it in this order is so when you activate fglrx, it can be built properly (it's a kernal module).

If you activate it and THEN install the headers without deactivating it first, you're stuck with brokenness.

Try it the way I described and let me know if it works out for you.

---

### Post by endguy on 2012-10-23
Try running:

```
sudo /usr/lib/emacsen-common/emacs-remove xemacs21
```

---

### Post by proghume on 2012-11-16
This doesn't work for me. I did a fresh install of Ubuntu, installed linux-headers-generic and tried to activate fglrx-updates. No luck, exactly the same problem as in the start of this thread. Radeon HD 5850.

Man, every few years I get the urge to see how Linux has improved, but come away cursing. Ubuntu 12.10 made a *terrific* first impression, but then I press a button to enable hardware accelerated drivers and suddenly the thing just doesn't work, I have no idea what to do and the even trying to start X in safe mode through the boot loader won't actually start the OS in any form.

EDIT:
The 12.11 Beta directly from AMD works. It's annoying though, because of a watermark that says AMD Testing use only.

EDIT2:
This fixed the watermark for me:
[http://askubuntu.com/questions/206558/how-to-remove-the-amd-testing-use-only-watermark-from-ubuntu-12-10/218698#218698](http://askubuntu.com/questions/206558/how-to-remove-the-amd-testing-use-only-watermark-from-ubuntu-12-10/218698#218698)

I don't know how stable the beta drivers are, but all the other hardware accelerated ones crash every time, immediately. No problems so far with these.

---

