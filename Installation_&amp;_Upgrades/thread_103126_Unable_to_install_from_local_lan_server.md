---
title: "Unable to install from local lan server"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by aSa on 2005-12-13
Hi folks,

please give me a hint or two what I'm doing wrong here:

I have an old RH9 server acting as a file/dhcp/pxe server, and that's working like a clock.  The problem is that when I try to install Ubuntu 5.10 from it (with pxe/netboot stuff), installer stops soon after the first reboot ("phase 2" at 5%).  RH9 has apache running and working, and has a properly mounted Ubuntu iso.

My lan has access to the internet, and that (somehow) seems to be the reason to this behaviour.  **When I disconnect lan from the internet, Ubuntu installer works fine**, without a glitch.  So basically the server side is very close to ok.

When the Installer asks for sources/mirrors I give the address of my RH9 manually (like 10.10.10.254:80 and for path /ubuntu/).  This procedure works if my lan is *disconnected* from the internet.  The error situation (below) happens also with real internet mirrors.

With internet access allowed logs shows that last installed package was "popularity-contest 1.30ubuntu1" (dpkg.log) and some dependency problems are found (base-config-pkgsel.log):
> E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  kpdf: Depends: kdelibs4c2 (>= 4:3.4.3) which is a virtual package.
        Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
  libkscan1: Depends: kdelibs4c2 (>= 4:3.4.3) which is a virtual package.
  ksvg: Depends: kdelibs4c2 (>= 4:3.4.3) which is a virtual package.
        Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
  ksnapshot: Depends: kdelibs4c2 (>= 4:3.4.3) which is a virtual package.
             Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
  kooka: Depends: kdelibs4c2 (>= 4:3.4.3) which is a virtual package.
         Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
  kdegraphics-kfile-plugins: Depends: kdelibs4c2 (>= 4:3.4.3) which is a virtual package.
                             Depends: libopenexr2c2 (>= 1.2.2) which is a virtual package.
                             Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
  krita: Depends: kdelibs4c2 (>= 4:3.4.3) which is a virtual package.
         Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
  kamera: Depends: kdelibs4c2 (>= 4:3.4.3) which is a virtual package.
  kghostview: Depends: kdelibs4c2 (>= 4:3.4.3) which is a virtual package.
              Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.
  koffice-libs: Depends: kdelibs4c2 (>= 4:3.4.3) which is a virtual package.
                Depends: libqt3-mt (>= 3:3.3.4) which is a virtual package.

I'm trying to do a very basic install here at first with the default Gnome and all.  Similar to Ubuntu CDROM install, but from lan server.  No pre-seeding yet.  Those dependencies look a lot like KDE stuff and I'm not installing KDE at all.

Btw. installing from cdrom works ok too with internet access allowed.

I hope you understand what I'm trying to explain here and hope you can help me..

  Thank You.. aSa

---

### Post by aSa on 2005-12-14
:-k This is still puzzling me and stopping me thinking of any mass installations with this.  I'm not that good with Ubuntu/Debian so this seems to be too much for my know-how.  I have tried all variations I could think of.

---

### Post by aixguy on 2006-03-14
Did you ever get anywere with this?  I am using the pxe install and can get the server to load from the internet but can not figure out how to do it from a local server.  From what you said, it sounds like I need to umpack my iso file on an apache server.  I just can not figure out how to tell the installer where to go.  The main menu does not seem to take input.. From the looks of replies to your post, this is dark water ...

---

### Post by aSa on 2006-03-14
Well, that was soo long ago for my memory capacity.   But if I remember right, I did not totally get rid of the weird behaviour. I managed to create some sort of installation system for testing purposes but can't remember if I still had to unplug "the internet" from my home network while doing installations from my own server. My testing target was the preseeding function, especially its usability for mass installations.  I'm sorry I can't help you much at the moment.

Anyway I'm now waiting for the next release to appear.  That would be a good reason to try to recreate the installation environment again. Maybe with better luck.

:-?

---

