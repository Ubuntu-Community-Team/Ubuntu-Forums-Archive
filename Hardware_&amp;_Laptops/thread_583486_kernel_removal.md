---
title: "kernel removal"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by shanerdaner on 2007-10-20
Hi I upgraded to gutsy but I had to delete an old kernel in order for the new version to boot.  I deleted the kernel in my grub boot options and it boots beautifully... my question is do I need to delete the old kernel?  if so how?  love the new upgrade it is great!!

---

### Post by monoufo on 2007-10-20
you can remove old kernel in synaptic if you want.  It's certianly not required as kenels would take up a negligible amount of disk space.

---

### Post by shanerdaner on 2007-10-20
how do I do this?  TIA

---

### Post by jespdj on 2007-10-20
System / Administration / Synaptic Package Manager
Search for "linux"
Mark the old kernel and possibly other stuff for deletion
Click "Apply"

---

### Post by shanerdaner on 2007-10-20
Well I cannot find it I know it was kernel with 14 in it the newest is 16 if it does not hurt I may keep it...  thoughts??

---

### Post by monoufo on 2007-10-21
in Synaptic, click on installed (local or obsolete) in the left side menu.  This will show you all the old things and things you manually installed that aren't in the repos.  you should see your old kernels in there.  to get that choice to show up click the status button in the bottom left section.  you may also want to click on not installed (residual config) and mark those for complete removal.  This is all assuming you want a nice clean system.  You could just leave that stuff there, it causes no harm.

---

### Post by shanerdaner on 2007-10-21
thanks!!!

---

