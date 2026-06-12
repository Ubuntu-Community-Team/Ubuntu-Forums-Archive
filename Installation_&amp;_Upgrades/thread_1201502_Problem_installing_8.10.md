---
title: "Problem installing 8.10"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by Richard Kimber on 2009-07-01
Having failed to install 9.04 on my new PC - there seems to be a kernel bug, see my post yesterday - I am trying 8.10, which is known to work.  However, this will not load either.  The message I get is:-

Aperture pointing to e820 RAM
Your BIOS doesn't leave a aperture memory hole
Please enable the IOMMU option in the BIOS setup
This costs 64MB of RAM

Can someone explain this for me?  I can't see any IOMMU option in my BIOS, which is AMI on an Asus M4A78 Pro M/B.

I have tried booting with iommu=memaper=3 (and 2,1) but I still get the same message.

I'd be very grateful for any suggestions, as I'm getting desperate.

---

### Post by presence1960 on 2009-07-01
> **Richard Kimber said:**
> Having failed to install 9.04 on my new PC - there seems to be a kernel bug, see my post yesterday - I am trying 8.10, which is known to work.  However, this will not load either.  The message I get is:-

Aperture pointing to e820 RAM
Your BIOS doesn't leave a aperture memory hole
Please enable the IOMMU option in the BIOS setup
This costs 64MB of RAM

Can someone explain this for me?  I can't see any IOMMU option in my BIOS, which is AMI on an Asus M4A78 Pro M/B.

I have tried booting with iommu=memaper=3 (and 2,1) but I still get the same message.

I'd be very grateful for any suggestions, as I'm getting desperate.

I forget the exact explanation, but that is not an error. There was a thread which I can't seem to locate right now dealing with this. But unless you have very little RAM the fix described in the thread seemed like too much work for 64 MB of RAM to be saved. I have 4 GB. So having 64 MB not available isn't an issue. if I find the thread I'll post a link.

If you can't install try the alternate text based installer, which is actually better because it gives way more options. Get it here: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by Richard Kimber on 2009-07-01
Thanks.  I have 4GB too.

Maybe I'll try the text based installer for 8.10, but it's not clear to me why that might overcome the aperture issue (whatever that is).

---

### Post by Kevbert on 2009-07-01
Please see [[COLOR="Red"]this.[/COLOR]]("http://rubbad.wordpress.com/2008/11/28/ubuntu-810-iommu/") To add boot options, take a look [COLOR="Red"][here]("https://help.ubuntu.com/community/BootOptions")[/COLOR].

---

### Post by Richard Kimber on 2009-07-01
> **presence1960 said:**
> 
If you can't install try the alternate text based installer, which is actually better because it gives way more options. Get it here: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

I tried the alternate installer, but got the same aperture error.

I'd be very grateful if you or anyone, can point me to a solution.

---

### Post by Richard Kimber on 2009-07-01
> **Kevbert said:**
> Please see [[COLOR="Red"]this.[/COLOR]]("http://rubbad.wordpress.com/2008/11/28/ubuntu-810-iommu/") To add boot options, take a look [COLOR="Red"][here]("https://help.ubuntu.com/community/BootOptions")[/COLOR].

Thanks.  I tried iommu=noaperture and that did indeed get rid of the aperture error.  However, when it went on to boot up, it got as far as

io scheduler cfg registered (default)

and then it hung.

---

### Post by presence1960 on 2009-07-01
> **Richard Kimber said:**
> I tried the alternate installer, but got the same aperture error.

I'd be very grateful if you or anyone, can point me to a solution.

I believe this is a BIOS issue. Have you looked on your mobo manufacturer's site to see if there is a BIOS update for your mobo?

---

### Post by Richard Kimber on 2009-07-01
> **presence1960 said:**
> I believe this is a BIOS issue. Have you looked on your mobo manufacturer's site to see if there is a BIOS update for your mobo?

The people who assembled the machine say it's the latest BIOS.

---

### Post by presence1960 on 2009-07-01
> **Richard Kimber said:**
> The people who assembled the machine say it's the latest BIOS.
it won't hurt to check the site. other than that, sorry to say I am out of ideas. Hopefully someone else will wander in here who can offer new suggestions. Just be patient if you can.

---

### Post by Richard Kimber on 2009-07-01
It's definitely the latest BIOS for that M/B, according to the manufacturer's website.

---

### Post by Kevbert on 2009-07-01
Please perform a couple of passes of memtest86+ from the boot menu. You should not get any errors. Also try the vga=... bootmenu option (see previous post for links).

---

### Post by Richard Kimber on 2009-07-01
> **Kevbert said:**
> Please perform a couple of passes of memtest86+ from the boot menu. You should not get any errors. Also try the vga=... bootmenu option (see previous post for links).

I did use memtest for an hour or so, but nothing showed up.  I'll have another look at vga= but I'm not convinced it's a graphics issue.  I disabled the built-in graphics and used an nvidia pci card that I know works with Ubuntu, but still had the same problems.

---

