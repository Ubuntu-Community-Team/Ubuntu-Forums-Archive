---
title: "Installation problems on old laptop"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by Linuxgood on 2009-10-17
Hi!

I have bought an Asus L5800C, which is about 6 years old.
There's a DVD/cdrom drive in it, but it will not read my burned CD's or DVD's. Oddly enough it can read an old Windows XP CD, so this is what I have on the harddrive. I have also created an ext3 partition with the partition magic software.

I would like to install Ubuntu on that partition, or preferably on the whole drive. I have wireless networking in the house, but I haven't been able to get it to work in XP.

I have a 2GB USB stick which I have used to get Linux distributions and other software on to the harddrive, and I have got ubuntu to run from within Windows. The laptop has a boot from USB in the Bios, but unfortunately it will not do it.

The laptop will boot from floppy, so I was thinking of booting with a Linux floppy and then somehow installing Linux from an image placed on the Windows XP partition or the EXT3 partition ?

What do you think ?

Thanks.

---

### Post by kerry_s on 2009-10-17
are you burning as a image at slow speed(4x)?

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Linuxgood on 2009-10-17
> **kerry_s said:**
> are you burning as a image at slow speed(4x)?

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

I burned the image at slow speed and tried it, but no luck..

---

### Post by Linuxgood on 2009-10-24
I managed to get the laptop to booot off a CD-R.
It wouldn't read the ones I made with k3b, but with
the default burner program in Ubuntu, burning at normal
speed, it recognized the CD. You apparently can't use CD+R
or any DVD's.

So now there's Ubuntu 9.10 on the laptop :popcorn:

---

### Post by dandnsmith on 2009-10-24
> **Linuxgood said:**
> I managed to get the laptop to boot off a CD-R.
It recognized the CD. You apparently can't use CD+R
or any DVD's.

There only 2 CD types: CDR (write once) and CDRW (rewritable) - the other variations only apply to DVD.

If there is at least one CD which it will recognise, how about running a lens-cleaner CD - that might get you better performance, if the drive isn't just dying.

In the matter of failing to boot from USB, I've come across several older PCs which look as if they ought to do it (from the BIOS entries), but either will not, or are incredibly choosy about type and format.

---

### Post by Linuxgood on 2009-10-24
> **dandnsmith said:**
> There only 2 CD types: CDR (write once) and CDRW (rewritable) - the other variations only apply to DVD.

If there is at least one CD which it will recognise, how about running a lens-cleaner CD - that might get you better performance, if the drive isn't just dying.

In the matter of failing to boot from USB, I've come across several older PCs which look as if they ought to do it (from the BIOS entries), but either will not, or are incredibly choosy about type and format.

Yes, sorry, there are only CD-R, no CD+R. DVD+R was new at the time my laptop was made, so it's possible it can't read those.

---

### Post by dandnsmith on 2009-10-25
> **Linuxgood said:**
> DVD+R was new at the time my laptop was made, so it's possible it can't read those.

It was common, in the 'early' days to have a combo drive on the laptop, and a statement that only DVD-R was supported - this was still said when later drives handling DVD+R were fitted (just never got updated).

---

### Post by Mark Phelps on 2009-10-25
If you can get the model number of your optical drive, you can then Google on that for specs and see if it will handle any DVD media.  If it's a really old drive, it might just be CD-only.

---

