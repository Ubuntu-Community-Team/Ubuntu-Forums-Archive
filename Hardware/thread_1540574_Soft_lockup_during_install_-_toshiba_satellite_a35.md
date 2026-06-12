---
title: "Soft lockup during install - toshiba satellite a355-s6935"
date: 2010-07-28
forum: Hardware
---

### Post by Alphagas on 2010-07-28
I am experiencing this soft lockup bug when I am trying to install. I am on a toshiba satellite a355-s6935: intel core 2 duo, 4gb ram, using ati mobility radeon hd 3650 video card. **None** of the workarounds I have found produce any results. I have been trying for about a week now to find a solution and m I'm at my wits' end. Please help

---

### Post by P4man on 2010-07-28
what soft lockup? Please elaborate. Does the livecd work? Also are you installing from CD or USB? Have you verified the medium for errors?

---

### Post by Alphagas on 2010-07-28
The live CD does not work.  I get the soft lockup during boot up, apparently, not install, although, it is not installed yet.  I have tried multiple CDs, and multiple versions of Ubuntu (10.04, 9.10, and 9.04, none have worked).  

The bootup/install gets to a point where it says the following messages:
```
W: Skipping nonexistent file /cdrom/dists/lucid/main/binary-amd64/Packages
W: Skipping nonexistent file /cdrom/dists/lucid/restricted/binary-amd-64/Packages
No value set for '/apps/netbook-launcher/favorites/favorites_list'
No value set for '/apps/netbook-launcher/favorites/favorites_list'
No value to set for key: '/apps/netbook-launcher/favorites/favorites_list'

```

then the following error messages repeat over and over:
```
BUG: soft lockup – CPU#0 stuck for 61s!
BUG: soft lockup – CPU#1 stuck for 61s! 
```

I have tried booting up with acpi off, in nomodeset, installing 9.10 and upgrading from there, the solution in this thread: [http://ubuntuforums.org/showthread.php?t=1537818](http://ubuntuforums.org/showthread.php?t=1537818) and nothing has made even a dent in getting past this point.

---

### Post by P4man on 2010-07-28
Have a look here:
[http://wwww.ubuntuforums.org/showthread.php?p=8893185](http://wwww.ubuntuforums.org/showthread.php?p=8893185)

Same laptop as you. Relevant quote:
[I]
3) Okay here's the important part. Apparently this particular graphics card fails to get properly allocated into the Kernel. So here's what you've got to do. Add** pci=use_crs** to the boot options. Do this by selecting your language with the arrow keys and enter. Then hit F6 and it will show you a menu. Close the menu out with Escape. Then type pci=use_crs directly after quiet splash --. It should look like “.seed boot=casper initrd=/casper/initrd.lz quiet splash -– pci=use_crs”. Hit enter to enter the Ubuntu environment. This should bypass the black screen problem with those having issues.[/I]

---

### Post by Alphagas on 2010-07-28
Thank you SO SO SO SO SO MUCH!!!! This worked like a charm.  I'm writing this post to you from inside Ubuntu!

---

