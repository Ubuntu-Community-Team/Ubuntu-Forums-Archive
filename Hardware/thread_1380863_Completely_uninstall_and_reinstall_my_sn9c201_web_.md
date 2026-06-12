---
title: "Completely uninstall and reinstall my sn9c201 web cam driver"
date: 2010-01-14
forum: Hardware
---

### Post by Rezwan Mahbub on 2010-01-14
I want to completely uninstall and reinstall my sn9c201 web cam driver to make it working again. I had installed the driver from the site: [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft). It worked for many days but now I cant find my web cam in Skype.

What may be my possible steps to solve it. Please.

---

### Post by Rezwan Mahbub on 2010-01-15
Ubuntu forums sucks!!! I never found it to be responsive like other forums. May be the experts have left the forum already.

---

### Post by IcarusR on 2010-01-16
If you still have the source directory, where you compiled it from, you may be able to remove it with...
```
make uninstall
```

The quoted page says..
> NOTE: This driver has been deprecated in favor of the sn9c20x sub-driver that is now included in the mainline kernel (2.6.31 or higher).
Which would suggest that your webcam should work without extra modules if running 2.6.31 or higher kernel.

The reason nobody has replied is that they do not have anything positive to suggest.
This is no reason to slag the forum & it's users !!

---

