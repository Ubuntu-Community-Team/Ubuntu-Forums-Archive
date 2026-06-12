---
title: "Hardy refusing to keep nvidia drivers or monitor settings"
date: 2008-05-02
forum: Hardware
---

### Post by jaydubster on 2008-05-02
I really am cursing the day I "upgraded" to 8.04LTS
Gutsy worked perfectly, but I've wasted about 4 hours just trying to get this poxy system to do anything useful since the 'upgrade'

Ok, Nvidia GF4 Ti 4400, iWill MoBo (old but fine), 1Gb ram, running Gnome I think. 
How do I check Gnome or KDE? This was Gutsy to Hardy upgrade, not fresh install.

This exact setup ran with restricted drivers & hardware accell on Gutsy, no trouble.

With Hardy I can't even find the restricted drivers, and it doesn't point out the lack of them, like Gutsy did.
Admin/Hardware Drivers shows "no proprietary drivers in use" and I have no hardware acceleration at all. System's real slow.

Envy goes thru setup, finds my card & screen, reboots then forgets everything. Gives me "low graphics mode" screen, with vesa drivers & plug n play monitor every time.

Just done the "recovery, sudo dpkg-reconfigure... thing, got 1024 but no drivers.

Enabled "Screens & Graphics" & can adjust screen res, but reboot & it's gone again. Every time it completely forgets my working settings & gives me the "low graphics mode - vesa drivers, plug n play monitor" junk *grrrr*

Where are the restricted drivers now?
How can I install them as Envy obviously refuses to help?

Can't login as root, & can't save xorg.conf file;
Tried to copy the graphics card & monitor code out of an old (working) xorg file, but it won't let me save, even after editing via: sudo gedit

Think I should format & head back to gutsy as this really is peeing me off.

Any more suggestions ???
Seems that many people are having graphics issues with Hardy that weren't there with gutsy. What have they broken & when will they fix it ??

---

### Post by wrightee on 2008-05-02
Sorry Jay, no fix from me - just chiming in with a "me too".

I followed the instructions posted at LucioAlbenga.com which *worked* - when I got back in (without a reboot) I had the full 1920x1200 resolution. 

But, any reboot and I only get low graphics mode too.

---

### Post by jaydubster on 2008-05-02
Oh Man! but at least I'm not the only one. Hardy sucks balls imho.

Wonder if it'll be any different if I DL hardy & do a clean install, not an upgrade.
Really shouldn't have to though, it worked brilliantly before.
Now it's just stressing me out every frikkin time I go near it.
4 days, many hours, exactly the same boat as when I started *grrrrrr*
Maybe I should say sod it & go back to Gutsy :(

---

### Post by wrightee on 2008-05-02
That didn't help me - I did an upgrade first and completely hosed my machine.  Then did a clean install wiping everything and can only get low graphics.. except for those moments immediately after installing the driver when I get the tantalizingly perfect full res on my HD screen... :(

Gutsy was working so well too.

---

### Post by jaydubster on 2008-05-02
Thanks for the info, think I'll screw it & go Gutsy then !!

Good luck with yours, prolly best going gutsy too !!

---

### Post by starcannon on 2008-05-02
I only had to add nvidia to my /etc/modules list, and I blacklisted nv in the /etc/default/linux-restricted-modules-common file.

so my /etc/modules file looks like this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
nvidia

```

and my  /etc/default/linux-restricted-modules-common file looks like this:
```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="nv"

```

That worked for me, my settings and drivers are remembered every boot now; side note, I used to have to do this in Gutsy as well, maybe because I do run the latest drivers from the Nvidia.com site. Do try this, it only takes a moment and a reboot and it may be your fix. Get back to us, I always like to know if I helped or not so that I don't continue giving bad advice ;)

---

### Post by jaydubster on 2008-05-20
Thanks for your input starcannon, it worked to a point...
As in, started up (this time at least) without entering low gfx mode, but I've still no hardware accelleration, so it's still a bag o nails.
I'll try a reboot in a min, see is she starts up in 1024 for starters.

WOOHOO !!!   We Have LIFT OFF !!!

Did the script thing to completely remove Envy,
reinstalled it from Synaptic, logged off, ran Envy, let it auto configure then rebooted.
Suddenly Compiz works, I have nice little flashes and animations on mouse clicks, and it's firing along a decent speed at last !!

Now I just gotta update the beastie (150mb to DL) and see how she fares after a complete shut down.

---

### Post by lightsaber on 2008-07-18
Anyone know if there is a reason it needs to be blacklisted now but not previously?  Since they first started using the proprietary drivers I've had no problems just installing and running.  This should probably get fixed in the installer or something as average users are not(and should not) be modifying config files.  That's like telling the average user to apply registry hacks in Windows.

I'm a big fan of Ubuntu.  I've been using it since 5.04 and I've run Debian in the 4 years previous.  Ubuntu has allowed me to make my whole house as well as my office computer Windows free.  However, one of the things that drew me to it is the fact that I can put my parents and my wife on it and expect that they will be able to operate with only minor difficulty.  Asking one of them to modify a config file is out of the question.

---

