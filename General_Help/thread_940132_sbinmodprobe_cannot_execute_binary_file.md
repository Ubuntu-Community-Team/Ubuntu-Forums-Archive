---
title: "/sbin/modprobe: cannot execute binary file"
date: 2008-10-06
forum: General Help
---

### Post by Seedsta on 2008-10-06
I am attempting to install madwifi to support a D-Link DWA 652 with a Atheros AR5008 Chipset.  After running make, the command 

su ****  /sbin/modprobe ath_pci

I get the following

/sbin/modprobe: /sbin/modprobe: cannot execute binary file

I have searched and searched and searched to try and figure out what the problem is, but have come up empty handed.

Any help would be greatly appreciated.

the files are going to /lib/modules/2.6.24-19-generic/madwifi
if that helps.  I cant seem to figure out where modprobe is searching for the binaries at.

Thanks for any help

---

### Post by Seedsta on 2008-10-07
Does anyone at all have a clue as to what is going on with this?
the modprobe man says that the binaries should be in 

/lib/modules/'usr name' 

but that directory did not exist
so I used 

EDIT

After using the modprobe ath_pci -l -t /lib/modules//2.6.24-19-generic/madwifi

if finally seems to have installed, it still does not work, but it did not throw any error messages at me.

---

