---
title: "CD drive on Laptop not detected"
date: 2007-10-07
forum: Hardware &amp; Laptops
---

### Post by LaRoza on 2007-10-07
I just got a new ThinkPad R61i, and am having some trouble. I only have random internet connections, so I don't really have the ability to do extensive searches for answers, so I hope this question is answered and I am able to read it.

I have two problems, neither of which involve wireless.

I am using Ubuntu 7.04, but plan on using Gutsy when it comes out.

I have two issues:

Mobile Intel 965 Express  and a resolution of 1280x800, but can only get 1024x768 on Feisty. This is the minor problem, which I can easily solve once I get a more reliable internet connection.

The main issue is with the Disk drive. It original defined it as "hdc" or something, but was unable to use it at all. What should the fstab entry be for a dvd/cd drive? Any suggestions are welcome, I don't mind trying them out.

I really need the cd drive to work, because I have no internet connection (except for the wireless network that is sometimes available, but is very week), and have 6 DVD's with the repositories, which rely on, but cannot use.

Thanks for your help.

---

### Post by LaRoza on 2007-10-08
It is morning now, and I have gotten the resolution thing sorted out (user error), by selecting a resolution my monitor supports :D.

I am connected to the internet through Ubuntu, on a wireless network, no trouble. :D

The CD drive still doesn't work, the fstab entry is:

```

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Can you see a problem with it? Thanks.

---

### Post by LaRoza on 2007-10-08
> 
DVD drive not recognized

The ata_piix SATA driver grabs ownership over the IDE ports when it is loaded, but (by default) does not support PATA ATAPI devices such as the Ultrabay optical drives. Thus, if the ide driver is compiled as a module and loaded after ata_piix, the DVD drive will not be recognized by either driver.

Either of the following configurations will work:

    * For kernel 2.6.14 and newer: enable ATAPI support in the SATA system using libata.atapi_enabled=1 (see below; this is experimental).
    * Compile IDE into the kernel (non-module).
    * Compile both IDE and SATA as modules and make sure IDE is loaded first (the module is called 'ide_generic'). 

Note that the optical drive must be in the Ultrabay during system boot (Ultrabay device swapping is currently unsupported). 

I found this, how do I do it?

[http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux)

---

