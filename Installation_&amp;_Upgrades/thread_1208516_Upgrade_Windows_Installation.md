---
title: "Upgrade Windows Installation"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by lambogalardo on 2009-07-09
Hello All,

I currently have a gateway notebook with a 500GB HDD. it has a triple boot, Vista, Windows7 RC, and Ubuntu. I have preordered Win7 when it comes out in Oct, as it is running much better than the Vista. When the disk comes, can I simply run the upgrade in Vista, or will the GRUB be corrupt? Just as a note, my GRUB, after I cleaned up the titles and ordering, shows:
Windows 7/Vista Bootloader (from here I choose V/7)
Ubuntu
Ubuntu Safe
and a few other ubuntus

any ideas? It seems like Vista and 7 are very similar in the core, where XP to Vista was a huge change, so I imagine this being less of a deal than XP -> V. 

Thanks

---

### Post by raymondh on 2009-07-09
[QUOTE=lambogalardo;7587190] When the disk comes, can I simply run the upgrade in Vista, or will the GRUB be corrupt?[QUOTE]

I too have the upgrade option.  I think it will write a new MBR.  If so, you will just have to recover GRUB.

I  may be wrong through.

---

### Post by lambogalardo on 2009-07-09
...which I can do thru the Live CD, correct? I'm still new to this stuff...

---

### Post by raymondh on 2009-07-09
> **lambogalardo said:**
> ...which I can do thru the Live CD, correct? I'm still new to this stuff...

Yes.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

As it is still early and not final, see what happens first. I may be wrong.

---

### Post by lambogalardo on 2009-07-09
Great, thanks for the help!

---

### Post by raymondh on 2009-07-09
So, when you do get your disc, do you plan to upgrade Vista or upgrade the windows7RC (to final)?  I am wondering now what happens if we just upgrade the RC to final?

I ask because my plan is to take-out Vista .... which means I also have to uninstall RC as it will be unuseable (just like beta is now with RC out)

---

### Post by lambogalardo on 2009-07-09
> **raymondhenson said:**
> So, when you do get your disc, do you plan to upgrade Vista or upgrade the windows7RC (to final)?  I am wondering now what happens if we just upgrade the RC to final?

I ask because my plan is to take-out Vista .... which means I also have to uninstall RC as it will be unuseable (just like beta is now with RC out)
Optimally, I'd like to keep Vista and upgrade the RC, but since it's just the upgrade, I'm not sure if that's possible (RC is ultimate, i only bought Premium to match my Vista.) Honestly, at this point I am about to chuck my 7 RC partition. I had some huge changing of drive letters and such when I upgraded my HDD and the programs in 7 are very unstable... I guess once 7 is released I will delete the 7 RC, upgrade Vista to 7 then go in and save Ubuntu. ...this is a mess...

---

### Post by raymondh on 2009-07-09
Another option I am considering (for a diffrent machine) is to sole-boot ubuntu and just virtualize windows ... since I only use windows for a few apps and their data output, I can store in a USB or move to a storage partition which can be accessed (read and write) by Ubuntu.

Good luck on your next partitioning adventure .... Back up your files .... and Happy Ubuntuing.

---

### Post by Mark Phelps on 2009-07-10
There's been nothing official published on this yet, but as the RC that's been distributed is only Ultimate, unless you plan on wasting your money buying ultimate, you're not going to be able to "downgrade" your existing Ultimate install to something else.  Not surprisingly, MS has only supported upgrading "to" Ultimate from other versions.

Also, it's likely that while the RTM will be upgradeable to the retail version, the RC is most likely NOT going to be upgradeable.

You may be able to get away with using an "upgrade" version to do a clean install (if you don't want to upgrade your Vista install) simply by installing the new version and NOT supplying a product key at the time, and then doing an Upgrade install a second time, this time supplying the product key. That worked for Vista; don't know if it will still work for Seven.

---

