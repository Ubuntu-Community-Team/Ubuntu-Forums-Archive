---
title: "Cannot disable Vari-Bright"
date: 2012-09-08
forum: Hardware
---

### Post by mascari on 2012-09-08
I posting this in the laptop area as I believe that this vari-bright "feature" is more geared toward laptops to preserve battery life.

I am running Ubuntu 12.04 on an HP Pavilion g7.  I have that plugged into a 32" Vizio flatscreen TV via an HDMI cable.

I now use my Ubuntu Laptop for work and home. Everything is so much cleaner and easier than in Windows.  Everything except for one thing:  Vari-Bright.

When I play games with dark backgrounds (such as Vendetta) or open screens with dark backgrounds (terminal window), the brightness level is auto-adjusted, evidently for "my own good".  But, it is horrible.  Everything gets dark and is all washed out. 

I have searched the forums, and they keep saying to turn off Vari-Bright.  So, I opened the CCC (Admin) and every time I unclick it and hit "apply" it rechecks it and puts it back to "maximize battery life".

I then went and found the amdpcsdb and amdpcsdb.default files and changed all of the lines with:

PP_VariBrightFeatureEnable=V1

To:

PP_VariBrightFeatureEnable=V0

Which I believe is the indicator to turn off vari-bright.  I did this in both files, and then rebooted.  (It had no immediate effect, so I just rebooted)

However, when I went back to the amdpcsdb file, every entry had been replaced with the "V1" option.  The default file was left unspoiled.

I then changed the permissions to READ ONLY on the file (after changing it again) and rebooted.  The file was remade with "V1" again - so it is something in the AMD software that basically is forcing vari-bright to be on.

I can see some value in having this option to turn on if you WANT it, but cannot see why it would always force itself to be on.

Does anyone know of anything I can do to force vari-bright to be off, stay off, and never, ever turn back on again.  I will never use it, and do not want it.  Ever.

Thank you!

---

