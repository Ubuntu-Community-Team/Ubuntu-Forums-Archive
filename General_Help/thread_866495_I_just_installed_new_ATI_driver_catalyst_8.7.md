---
title: "I just installed new ATI driver catalyst 8.7"
date: 2008-07-21
forum: General Help
---

### Post by sdowney717 on 2008-07-21
It now has ubuntu support
file name is ati-driver-installer-8-7-x86.x86_64.run

notice and download it here
[http://www.phoronix.com/scan.php?page=news_item&px=NjYwNQ](http://www.phoronix.com/scan.php?page=news_item&px=NjYwNQ)

after you download it simply a few steps
make it executable
build an ubuntu package like this for hardy 8.04:

 sudo ./ati-driver-installer-8-7-x86.x86_64.run --buildpkg Ubuntu/8.04
 Five debs get made

move the resulting deb files to a certain directory
run this command to install, do this from within directory

sudo dpkg -i *

2 issues came up.
I had to install cdbs common build system for Debian packages using synaptic, make sure this is installed before building your package.
I had to manually remove old fglrx control and fglrx amdcc using synaptic, probably should do this before installing the new debs.
Then installed the new fglrx-amdcc

so far it is working just fine.

---

### Post by sbyte on 2008-07-22
Does the new driver resolve the issue when running Xv in windowed mode?

ie. do movies still flicker when in windowed mode?

---

### Post by sdowney717 on 2008-07-22
I dont know, but for me I did not have that problem.
I usually run compiz and must play video using x11 video output.
So for a test, I switched window managers back to metacity, and ran totem which is set for Xv. No flickering.
My other players, smplayer and VLC use x11 playback. No flickering on any of them.
GoogleEarth still flashes when running compiz, no flashing when running metacity.
I still get problems switching users using the fast user switcher applet.

My video card is an older ATI 9600se with only 64mb.

---

### Post by rbmorse on 2008-07-22
I see the same behavior here. 

Curiously, if I purge the existing FGLRX driver files and then reinstall the 8.6 drivers using EnvyNG (in repository) I don't have the video blanking problem with Compiz enabled that I see when the drivers are installed with the ATI installer. 

I don't know what the Envy devs are doing in this regard, but I am glad they are on the case.

---

### Post by chalewa on 2008-07-22
> **sbyte said:**
> Does the new driver resolve the issue when running Xv in windowed mode?

ie. do movies still flicker when in windowed mode?

yes

---

### Post by chalewa on 2008-07-22
what is the version number that you have in catalyst after installing 8.7?

---

### Post by rbmorse on 2008-07-22
8.51.3

---

### Post by The Tronyx on 2008-07-22
Problem Solved.  Post Erased.

---

### Post by sbyte on 2008-07-22
> **sdowney717 said:**
> I dont know, but for me I did not have that problem.
I usually run compiz and must play video using x11 video output.
So for a test, I switched window managers back to metacity, and ran totem which is set for Xv. No flickering.
My other players, smplayer and VLC use x11 playback. No flickering on any of them.
GoogleEarth still flashes when running compiz, no flashing when running metacity.
I still get problems switching users using the fast user switcher applet.

My video card is an older ATI 9600se with only 64mb.



Im running the newer HD4850.
Taking your advice and setting Mplayer to x11 playback has resolved the flickering. however i still get flickers on VLC, TOTEM (both Xv) while Compiz is enabled.

at least its working on one player now, i can live with that.

---

### Post by sdowney717 on 2008-07-22
You can set smplayer and VLC to use x11 video output.
I actually for video prefer smplayer to mplayer.
Try out smplayer. 

[http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)

Has anyone figured out how to set totem to use x11?

Any thoughts on googleearth flicker?

---

### Post by External on 2008-07-23
> **sdowney717 said:**
> It now has ubuntu support

I wonder what that "Ubuntu support" means. The referred text in the original post claims this 

> In fact, the new features in this release are just bringing official Ubuntu 8.04 and SuSE Linux Enterprise Desktop 10 SP2 support.

but according to the ATI 8.7 release notes only 1 minor Ubuntu-related issue has been 'corrected'. So in what ways is Hardy supported? (Especially if a lot of people experience flickers and ghost images, as well as problems during installation, as I did.)

---

### Post by jocko on 2008-07-23
> **sdowney717 said:**
> Has anyone figured out how to set totem to use x11?

Any thoughts on googleearth flicker?

Totem (and all other gstreamer apps):
Set gstreamer-properties to use x11 and live with the poor quality of x11 compared to xv.

Googleearth: Probably no fix, other than disabling 3d rendering in googleearth, which makes it VERY slow (a fix in the same direction as using x11 instead of xv for video rendering, in my opinion...)

---

### Post by cristo-father on 2008-07-25
> **sdowney717 said:**
> It now has ubuntu support
file name is ati-driver-installer-8-7-x86.x86_64.run

notice and download it here
[http://www.phoronix.com/scan.php?page=news_item&px=NjYwNQ](http://www.phoronix.com/scan.php?page=news_item&px=NjYwNQ)

after you download it simply a few steps
make it executable
build an ubuntu package like this for hardy 8.04:

 sudo ./ati-driver-installer-8-7-x86.x86_64.run --buildpkg Ubuntu/8.04
 Five debs get made

move the resulting deb files to a certain directory
run this command to install, do this from within directory

sudo dpkg -i *

2 issues came up.
I had to install cdbs common build system for Debian packages using synaptic, make sure this is installed before building your package.
I had to manually remove old fglrx control and fglrx amdcc using synaptic, probably should do this before installing the new debs.
Then installed the new fglrx-amdcc

so far it is working just fine.

I have 2 questions.
1) How do i make it executable?
2) I have hardy 8.04.1 64 and a HD4850. What do i have to change on the instructions(based on the architecture and version)?

---

### Post by olskar on 2008-07-25
Make it executable with > chmod +x ati-driver-installer-8-7-x86.x86_64.run --buildpkg Ubuntu/8.04



Edit: And check this out, very good guide
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by cristo-father on 2008-07-26
> **olskar said:**
> Make it executable with 



Edit: And check this out, very good guide
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Worked!!!:)

---

