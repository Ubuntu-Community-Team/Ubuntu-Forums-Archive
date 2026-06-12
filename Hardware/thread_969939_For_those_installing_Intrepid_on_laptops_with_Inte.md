---
title: "For those installing Intrepid on laptops with Intel 830 graphics:"
date: 2008-11-03
forum: Hardware
---

### Post by immerohnegott on 2008-11-03
I just ran a clean install on my Dell Latitude C400 (which I've been using Ubuntu on with varying degrees of success for several years now) and was rather surprised when I booted the thing and X froze hard upon login -after GDM all you get is a mouse cursor on a blank background. Keyboard freezes and standard key combos are useless (no TTY, no CTRL+ALT+BACKSPACE).

The fix is to drop into a root term via the recovery mode and do this:

apt-get remove compiz
apt-get remove compiz-core

evidently there's a bug with the version of compizfusion being used in the fresh Intrepid install which breaks X on this chipset (i think 845 CGCs might be affected too).

Just letting you know.

---

### Post by immerohnegott on 2008-11-07
I've been messing with it some more since the install - it's been usable and hasn't hardlocked like early Hardy did with this chipset. My main issue now is the continuance of poorly rendered gradients in 24-bit mode - I've had this issue since late in the Gutsy lifecycle. Working on various options in xorg.conf, and digging through a bit of the intel driver's source code to no avail (i also compiled the latest version of the intel driver from source and it had the same issue, so the bug has yet to be fixed). 

If anyone feels like lending a hand here, it'd be greatly appreciated.

---

### Post by RtVD on 2008-11-10
I've just clean installed ubuntu 8.10 on an old vaio pcg-r505dl

it also has the intel 830M graphics chip, can't load compiz (worked fine in 8.04, not really a loss though)...

But more importantly/interestingly I get graphical corruption on fonts.. not an issue in 8.04, and I upgraded in place, had corruption issues, decided to clean install.. only to find them alive and well.

Think this could be to do with any 830M 8.10 issues?

-RtVD

---

### Post by immerohnegott on 2008-11-11
> **RtVD said:**
> 
Think this could be to do with any 830M 8.10 issues?

-RtVD

Highly likely. I've been getting all kinds of texture corruption, especially in Firefox. The icons on the tabs get corrupted, as do the Back, Forward, and refresh buttons.

I also get black bars across the panel (they disappear if I activate a button they're over).

I've tried this driver on two versions of Mandriva, as well as Fedora 9, and I got the same issues, so it's not Ubuntu's fault. It seems the Intel driver devs have slightly broken these chipsets in the the battle to fully support the newer stuff.
*sigh*
If I recall,the i810 driver works better (less corruption, REAL 24 bit color), but you have to completely disable DRI to keep it from hardlocking every five minutes.

---

### Post by RtVD on 2008-11-11
> **immerohnegott said:**
> Highly likely. I've been getting all kinds of texture corruption, especially in Firefox. The icons on the tabs get corrupted, as do the Back, Forward, and refresh buttons.

I also get black bars across the panel (they disappear if I activate a button they're over).

I've tried this driver on two versions of Mandriva, as well as Fedora 9, and I got the same issues, so it's not Ubuntu's fault. It seems the Intel driver devs have slightly broken these chipsets in the the battle to fully support the newer stuff.
*sigh*
If I recall,the i810 driver works better (less corruption, REAL 24 bit color), but you have to completely disable DRI to keep it from hardlocking every five minutes.

Ah, I did notice that I've now got the i915 driver in use.

I may work on replacing it with the i810 driver after work today, know if can I override the xorg probed stuff with an xorg.conf?

-RtVD

---

### Post by phidia on 2008-11-11
> **RtVD said:**
> Ah, I did notice that I've now got the i915 driver in use.

I may work on replacing it with the i810 driver after work today, know if can I override the xorg probed stuff with an xorg.conf?

-RtVD

That's an excellent question-how does one change xorg now? 
The dpkg-reconfigure command is all auto-no user input asked for or allowed. 
I've tried replacing xorg in 8.10 with a working one from 8.04 but it didn't change anything. I'm not using an intel card btw. 
Still I'd like to know if xorg configuration is intended to be automatic-as in corporate-no user configuration accepted?

---

### Post by immerohnegott on 2008-11-18
It would seem that it's inching toward an automatic-oriented setup. Displayconfig-gtk is gone entirely - the only easily usable display configuration tool is the basic GNOME resolution changing tool. This would all be well and good if everything worked properly (and most things do), but there are several points where an easier advanced config would be useful. 

One can still edit xorg.conf by hand to change options, specify valid modes, etc., but of course it isn't very user friendly. PLUS for whatever reason, selecting i810 as the driver in xorg.conf results in a "No Devices Found" error (I have the package installed). This worked fine in Hardy and before, but for the life of me I cannot get Intrepid to play nice with it.

I DID however discover that forcing the color depth to 16 gets rid of the graphical corruptions. In the "screen" section of xorg.conf, append the line:

```
DefaultDepth 16
```

24 bit color would be really nice, but this might have to work for now (they DID just update the driver today, I haven't checked it out yet).

---

### Post by RtVD on 2008-11-18
Excellent news, thanks!

Now I just need to figure out if the jogger/scroll wheel on my vaio can be used in 8.10, 8.04 picked it up ok (barring sony-laptop/sonypi incompatibility issues).
I may have to look at booting a live 8.04 on it and seeing what settings my xorg gets.

---

### Post by kevdog on 2008-11-29
Can someone post their xorg.conf file as mine is blank by default?

---

### Post by Nick Rhodes on 2009-01-09
The fix for the corrupt fonts is to edit your /etc/X11/xorg.conf

you need to add the following to the "Device" section

```

	Option	 "AccelMethod" "XAA"

```

Then there is not need to run 16 bit colours.

Cheers, Nick

PS I spotted thisfix on launchpad, well worth searching there for reports of existing bugs.

---

### Post by Jeroen de Lange on 2009-01-20
OK, I've got an old Dell C400 without an external CD-Rom.
So I copied the Ubuntu system to a stick and chose for double boot
Windows + Ubuntu

It took 4ever to install and when it was installed I got a white screen after logging in. I could see my cursor though.

What I did to solve this problem (with a little help from the web)
was

==> Choose Ubuntu (remember, dual boot)
==> Press Escape within a few seconds and go 4 Ubuntu 8.10 (recovery mode)

(U get all kinds of fun little letters that fly by so fast u can't read them xcept Activating swapfile. It ends up with a lovely blue screen)

==> Go to root and Enter

Then follow these instructions:

2) sudo pico /etc/X11/xorg.conf
3) Add the following:
Section "Extensions"
Option "Composite" "disable"
EndSection
4) save file, quit pico, logout.

Worked 4 me, and as a bonus, the inbuilt wifi network card works out of the box. I like it, cu

---

### Post by ls8 on 2009-02-11
Same problem here, esp. in Firefox menus and buttons sometimes get graphically corrupted (ping, green,...). Unfortunately neither DefaultDepth 16 nor XAA acceleration helped :(

---

### Post by immerohnegott on 2009-02-24
There may be another fix for that.

in xorg.conf, under the device section, rock something like this:

Section "Device"
Driver    "intel"
Option    "AccellMethod" "exa"
Option    "ExaNoComposite" "true"
Option    "UseFBDev" "true"
EndSection

Color is STILL shafted, but at least I can see what I'm doing. I had totally forgotten about those glitches, then I re-installed after playing with the Jaunty alpha...

---

### Post by cawaker on 2009-03-08
> **immerohnegott said:**
> I just ran a clean install on my Dell Latitude C400 (which I've been using Ubuntu on with varying degrees of success for several years now) and was rather surprised when I booted the thing and X froze hard upon login -after GDM all you get is a mouse cursor on a blank background. Keyboard freezes and standard key combos are useless (no TTY, no CTRL+ALT+BACKSPACE).

The fix is to drop into a root term via the recovery mode and do this:

apt-get remove compiz
apt-get remove compiz-core

evidently there's a bug with the version of compizfusion being used in the fresh Intrepid install which breaks X on this chipset (i think 845 CGCs might be affected too).

Just letting you know.

This worked for me on a fresh install of Intrepid on a Dell Inspiron 2600 but I also changed the xorg driver to "intel"

Fortunetly for me I dont need accelerated video or fancy graphics on that laptop.

---

### Post by jlewis05 on 2009-10-29
> **immerohnegott said:**
> There may be another fix for that.

in xorg.conf, under the device section, rock something like this:

Section "Device"
Driver    "intel"
Option    "AccellMethod" "exa"
Option    "ExaNoComposite" "true"
Option    "UseFBDev" "true"
EndSection

Color is STILL shafted, but at least I can see what I'm doing. I had totally forgotten about those glitches, then I re-installed after playing with the Jaunty alpha...

I'm positively ecstatic that this solved my graphics corruption issues, thank you so much.  I used it just as given in whole, so not sure if it all made the difference or one part in particular.  I am running Ubuntu 9.04 on a Sony VAIO PCG-R505EL with Intel 82830 (rev 4) graphics.  I was worried that perhaps there wasn't a fix after trying many things.  Colors look good to me, they might have been slightly altered but I can't really tell.  If there's any more information I should supply please let me know and I will get it right up here.  I know a lot of people with the VAIO PCG-R505 series have had problems with 9.04 and perhaps other versions.  Sorry if this has been addressed in another thread as I know the intent of this thread was for Intrepid users, hope it's helpful.

- John

---

