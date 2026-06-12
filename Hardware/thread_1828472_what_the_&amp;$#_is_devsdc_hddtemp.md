---
title: "what the &amp;*$# is /dev/sdc hddtemp"
date: 2011-08-19
forum: Hardware
---

### Post by sclagler on 2011-08-19
Greetings!

I have two Western Digital hard drives in raid 0.

I have three entries in the hddtemp preferences for the gnome panel.

/dev/sda is listed as WDC WD5001AALS-00L3B2.
/dev/sdc is listed as WDC WD5001AALS-00L3B2.
/dev/sdb is listed as WDC WD5001AALS-00L3B2.

They are listed in that order.

What concerns me is the high temperature of /dev/sdc.
It slowly creeps up to the high 40's.

The /dev/sda and /dev/sdb settle comfortably into the very low 30's.

I do have a Windows 7 partition but I don't see how that is relevant.

Any help, insights, thoughts, etc would be greatly appreciated

-sheldon

---

### Post by Ozymandias_117 on 2011-08-19
Is that drive in a more enclosed section of your case?  Is it covered in dust? Those are two reasons they sometimes get hotter.

---

### Post by sclagler on 2011-08-19
The drives are on top and on bottom of a cage cooled by a 12 cm fan and filtered with a clean washable filter.  I don't believe there is a dust problem.

thanks,
 -sheldon

---

### Post by sclagler on 2011-08-19
forgot to mention that I have checked the drives for errors using fsck and on Windows 7.

thanks,
 -sheldon

---

### Post by hsoulen on 2011-08-19
Well the temp is well within tolerance for the drive so you should not freak out quite yet, but with that said is the drive that is reporting high temps in a different part of the box? You mentioned they are "on top and bottom of a cage", could the one showing the higher temps be on top? Remember heat rises!

Try rearranging the drives, if you have a large cage can you allow more airflow between the drives?

Cheers,

Hank

---

### Post by sclagler on 2011-08-19
I guess I didn't make myself clear.
Sorry about that.

I only have 2 hard drives not 3.

thanks,
 -sheldon

---

### Post by sclagler on 2011-08-20
Thanks to everyone for your input!

I feel like an idiot but am probably just obsessive.

What confused me was that /dev/sdc was listed as 
WDC WD5001AALS-00L3B2.

I completely forgot about my Seagate Baracuda external hard drive!
The /dev/sdc hddtemp applet behaves in accordance with this drive's operation.

Sorry

Thanks again,
 -sheldon

---

