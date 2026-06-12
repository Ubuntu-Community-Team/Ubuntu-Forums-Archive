---
title: "Can't Install Blender"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by adinfinitum on 2009-03-09
Hi all,

Have done a search but find almost no reference to my particular error.

Using Hardy, I am trying to install Blender, but whether via Synaptic or Command, I get the same error

-Synaptic=
blender:
 Depends: libgettextpo0  but it is not installable

Terminal=
tony@tony-desktop:~$ sudo apt-get install blender
[sudo] password for tony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  blender: Depends: libgettextpo0 but it is not installable
E: Broken packages
tony@tony-desktop:~$ 
.....

a Google search for "libgettextpo0" reveals almost nothing.

Any ideas?

---

### Post by cariboo on 2009-03-09
Go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages, and remove the broken packages and try again.

Jim

---

### Post by adinfinitum on 2009-03-11
thanks, but no change

---

