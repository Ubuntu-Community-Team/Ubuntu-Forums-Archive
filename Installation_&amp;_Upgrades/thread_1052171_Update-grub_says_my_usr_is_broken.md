---
title: "Update-grub says my /usr is broken?"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by bubba_169 on 2009-01-27
Im confused and google is turning out nothing for me? After updating to a newer kernel, 2.6.27-11 from 2.6.27-7, I noticed it wasn't showing up in grub. I tried running update-grub and the exact error message I get is:

```
$ sudo update-grub
Your /usr is broken, please fix it before call this wrapper!
```

Any ideas?

---

### Post by breusshe on 2009-01-29
Yeah, just figured it out.  You need to do the following:

chmod 744 /usr/sbin/update-grub

The problem is that when you call "update-grub" it runs the script /sbin/update-grub (not in /usr), this file checks a couple of things, one has to do with your kernel conf file stuff (not real sure what it is about) and the other makes sure that /usr/sbin/update-grub exists and is executable.  Right now, /usr/sbin/update-grub is not executable.

So, run the chmod and then "sudo update-grub" and it will work.

---

### Post by bubba_169 on 2009-01-30
Thank you, worked a treat :D

Is it just me or has the thanks button gone walkies?
.. And I cant mark this as solved?

---

### Post by beeman on 2009-06-06
Thanks, this worked (Linux Mint 6) :)

---

### Post by rohitfeb14 on 2009-10-14
In my case the file /usr/sbin/update-grub is missing..
What should i do?

---

### Post by breusshe on 2009-10-14
Reinstall grub-gfxboot package.  It is the one that has update-grub in it.

---

### Post by vikrant82 on 2009-10-15
There is no package with name grub-gfxboot, but there's a gfxboot package which I already installed. Still, no /usr/sbin/update-grub but there's a /sbin/update-grub.

$sudo update-grub 
Your /usr is broken, please fix it before call this wrapper!

---

### Post by vikrant82 on 2009-10-15
Well the correct package was grub-pc, which installed /usr/sbin/update-grub. 

The package is installed by default, but it got removed for me when I had installed a package 'grub-choose-default'.

---

### Post by breusshe on 2009-10-15
Oh, sorry for pointing you to the wrong package.  Glad you got it going again.

---

### Post by azimout on 2009-10-18
The funny thing is, installing 'grub-pc' to get back /usr/sbin/update-grub removed the package 'grub', which contained /sbin/update-grub, which gave the above error message in the first place :-)

---

