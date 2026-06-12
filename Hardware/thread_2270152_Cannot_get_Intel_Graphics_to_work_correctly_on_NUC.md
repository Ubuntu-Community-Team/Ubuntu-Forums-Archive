---
title: "Cannot get Intel Graphics to work correctly on NUC 5I5RYH"
date: 2015-03-20
forum: Hardware
---

### Post by ktulu2 on 2015-03-20
Hi there,
I recently bought Intel's new i5 NUC, which comes with the HD 6000 GPU.  I cannot get it to work properly with Ubuntu, though.
i915.modeset=0 works as a temporary work-around, but not as a long term fix.
Here's an example of the problems I'm experiencing: [Sorry about the lighting]("http://i.imgur.com/oi6gcoH.jpg")
 - Text not displaying correctly
 - Context menus look like static interference
 - Icons not loading

Thanks.

---

### Post by gordintoronto on 2015-03-21
When hardware is newer than the OS, it's often problematic. Have you tried the development version of Ubuntu, 15.04? (I have been using Xubuntu 15.04 for three weeks with no problems.)

---

### Post by Mikael_Glentoft on 2015-07-04
Hi

I have the same problem and is not really sure how to fix it.
To get any image at all I first had to update the BIOS to [v0249]("https://downloadcenter.intel.com/download/24977/BIOS-Update-RYBDWi35-86A-")  (and switch to 50Hz frequency)

Ubuntu 14.04 did not work at all, I only got a gray mass with a few lines here and there.
I tried 15.04 and this worked like a charm (the install part).

The problem now is that the image does not seem to fit the tv - the "quick launch bar" at the right is only party visible and I lack a few centimeters at the top as well.
Anyone know how to fix it?


Regards,
Mikael

---

