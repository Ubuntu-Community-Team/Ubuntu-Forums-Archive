---
title: "Smart Data reports huge amaount of bad sectors!"
date: 2011-11-13
forum: Hardware
---

### Post by BigSilly on 2011-11-13
Using the missus' Dell 1525 Inspiron running Ubuntu 10.04.3 LTS 32 bit.

Could this be a fault with the Smart Data tools or do we have a borked drive here? In Disk Utility/Smart Data, it shows under Current Pending Sector Count a value of -223477758 bad sectors, and says "Disk has a few bad sectors". I'll say!

It's been like this for a year. I only left it so long because ages ago I found a number of similar situations on the forums, but the general consensus was that Smart Data was often wrong when it comes to big numbers. The OS has been running fine with no issues, but of course that doesn't mean it isn't about to go, as with all hardware.

But this is indeed a massive number to be getting wrong isn't it? What's the likely story here do you think?

---

### Post by BigSilly on 2011-11-14
Shameful bumpage for helpage. :)

---

### Post by WasMeHere on 2011-11-14
Hi BigSilly,

IMHO the smart drive seems sillier than your ubuntu-name ;-)

Have you tried a force check of the disk with ***e2fsck***? Or tried to copy/clone the partition with ***ddrescue***? I think this way you will get an answer about the real status of your hard drive: Are there any bad sectors or not?

Have fun finding out
Olle

---

### Post by BigSilly on 2011-11-14
> **Olle Wiklund said:**
> Hi BigSilly,

IMHO the smart drive seems sillier than your ubuntu-name ;-)

Have you tried a force check of the disk with ***e2fsck***? Or tried to copy/clone the partition with ***ddrescue***? I think this way you will get an answer about the real status of your hard drive: Are there any bad sectors or not?

Have fun finding out
Olle

Hi there, and thanks for the reply.

I'll give that a go, thanks. I usually use Clonezilla for image backup. What would ddrescue do differently, and how would it tell me the drive is kaput? Cheers.

---

### Post by WasMeHere on 2011-11-14
ddrescue is a very good tool to rescue what is left on failing disks. Browse the internet or download ddrescue and read the info page
```
info ddrescue
``` It is very well written and explains what can be done including why and how.

Remember that you should run it from another drive and have the drive to be rescued (or tested in your case) ***un***mounted! I think ddrescue is on the Clonezilla disk, if not, you can download in into a live Ubuntu system with
```
sudo apt-get install ddrescue
```

---

