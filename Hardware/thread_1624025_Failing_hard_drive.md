---
title: "Failing hard drive?"
date: 2010-11-17
forum: Hardware
---

### Post by tommah04 on 2010-11-17
ok, unusual problem and I'm not really sure where to begin...

I have two HDDs in my computer, my master that holds my OS's, dual-boot win7 and ubuntu 10.10. and my slave that hold all my files and such for storage.

a little while ago my computer started having trouble booting, it would freeze or fail to load an OS (mostly freeze) during the boot process, and occasionally locks up while loaded.  so I am pretty confident on of my HDDs are dying, but I'm not sure which one

is there any way of checking which HDD could be failing?  I know this isn't exactly a ubuntu problem but this is my favorite forum, so I thought to come here first.

Thanks for any and all help

---

### Post by ibizatunes on 2010-11-17
in the bios enable smart then look in sys > admin > disk utility and see if you have any bad sectors etc

---

### Post by tommah04 on 2010-11-18
interesting... ok it says I have 8 bad sectors, is there anyway of repairing them?  or is it just to identify?

---

### Post by CharlesA on 2010-11-18
Does it say that they were reallocated or that they are pending?

---

### Post by psusi on 2010-11-18
It depends on which attribute says 8 sectors.  Is it offilne uncorrectable, pending relocation, or relocated?

---

### Post by tommah04 on 2010-11-18
"Reallocated Sector Count"

---

### Post by TNT1 on 2010-11-18
I get a reallocated sector count - disc failing warning. Many many sectors. Ubuntu, 10.04 is the only thing that reports this for this disc. 10.10 doesn't, and neither do any other distros. Why would that be?

327729 sectors to be exact...

---

### Post by CharlesA on 2010-11-18
As long as it doesn't start to increase, you'll be ok.

Just monitor it and replace the disk if it keeps increasing.

---

### Post by psusi on 2010-11-18
If there are 8 reallocated sectors and 0 pending, then you are probably fine, but keep an eye on it to make sure it does not increase.  Run the long self test to make sure there aren't any more it hasn't noticed yet.  Repeat the long self test periodically, say, once each week for a few weeks, then maybe once a month after that.  If the counts go up, replace the drive.

A ridiculously large count is usually the result of broken firmware in the drive reporting the count wrong.

---

