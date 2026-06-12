---
title: "Vista and Ubuntu dual-boot on a laptop"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by librarianlookingforhelp on 2009-07-11
I want to update my laptop so that it can dual boot Ubuntu and Windows Vista.  I am wondering: a)what problems/challenges/evil glitches I can anticipate, and b)will it hinder the performance of my laptop?

---

### Post by Zimmer on 2009-07-11
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Works for me...  EasyBCD installed on the Vista install,  GRUB installed to the Ubuntu partition and NOT to the MBR,
 Oh, and using the Vista file tools to free up space for the Ubuntu install.
Vista may be very mean in how much space it will let you have back. There are various tips around to try and squeeze as much as possible. If I find them I will update this post..

---

### Post by merlinus on 2009-07-11
In order to free up more space in the vista partition before shrinking, delete temp and other unneeded files and defrag several times.

You can free up even more room by disabling paging (option probably located in disk manager), rebooting, deleting pagefile.sys, defragging, and then shrinking.

---

### Post by librarianlookingforhelp on 2009-07-11
Thanks for all of your help... Do you think I would be smart to upgrade Vista to Windows 7 before installing Ubuntu?  I know (supposedly) it resolves some of Vista's resource gobbling ways.

---

### Post by merlinus on 2009-07-11
If you are planning to upgrade anyway, it would make sense to do it before installing ubuntu.  If you do it afterwards, you will have to reinstall grub, since windows will install its bootloader to the mbr, but this is no big deal.

My reasoning includes the sad reality that whatever can go wrong probably will, especially with installing windows.

---

### Post by lisati on 2009-07-11
I set up dual-boot Vista & Ubuntu on my laptop without any major hassle. What I did was something along these lines:
[LIST=1]
[*]Make a backup of important data
[*]Clean out temporary files from Vista. As useful as the "disk cleanup" utility that comes with Windows can be, it might be necessary to navigate to the %temp% directory.
[*]Defrag a few times
[*]Locate and try to use Vista's resize option to free up a bit of space. Failed, possibly due to unfamiliarity......
[*]Boot from Live CD, and use the copy of gParted to tinker with partition sizes. (It's on the System->Administration menu under "partition editor")
[*]Install Ubuntu, telling the partition manager to use the largest continuous free space.
[*]Boot into Ubuntu from HD, do a preliminary check that things are working, install updates, and do a couple of minor tweaks.
[*]Eventually boot back into Vista to let it do its CHKDSK stuff and to make sure it wasn't seriously hurt.
[/LIST]

Edit: as usual, don't forget to make sure you have a way of recovering important stuff in the unlikely event of something going wrong..... backup backup backup

---

