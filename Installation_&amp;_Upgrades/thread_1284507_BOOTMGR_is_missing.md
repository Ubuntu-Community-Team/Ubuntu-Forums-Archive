---
title: "BOOTMGR is missing"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by el canadiano on 2009-10-06
...and by fixing it, I can't boot into Ubuntu. I'm using Jackalope, if that helps at all. I had the problem listed below.

[http://lifehacker.com/251733/vista-tip--repair-bootmgr-is-missing-error](http://lifehacker.com/251733/vista-tip--repair-bootmgr-is-missing-error)

For some reason, I can't get into c:\found.000 as an admin or a regular user. Also, I WAS going to have a partitioned version of Ubuntu using LVPM, but I never got to finish it. I am aware of my limitations with Wubi vs. a full Ubuntu partition. Anyways a little help will be nice.

Thanks,
el canadiano.

---

### Post by el canadiano on 2009-10-07
For some reason, I can't even boot directly from the Ubuntu CD as well! =/

---

### Post by pmlxuser on 2009-10-07
to boot into a live Cd you need your computer set in bios to boot from CD as first option. Other computers you press Esc/F12 /del to choose the boot medium.

is yours set to this already

---

### Post by Mark Phelps on 2009-10-07
The fact that you have a "found" file indicates that chkdsk found some corrupted files and was not able to recover the file names.  If one or more of these were your Vista boot loader files, the only known way to repair them is with the link you provided -- booting from a Vista DVD and running Startup Repair.

You mentioned wubi, so if that's the only way you have to boot into Ubuntu, you're hosed there as well -- one of the downsides of using a Wubi-based installation.

So, basically, if you're asking if you can repair Vista from inside Ubuntu, the unfortunate answer is no.

---

### Post by el canadiano on 2009-10-07
> **Mark Phelps said:**
> The fact that you have a "found" file indicates that chkdsk found some corrupted files and was not able to recover the file names.  If one or more of these were your Vista boot loader files, the only known way to repair them is with the link you provided -- booting from a Vista DVD and running Startup Repair.

You mentioned wubi, so if that's the only way you have to boot into Ubuntu, you're hosed there as well -- one of the downsides of using a Wubi-based installation.

So, basically, if you're asking if you can repair Vista from inside Ubuntu, the unfortunate answer is no.

Thanks for the reply. I had that error and re-did the startup repair. What happened after was that I was unable to boot into Ubuntu (Wubi). I tried reinstalling Wubi (I had the original root.disk backed up), but after rebooting after a new successful installation, Windows Boot Manager does not pop up, and I go directly to Vista, which is REALLY pissing me off now.

My original plan was to convert my Wubi installation to a full partition using LVPM, now I can't even boot from CD. I usually successfully do it by hitting F12 in Boot Menu and selecting a Boot from CD. That just sent me directly to Vista.

---

### Post by Mark Phelps on 2009-10-07
> **el canadiano said:**
> Thanks for the reply. I had that error and re-did the startup repair. What happened after was that I was unable to boot into Ubuntu (Wubi). I tried reinstalling Wubi (I had the original root.disk backed up), but after rebooting after a new successful installation, Windows Boot Manager does not pop up, and I go directly to Vista, which is REALLY pissing me off now.

My original plan was to convert my Wubi installation to a full partition using LVPM, now I can't even boot from CD. I usually successfully do it by hitting F12 in Boot Menu and selecting a Boot from CD. That just sent me directly to Vista.

OK, I'm NOT an expert on Wubi, but I'm guessing what happened is that when you repaired Vista, it rewrote it's boot loader files and effectively removed any previous Wubi entries.  Windows Boot Manager will only show a menu if there is more than one OS choice available, which with the Wubi info gone, is no longer the case.

I would have thought that a reinstall of Wubi would have fixed it.  Sorry, don't know enough about Wubi to tell you what to add using BCD Edit in Vista to get Wubi access back.

---

### Post by el canadiano on 2009-10-07
Yeah, that I thought too, but I guess it doesn't seem to be the case, which really pisses me off. I'm gonna try reburning the Live CD.

---

### Post by el canadiano on 2009-10-07
Doesn't seem like Vista likes me :(

I was also wondering if there was a program that would let me view the root.disk file inside Windows. The two programs listed here do not work.

[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?)

---

### Post by Gstrazds on 2010-05-11
Hi there.. I now have this problem too..

I need to know where the wubi boot loader or mount point  is located? c:\ubuntu? or elsewhere..

the process would then be to add; Wubi info using bcdedit commands to add it to boot manager

Your install would then be recovered

---

### Post by el canadiano on 2010-05-11
I got this fixed by uninstalling using the uninstall method at c:\ubuntu with a root.disk backed up and reinstalled it afterwards and replaced root.disk.

---

