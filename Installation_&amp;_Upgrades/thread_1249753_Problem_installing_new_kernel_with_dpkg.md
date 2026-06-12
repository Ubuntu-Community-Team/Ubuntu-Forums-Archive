---
title: "Problem installing new kernel with dpkg"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by Aptana on 2009-08-25
I have built and compiled the kernel based on instructions from the web, and now have a .deb file that's apparently ready for installing. When I type this command:

```
dpkg -i ../linux-image-2.6.24.6_custom.1.0_i386.deb
```

I get this:
```
root@ks23741:~/linux-source-2.6.24# dpkg -i ../linux-image-2.6.24.6_custom.1.0_i386.deb
couldn't open log `/var/log/dpkg.log': Permission denied
dpkg-deb: failed to create directory: Permission denied
dpkg: error processing ../linux-image-2.6.24.6_custom.1.0_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 ../linux-image-2.6.24.6_custom.1.0_i386.deb
```

I have tried Google'ing (this most of the time fixes my problems related to errors :P) but have found nothing suitable :(

Any help would be greatly appreciated. Thank you. :)

---

### Post by abansb on 2009-08-25
did you try 

```
sudo dpkg -i ../linux-image-2.6.24.6_custom.1.0_i386.deb
```Not for sure if this will work but it looks like you need root privilege from the permission denied 

If I am wrong I am a newbie to ubuntu :)

---

### Post by oldos2er on 2009-08-25
S/he's already at a root prompt, as shown by the #.

---

### Post by abansb on 2009-08-25
did not see that sorry

---

### Post by oldos2er on 2009-08-25
No need to be sorry! None of us were born knowing these things.

---

### Post by Aptana on 2009-08-25
Yeah, I used fakeroot to gain root privileges just for this task. :)

Problems still around though. :(

---

