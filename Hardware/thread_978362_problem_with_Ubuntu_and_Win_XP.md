---
title: "problem with Ubuntu and Win XP"
date: 2008-11-11
forum: Hardware
---

### Post by bcbotha on 2008-11-11
I didn't know where to place this thread.

I use Ubuntu for work and general use. my problem is that before i changed to ubuntu i was using Win XP with office 2007 so alot of my documents are not read in ubuntu. there are one or two programs that i still need running on XP. i recently installed opensuse just to play around with so i dont mind uninstalling it but if i do then ubuntu does not boot. ive tried installing VMWare on ubuntu but that never works. who else can i get XP running?

Thanks

---

### Post by lisati on 2008-11-11
Open Office Writer (which comes with most versions of Ubuntu) can read and write MS Office documents.

If you've removed Linux from your system and want to get Windows running again without reinstalling Linux, you may need a Windows installation CD/DVD. (Be cautious about using CDs of the "don't ask too many questions about where they came from" variety - they sometimes come with unpleasant surprises like malware, and also potentially open you up to legal hassles)
Boot up from the Windows CD/DVD, select "repair", and enter the following on the command line:
```

fixboot
fixmbr

```

---

### Post by bcbotha on 2008-11-11
will that allow me then to re-install windows?

open office cant read win office 2007 docs because open office reads .doc which microsoft used as the format since 95/98 but office 2007's format is .docx! you cant even open a office 2007 doc using office 2003.

---

### Post by bcbotha on 2008-11-11
iv managed to sort out the problem. i got VMware to work so im gonna install Windows on that.

---

### Post by 5nak3 on 2008-11-11
Just so you know open office 3 does support docx formats, as i've been using it to do so. I dont think it actually saves in docx formats. But this isn't an issue as you can just save as a doc file.

---

