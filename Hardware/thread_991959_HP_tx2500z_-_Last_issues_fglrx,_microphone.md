---
title: "HP tx2500z - Last issues: fglrx, microphone"
date: 2008-11-24
forum: Hardware
---

### Post by luckygerbils on 2008-11-24
I've been working on getting everything setup correctly on my new hp tx2500z for about a month now.  Nearly everything is working now, and the last few things I'd need to be completely satisfied are: screen rotation, and front microphone use.

Today I found some information on the newest fglrx driver (which wouldn't upgrade from the repository so I just downloaded and installed it directly).  This newest driver APPEARS to support rotation and I got really excited at first, but then I noticed the screen was entirely unresponsive.  You can still click things and change window focus, but nothing will actually move on the screen except the mouse.  You have to blindly navigate back to your terminal and type "xrandr -o normal" to recover.

Has anyone downloaded and used this driver successfully on one of the tx2000 series?

NOTE: Some tx2000's have nvidia graphics cards, which appear to support rotation perfectly--this isn't what I have.  Also, I know that the ati and radeon drivers both support rotation, but they're currently extremely slow and had other graphics problems with my hardware.


The integrated microphone has never worked and I've tried everything that I could throw at it. I don't even think that it is showing up as an input device.  I've seen many tutorials where they say they got external mics working, but has anyone gotten the integrated one?


Some system information:
Ubuntu 8.10 Intrepid Ibex (kernel 2.6.27-7-generic)
ATI Radeon HD 3200 Graphics
fglrx version: Catalyst 8.11 (newest version installed manually)

Thanks for whatever help can be given!
I might be able to answer some questions about other tx2000 setup since I've gotten this far.

EDIT: haha, apparently fglrx now starts in rotated mode too, meaning every boot I have to do a blind 'xrandr -o normal'.  help!

---

### Post by Favux on 2008-12-04
Hi luckygerbils,

The way those of us with TX2000's and nVidia graphics get our rotation working is adding this command to our video device section in xorg.conf:
```
	Option		"RandRRotation"  "on"
```
In other words our xorg.conf for video looks like:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	Option		"RandRRotation"  "on"
EndSection
```
where yours would say "flgrx" instead of "nvidia", or something close.  I'm assuming you otherwise have a working xorg.conf and your sylus, eraser, and touch work.  And that you can calibrate them through wacomcpl.

Now how did you rotate your screen?  Did you use something like ATI Settings in System Preferences or Administration?  I'm trying to get an idea why you're booting up rotated.

There's a cpl. basic ways we rotate the tablet and get the stylus, eraser, and touch to go along.  I explain this here:
   [http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")
Hope this helps some.  Good luck.

PS:  Let me know if the new flgrx driver really supports rotation.  We could add it and the TX2500 to the HOW TO.

---

### Post by Favux on 2008-12-06
luckygerbils,

As far as I have been able to determine ATI's proprietary driver "flgrx" up to and including Catalyst 8.11, does not support rotation.  It looks like you'll have to use Xorg's "radeon" driver to get rotation.

---

### Post by luckygerbils on 2009-01-25
I think I remember the documentation saying that it did, but I had to follow the extremely complicated (and actually incorrect) install procedure on the ati site (which I don't recommend).  I did have that bit of annoying rotation going for a while, but I've since downgraded back to the current version in the repos and I don't really want to mess up my configuration again.

The radeon driver has gotten better, but I still can't run compiz with it, and the rotation I get includes a lot of tearing.

Tried the RandRRotation thing a long time ago, it's just the nvidia one that supports that.

Is anyone else even having my problems with the built in microphone though?  This thread is the first google result for that problem...

---

### Post by Favux on 2009-01-25
Hi luckygerbils,

Bummer you still have the microphone problem.

I'm sorry about the:
```
	Option		"RandRRotation"  "on"

```
thing.  That was before I realized it depended on the video card.  NVidia and Intel need it, I guess.

The reason I posted is I was talking to a TX2z owner a few days back who claimed rotation with "fglrx".  I think he has the newest one with Catalyst 8.12, which I don't think is in the repositories.  I asked him for more details (version, etc.), but he hasn't posted back.  I did look at the ATI site, and it still doesn't say anything about rotation.  That I could see anyway.

---

### Post by psycho on 2009-02-03
i can confirm that the latest fglrx (the one that's just a few days old, from ati.com) works (partially) with rotation.

i say "partially" because while the rotation is fine (you just have to do a quick```
sudo aticonfig --set-pcs-str="DDX,EnableRandR12,TRUE"
```to enable it), it seems somehow to conflict with compositing. if you don't care about drop-shadows or fancy compiz effects etc., this doesn't matter: rotate and be merry.

on the other hand, if you're using a compositor then it seems you have a choice between non-flickering 3d, OR screen rotation, but not both at the same time. i haven't figured out why yet, but toggling the option above (the EnableRandR12 setting in the /etc/ati/amdpcsdb database) seems to cause one problem whenever it fixes the other.

---

### Post by jpeter55 on 2009-04-24
I'm having the microphone problem too.  I'd love to figure out how to get this working, but no luck so far. The suspend/hibernate also doesn't seem to work properly, as the computer freezes completely upon resume. Also, only one application seems to be able to use the sound card at one time.  For example, if firefox is open and I've just played a youtube clip, I can't listen to music or make skype calls until I close firefox, and vice versa.  Any ideas?

---

