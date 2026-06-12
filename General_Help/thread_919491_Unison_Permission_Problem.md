---
title: "Unison Permission Problem"
date: 2008-09-14
forum: General Help
---

### Post by LonelyTraveler on 2008-09-14
I'm trying to sync two folders between my laptop and flash drive, but when doing that it fails and the error message says: "Failed to set permissions".

After doing some searching around I tried running this command:

```
 unison /home/crownambassador/.unison/USB\ Stick.prf b -perms=0
```

It opens Unison and the USB Stick profile, but has not folder set to sync.

How do I get this to work properly?

Thanks.

I kept on trying what I have been doing, (removing the profiles and redoing it) and now it works for some reason. Very weird!

---

### Post by borobudur on 2008-09-17
Check the solution of Toufik in this thread: [http://ubuntuforums.org/showthread.php?t=893365](http://ubuntuforums.org/showthread.php?t=893365)

Had the same problem and this works perfect for me!

---

### Post by ogami1972 on 2011-01-16
confirmed...this advice solved my unison sync issue.

props to Borobudur...

coupled with a request to get an easier to spell username.

---

### Post by borobudur on 2011-01-20
> **ogami1972 said:**
> coupled with a request to get an easier to spell username.
:)

---

