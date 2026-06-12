---
title: "apt problem"
date: 2008-10-01
forum: General Help
---

### Post by Bubba Ho_Tep on 2008-10-01
I'm trying to install the full version of vim and apt is complaining that it can't find a file for bluez-utils:

#############
$ sudo aptitude install vim-full
 <snip> 
 The following NEW packages will be installed:
   libruby1.8{a} tcl8.4{a} vim-full vim-gnome{a} vim-gui-common{a} 
   vim-runtime{a} 
 0 packages upgraded, 6 newly installed, 0 to remove and 366 not upgraded.
 Need to get 0B of archives. After unpacking 36.0MB will be used.
 Do you want to continue? [Y/n/?] y
 E: I wasn't able to locate file for the bluez-utils package. This might
 mean you need to manually fix this package. 
 Writing extended state information... Done
 E: I wasn't able to locate file for the bluez-utils package. This might
 mean you need to manually fix this package. 
 E: Internal error: couldn't generate list of packages to download
###########

I reckon I can fix that ok (or compile vim) but why is apt complaining about bluez-utils? Isn't that a package for bluetooth stuff?

What I don't understand is how this in any way related to installing vim.

I actually had a similar problem a while back when I was trying to uninstall a package (I don't remember what exactly  - I think it may have been Totem, the movie player). When I uninstalled it also uninstalled ubuntu-desktop.

I didn't notice at the time and I lost my GUI and had to reinstall.


Why is apt requiring packages that are completely unrelated to each other?




Cheers

BH-T

---

