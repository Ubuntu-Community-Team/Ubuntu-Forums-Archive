---
title: "Problems installing on a new laptop"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by Seefizzle on 2008-03-16
So I've got a brand new laptop, and I'm trying to install Ubuntu on it. The specs are something like this...
2 gig ram
250 gig hard drive
AMD Turion 64x2 processor
NVIDIA graphics card. (Not sure which exact one off the top of my head but it's a low to mid grade graphics card)

Now... On my desktop at home I installed Ubuntu using wubi. I think it's a fantastic way to install and run ubuntu. So this is what I try for my laptop. Everything goes fine until I get an error message about my Xserver and my graphics setup. Am I encountering compatibility issues with my nvidia graphics card or is it something else? As well does anyone have a solution? I'd really like to use wubi to install it instead of a live cd or something else... Not interested in re-formatting my hard drive.

Any help is much appreciated.

---

### Post by freebios on 2008-03-16
since you have a newer laptop try the hardy heron dvd.  It's supposed the have support for newer hardware.  just google hardy heron DVD and download the iso.  I hope it solves your problem.

---

### Post by Seefizzle on 2008-03-16
The only thing is that I would like to install it using wubi because I don't want to mess with partitioning my hard drive. Or is there an easy way to add a partition to your hard drive that doesn't require me to reload windows?

---

### Post by Ace2016 on 2008-03-16
Wubi should be on Ubuntu live cds of Hardy Alpha 5 or newer, i found this interesting link: [http://www.downloadsquad.com/2008/02/23/ubuntu-8-04-alpha-5-released/](http://www.downloadsquad.com/2008/02/23/ubuntu-8-04-alpha-5-released/)

So you can try downloading alpha 6 and if you like it, you might want to use its own partition

---

### Post by dptxp on 2008-03-16
> **Seefizzle said:**
> The only thing is that I would like to install it using wubi because I don't want to mess with partitioning my hard drive. Or is there an easy way to add a partition to your hard drive that doesn't require me to reload windows?

If the maximum used space ever was 20 GB, you can resize the Windows partition to 20 GB or more and create new ones without defragmenting the drive (that takes lot of time).

Backup all important data anyway.

---

### Post by newagelink on 2008-03-17
[COLOR="Indigo"]I don't know what wubi is; wish I had something else to say. Guess I'll look it up.[/COLOR]

---

### Post by sandysandy on 2008-03-17
> **Seefizzle said:**
> The only thing is that I would like to install it using wubi because I don't want to mess with partitioning my hard drive. Or is there an easy way to add a partition to your hard drive that doesn't require me to reload windows?

hi Seefizzle  

of course u can add a partition in ur existing hard drive without requiring u to reload windows. what i am talking about is dual booting windows and ubuntu. for this u would require ubuntu Cd (either live CD or alternate CD).

in this ur windows partition (NTFS format) is resized during installation and in the free space thus generated ubuntu root partition (ext3 format) and swap partition is created.

(in case u have more than one partition u can utilize the extra partition (after formatting to ext3) to load Ubuntu without resizing.)

some links for dual booting

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

other option is you can also resize ur windows partition using gparted live CD and create an ext3 partition ( for Ubuntu root ) and swap partition in the free space. thereafter u can install ubuntu on the new  ext3 partition created.

here is a link to tutorial on gparted.

[http://howtoforge.com/partitioning_with_gparted](http://howtoforge.com/partitioning_with_gparted)

Backup important data as safety prior to resizing.


regards

---

