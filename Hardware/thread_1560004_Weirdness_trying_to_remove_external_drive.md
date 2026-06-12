---
title: "Weirdness trying to remove external drive"
date: 2010-08-24
forum: Hardware
---

### Post by Shay Guy on 2010-08-24
I'm not sure why this happens, but sometimes, when I remove an external drive, /media/EXTDRIVE/ will still be there, but without read permission. Plugging it back in makes another directory, /media/EXTDRIVE_/. The other day, I was able to make it stop doing this by unplugging the drive again and using sudo rmdir on the "extra" directory; but today, that's giving me a "Device or resource busy" error. Short of rebooting, how can I get around this problem?

---

### Post by sydbat on 2010-08-24
> **Shay Guy said:**
> I'm not sure why this happens, but sometimes, when I remove an external drive, /media/EXTDRIVE/ will still be there, but without read permission. Plugging it back in makes another directory, /media/EXTDRIVE_/. The other day, I was able to make it stop doing this by unplugging the drive again and using sudo rmdir on the "extra" directory; but today, that's giving me a "Device or resource busy" error. Short of rebooting, how can I get around this problem?How are you removing the drive? Are you just pulling the cord? If so, there's your problem.

If you have used the "Safely Remove Drive" option when right-clicking on the drive, then pulling the cord, it should properly unmount and remove the entry.

---

### Post by Shay Guy on 2010-08-24
Well, that doesn't usually cause a problem for me, but yes.

So now that I know how to keep it from happening again, how do I get rid of the extra directory that's already there?

---

### Post by sydbat on 2010-08-24
> **Shay Guy said:**
> Well, that doesn't usually cause a problem for me, but yes.

So now that I know how to keep it from happening again, how do I get rid of the extra directory that's already there?I take it that it is under /media when you physically look at that directory? If so, hit 'Alt+F2' and type in gksudo nautilus. It will ask for your password. Then navigate to /media and delete the offending folder.

---

### Post by Shay Guy on 2010-08-24
That'd probably work if not for this part, which remains even when gksudo-ing it:

> **Shay Guy said:**
> The other day, I was able to make it stop doing this by unplugging the drive again and using sudo rmdir on the "extra" directory; but today, that's giving me a "Device or resource busy" error.

---

