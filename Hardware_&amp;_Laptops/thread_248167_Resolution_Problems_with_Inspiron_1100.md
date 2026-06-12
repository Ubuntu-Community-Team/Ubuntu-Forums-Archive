---
title: "Resolution Problems with Inspiron 1100"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by vkennedy85 on 2006-08-31
I posted this in a related forum but got no answer.

When I try to run the gedit I get a null Error.

I type sudo gedit 'path' i get an error, it says 'cannot open display: (null)

Any ideas how to fix the display problem and then fix the resolution?

---

### Post by croak77 on 2006-08-31
Can you post the output of gedit when you run it from a terminal?

You should use gksudo gedit not sudo gedit.

What is you resolution problem?

---

### Post by azraelx401 on 2006-08-31
> **vkennedy85 said:**
> I posted this in a related forum but got no answer.

When I try to run the gedit I get a null Error.

I type sudo gedit 'path' i get an error, it says 'cannot open display: (null)

Any ideas how to fix the display problem and then fix the resolution?

If it's an intel graphics chip then you need to download the i915 driver's using the synaptic program.  I have a Dell XPS M140 that has a wide screen view and I couldn't change the resolution but once I downloaded those driver's I was good to go.

---

### Post by vkennedy85 on 2006-09-01
IT's stuck on 640x480 resolution.

In the other thread they said if I edited the xorg.conf it would be fixed.  [http://www.ubuntuforums.org/showthread.php?t=190022&page=2&highlight=Inspiron+1100]("http://www.ubuntuforums.org/showthread.php?t=190022&page=2&highlight=Inspiron+1100")

It's in that thread.

---

### Post by wbmj on 2006-09-01
vK makes sure the 1100's BIOS is upgaded to the latest release before trying to edit your xorg.conf. There is a shared memory issue with the original BIOS shipped with that laptop.

---

### Post by azraelx401 on 2006-09-01
> **vkennedy85 said:**
> IT's stuck on 640x480 resolution.

In the other thread they said if I edited the xorg.conf it would be fixed.  [http://www.ubuntuforums.org/showthread.php?t=190022&page=2&highlight=Inspiron+1100]("http://www.ubuntuforums.org/showthread.php?t=190022&page=2&highlight=Inspiron+1100")

It's in that thread.

you still need to download the drivers.  I had the same problem but once i downloaded the drivers it fixed it.

---

### Post by vkennedy85 on 2006-09-04
Two questions then.

How do I know if the BIOS is updated, and if it's not how do I do so?

Also, how do I download the drivers?  Just google Inspiron 1100 Video Drivers?

Thanks.

---

### Post by vkennedy85 on 2006-09-17
Bump.

---

