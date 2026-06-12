---
title: "Resolution."
date: 2013-07-10
forum: Hardware
---

### Post by Ashboy on 2013-07-10
I just accidentally discovered that my laptop probably isn't using the right resolution. It's set to 1280x800, but I'm pretty sure it needs to be 1280x960. Is there an application that will let me change that? The Display 'configurer' (settings manager > display ) won't let me choose it. I read things about editing a certain file, but I checked and didn't seem to apply to 12.10. I can't see why someone hasn't yet made an app to modify it?

---

### Post by Yellow Pasque on 2013-07-10
This may help: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

If you still can't figure it out, pleasee post /var/log/Xorg.0.log (use [ code ][ /code ] tags).

---

### Post by Ashboy on 2013-07-11
Wow, I was really wrong about this. I had to draw a diagonal line (without anti aliasing) in Gimp to confirm it, but the resolution really is 1280x800! I'm guessing before, on Windows Vista, I had it scaled the whole time. :o

---

