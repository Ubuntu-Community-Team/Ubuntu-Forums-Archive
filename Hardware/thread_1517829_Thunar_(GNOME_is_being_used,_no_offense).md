---
title: "Thunar (GNOME is being used, no offense)"
date: 2010-06-25
forum: Hardware
---

### Post by jjpcexpert on 2010-06-25
I've had an absolutely hilarious error.
See the attached picture for more information.
The situation is, the GTKRC is returning: Murrine configuation option "gradients" is no longer supported and will be ignored.

Thunar interprets this (since it was on STDerr) as a permissions error.
It is hilarious, but don't laugh, it is serious. Updates must be made to Human (theme) to correct this error.
Oh and Thunar is running as root, because I've done a fix to my copy of the theme (or should better well have) and this is a frustration.

Or at least Thunar does not return a GTKrc error code when I run it as user, but rather a Fuse error.
:confused: as to how this happened.
Additionally, there is a simple FUSE error - I am not permissioned - even when I'm root! The Nautilus says - Fuse error (as user).

Footnote: This is hardware not working in a good way for Ubuntu's philosophy

Also, when I try to unmount the failed-to-mount-properly disks, it disagrees with the FStab. Grrrgh.

---

### Post by rollin on 2010-06-25
Got an imagebam link or something for the screenie? I don't see any image??
Edit: That's weird now I see it after posting...

---

### Post by rollin on 2010-06-25
Found this on google: [http://www.khattam.info/2010/02/11/solved-murrine-configuration-option-scrollbar_color-gradients-is-no-longer-supported-and-will-be-ignored/](http://www.khattam.info/2010/02/11/solved-murrine-configuration-option-scrollbar_color-gradients-is-no-longer-supported-and-will-be-ignored/)

---

### Post by jjpcexpert on 2010-06-26
/!\ THIS THREAD MIGHT LOOK LIKE AN ADVERT!!!!! Don't worry if it does.

Weird. How do I fix the ntfs-3g error? Reinstall fuse?

Refer to thread Hilarious Error #2 for info on my latest. Search Hilarious Error #2 in the box for more info.

Summary:

Now exo-mount has a problem and accepts gtkrc errors as device errors, but who will fix it? Find out in that thread.

---

