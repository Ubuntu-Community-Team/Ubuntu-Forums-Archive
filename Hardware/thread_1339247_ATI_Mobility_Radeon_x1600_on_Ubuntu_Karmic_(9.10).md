---
title: "ATI Mobility Radeon x1600 on Ubuntu Karmic (9.10)"
date: 2009-11-27
forum: Hardware
---

### Post by Wolf_vx on 2009-11-27
Hello all.
It has bugged me for so long...
I am trying to install proprietary drivers for my ATI Mobility Radeon x1600 on the Asus A6Jsa. I downloaded the latest catalyst package which is 9.10 but after the install without a single error "aticonfig" doesn't recognize my graphics driver.

I don't know if it is me or is it people that never talk to each other but I got so many answers after long searches. (Google sucks on this type of searches as it hardly gives any relevant info (keeps throwing at me ubuntu 9.04)) One says you can't use it as it is old, ATI says you can as it is listed.

My major question: 

Can I get proprietary drivers for my graphics card running on Ubuntu Karmic?

If so then how can I get rid of this annoying message "aticonfig: No supported adapters detected"

Thank you for your time.

---

### Post by Wolf_vx on 2009-11-30
It looks like as I have suspected, there is no clear answer...

---

### Post by bessangel on 2009-12-08
Have you try this 

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English)

?

---

### Post by ssri on 2009-12-09
> **Wolf_vx said:**
> Hello all.
It has bugged me for so long...
I am trying to install proprietary drivers for my ATI Mobility Radeon x1600 on the Asus A6Jsa. I downloaded the latest catalyst package which is 9.10 but after the install without a single error "aticonfig" doesn't recognize my graphics driver.

I don't know if it is me or is it people that never talk to each other but I got so many answers after long searches. (Google sucks on this type of searches as it hardly gives any relevant info (keeps throwing at me ubuntu 9.04)) One says you can't use it as it is old, ATI says you can as it is listed.

My major question: 

Can I get proprietary drivers for my graphics card running on Ubuntu Karmic?

If so then how can I get rid of this annoying message "aticonfig: No supported adapters detected"

Thank you for your time.

How is this for a clear answer, no...

Catalyst 9.3 (the last proprietary drivers for your card and mine) can only be installed on distros running xserver 1.5.2 and kernels 2.6.28 and below.  Granted, there is a patch to run it with 2.6.29, but that point is moot considering Karmic runs on 2.6.31.

Since Jaunty shipped with 2.6.28, I only had to downgrade my xserver from 1.6 to 1.5.2 (among other downgrades) to install catalyst 9.3, which works just fine.  However, for karmic, it is going to be a rough ride with downgrades to both the kernel and xserver.

---

### Post by myromance123 on 2009-12-09
I know this sounds rude and terribly sad, but get an Nvidia card as it will really save you so much trouble.

 The drivers are very well made and last. I finally changed my Ati x1650 after it just got worse with each new Ubuntu (not the fault of Ubuntu but the poorly made driver).
  Since I bought my Nvidia 9400GT it just keeps getting better and smoother with each new release of Ubuntu.

 If you really want to stick to Ati, get one of the newer ones that may get better support in terms of drivers for Linux. This is how companies make money, force users to buy their newer products eventhough the older ones still suffice.

---

### Post by rajeev1204 on 2009-12-11
The proprieatary drivers wont work for you since ATI has dropped support for older cards, cards below the HD 2000 i bilieve.

Use the open source radeon or use the hardy heron 8.04.


rajeev

---

