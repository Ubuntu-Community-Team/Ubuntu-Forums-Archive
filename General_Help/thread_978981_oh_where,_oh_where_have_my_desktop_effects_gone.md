---
title: "oh where, oh where have my desktop effects gone?"
date: 2008-11-11
forum: General Help
---

### Post by lonjim2 on 2008-11-11
I was using Ibex for quite some time, and out of nowhere my compiz desktop effects magically dissappeared  (after I changed themes).

I ran ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

I can't figure out why it's not working -- any ideas?

---

### Post by hictio on 2008-11-11
What happens if you execute 'compiz' on a terminal? Did you do it? Does it print any info?

---

### Post by jerrylamos on 2008-11-11
8.10 Intrepid compiz is broken for many Intel graphcis chips.  Compiz uses a code path no one else does.  If compiz is run on the pc's affected the pc's freeze, power off time.  They won't even boot, getting a "black screen" just after login since  compiz is on by default.

The temporary "workaround" is to "black list" the chips they know of so far that don't work.  Compiz won't be started for those pc's.
 
Without the "blacklist" those pc's won't run Ubuntu at all.  They don't have a solution to providing "eye candy" for the affected pc's yet.

If you want "eye candy" use Hardy 8.04.  There's more detail in Launchpad Bug #259385.

Jerry

p.s. I use full screen internet, full screen office, full screen digital pictures, ... so I don't notice the loss of desktop effects.  Do realize desk top effects are in line code and do slow down the pc if you care.

---

