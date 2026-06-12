---
title: "HOWTO: Hibernate Working with ATI"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by Ken_Lewis81 on 2007-05-26
Hey all!

**Due to issues with the following material -- it isn't as reliable as I'd like -- take the following with a pinch of salt.  I'll update it when I've corrected the thing.**

I've been fighting with my MSI notebook to get Ubuntu Feisty and Gutsy to hibernate. I won this morning: it works.  I remember having Dapper work beautifully but as I dist-upgraded my way through Edgy and Feisty, functioning hibernate got lost along the way.

I have an AMD64 notebook running the 64-bit flavour of Ubuntu.  That's a side issue: the problem is the ATI chipset (Radeon Xpress 200, as a RS482 and SB400) and ATI Mobility Radeon X700.

Apparently the consensus in these forums and elsewhere is that the FGLRX driver, from xorg-driver-fglrx and linux-restricted modules doesn't like hibernating.  So, a couple of nights ago I followed the guide at [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) to get the most out of my X700 using the community-developed driver.  While everything else works a charm, illustrated by getting 2200FPS from glxgears, it turns out that my card and/or the driver doesn't like the line:
```
Option          "AccelMethod"   "EXA"
```

Making the amendments in the RadeonDriver wiki enrty restored Suspend functionality, and gave me hope for getting Hibernate to work.  I've looked over what I did, and there's no clear silver bullet which resolves this.  If this porvides helpful ideas, then use it -- but take care not to break your Ubuntu installation!


Looking over the /etc/acpi.d/event/hibernate.sh scripts, there's a configuration file in /etc/default/acpi-support which could do with some fiddling.  In the process of fiddling with /etc/default/acpi-support, I changed the lines marked with a '#' (no quotes) to make the line a comment and not valid, and to make it look like this:
```
# Should we save and restore state using the VESA BIOS Extensions?
**#SAVE_VBE_STATE=true**

# The file that we use to save the vbestate
**#VBESTATE=/var/lib/acpi-support/vbestate**

# Should we attempt to warm-boot the video hardware on resume?
**# POST_VIDEO=true ** *(I think this is default, but it might need to be set anyway)*
```

If this works for another ATI card and/or chipset combination, can you stick a comment below, and if it doesn't but inspires you to find another fix, I'd be glad to edit this and include your methods.

Hope this helps.
Take care.
Ken.

---

### Post by kingkookie on 2007-05-28
Which files are you editing?  I know the one is xorg.conf, but I don't know the other.

---

### Post by Ken_Lewis81 on 2007-05-30
I've edited it...  This now makes for the third revision.  The original had the right filename, but didn't uniquely resolve the problem.  I've tweaked other things with my system which were part of the process (like getting the best from the Radeon driver, specifying the 'RESUME=/dev/hda6' in both the GRUB menu and initramfs and forcing swap to be identified by /dev/hda6 in /etc/fstab instead of the newer '/dev/disk/by-uuid/' location -- which breaks because the swap partition is remade every time it's checked and when you hibernate).  I can document those extra things if you'd like.

Take care.
Ken.

---

