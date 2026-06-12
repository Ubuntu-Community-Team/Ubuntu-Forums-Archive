---
title: "ACPI troubles..."
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by ghstzr0 on 2006-10-19
I have a Fujitsu Lifebook T4010 with the new Ubuntu Edgy Eft (RC) installed.  Not all of the ACPI features work (they didn't on Dapper either).  The features that don't work include: Dimming or blanking of the screen; the new gnome power features (power graph...).  Help, I really would like these features to work. ](*,)

---

### Post by ghstzr0 on 2006-10-20
Nobody???  Come on...

---

### Post by frogotronic on 2006-10-25
> **ghstzr0 said:**
> I have a Fujitsu Lifebook T4010 with the new Ubuntu Edgy Eft (RC) installed.  Not all of the ACPI features work (they didn't on Dapper either).  The features that don't work include: Dimming or blanking of the screen; the new gnome power features (power graph...).  Help, I really would like these features to work. ](*,)


I'm not using EE; I'm using DD,...BUT I think I've made progress.  I'm using a Dell Inspiron 8100 with an nVIDIA GeforGo2 video card.  I think the problem was the fact that the video driver doesn't support suspension "out-of-the-box".  This information is what I've gleemed from other threads.

Ok, so what's the solution?

1) make these changes to your files: [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

2) In your /etc/hibernate file, comment out all but your ACPI settings (there are REM instructions in the file) and select ACPI to "3" ie suspend to RAM.

3) Now my suspend to RAM works.  Have to solve hibernate (suspend to disk)

  I think ACPI is a working module on most machines, BUT needs a decent config utility.
Cheers,
cement_head

---

