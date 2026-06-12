---
title: "Error with update manager"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by skewer_ on 2009-10-07
i need help resolving a problem with my update manager. i was trying to update some pakages using terminal  and this is the error i get:

" An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 57 in source list /etc/apt/sources.list, E:The list of sources could not be read.'  "


is there any way to reset or restore my system to about a week ago? i appreciate the help

---

### Post by dominiquec on 2009-10-07
Possibly an error with your /etc/apt/sources.list file.  If you have Synaptic (as I expect you would), fire it up and reset the repositories from there.  I suggest you take out any third-party repositories first.  Hit reload and try again.

---

### Post by skewer_ on 2009-10-07
update manager is not loading so is synaptic ... is there any other way to uninstall third party programs?

---

### Post by dominiquec on 2009-10-08
Please check this thread to see if it helps you: [http://ubuntuforums.org/showthread.php?t=445843](http://ubuntuforums.org/showthread.php?t=445843)

I would tend to think at this point that you have a corrupted /etc/apt/sources.list file.  Can you post the contents of the file here?

---

### Post by skewer_ on 2009-10-13
thanx dominique... everything is working great

---

