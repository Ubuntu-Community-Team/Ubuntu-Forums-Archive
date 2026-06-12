---
title: "No internet with Live CD"
date: 2005-11-12
forum: General Help
---

### Post by mcrofutt on 2005-11-12
I just received my brand-spankin' new Breezy CD's today!! Booted the live first to see if all the changes were as kool as I'd hoped...was NOT dissapointed,, except Firefox won't connect to the net. :(  Hoary worked flawlessly on the SAME box without any input from me. What was changed that I can look at and MAYBE fix? I've set the networking tools to the exact settings that I had for hoary. Any clues?
 I don't want to install without I figger this out!


 Thanks,
 Marcus

---

### Post by Qrk on 2005-11-12
Are you on a modem? Those still have shody support.

also try 
```
sudo dhclient
```

and

```
ifconfig eth0 up
```

---

