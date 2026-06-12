---
title: "what is the kernal version number for Unbuntu 8.04"
date: 2008-07-20
forum: General Help
---

### Post by Windy Peaks on 2008-07-20
here is a simple one for some but not all.
I have Linux version 2.6. in a .bz2 file and I'm trying to load it on to this A200 toshiba laptop (not linux friendly) in the README file I have to add the kernel version number for Ubuntu 8.04 in to bzip2 -dc ../patch-2.6.xx.bz2 | patch -p1

Any Ideals Gentlemen

Thanks 
Windy:confused:

---

### Post by ibutho on 2008-07-20
Your post is a bit confusing. Can you please provide detailed info about what you are trying to do. Are you trying to install your own kernel, patch the existing Ubuntu kernel or do something else?

---

### Post by JagDragon on 2008-07-20
If you want to find the kernel version, use uname like this:
```
uname -r
```

If you want to, say, echo the kernel version, or use that in conjunction with something, use "`"'s around the command. So ```
mkdir my-kernel-`uname-r`
``` would create a directory called (for example) "my-kernel-2.6.24-19-generic".

The code you are looking for is (I think, I don't know what sort of patch you are applying)
```
bzip2 -dc ../patch-`uname -r`.bz2 | patch -p1
```

---

### Post by p_quarles on 2008-07-20
> **Windy Peaks said:**
> here is a simple one for some but not all.
I have Linux version 2.6. in a .bz2 file and I'm trying to load it on to this A200 toshiba laptop (not linux friendly) in the README file I have to add the kernel version number for Ubuntu 8.04 in to bzip2 -dc ../patch-2.6.xx.bz2 | patch -p1

Any Ideals Gentlemen

Thanks 
Windy:confused:
You don't install a kernel that way. I believe that you need to rethink your entire approach here.

---

### Post by Reiger on 2008-07-20
My kernel version number is **2.6.24-19-generic**. Which is the latest stuff for Hardy.

---

### Post by bilijoe on 2008-07-20
> **Windy Peaks said:**
> Any Ideals Gentlemen

Thanks 
Windy:confused: Gentlemen?  Excuse me for being off topic here, but isn't this a tad politically incorrect?  Do you not think there may well be some Ladies in your audience who are as well qualified to answer your question as the men out there?  Sorry, but OUCH!

---

### Post by Windy Peaks on 2008-07-21
> **bilijoe said:**
> Gentlemen?  Excuse me for being off topic here, but isn't this a tad politically incorrect?  Do you not think there may well be some Ladies in your audience who are as well qualified to answer your question as the men out there?  Sorry, but OUCH!


Fair point Young Lady, My Bad :(

Windy

---

### Post by Windy Peaks on 2008-07-21
Thanks:

That was simple and easy to understand, perhaps My question has dual meanings to some that I just don't now about.

Windy

---

