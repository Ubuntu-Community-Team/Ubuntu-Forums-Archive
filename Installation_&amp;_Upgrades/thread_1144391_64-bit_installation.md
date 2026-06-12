---
title: "64-bit installation"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by Tucks on 2009-04-30
Hello All,

I am trying to install a 64-bit copy of Ubuntu (Intrpid Ibex). But it is throwing an erxception that processor doesnt support 64-bit OS. Per my laptops manual and the Intel website the processor T9600 supports 64-bit OS. Please let me know if there are any settings that need to be done prior to the installation.
Also any pointers in this regards will also be helpful

Currently I am running 32-bit copy of Ibex
Thanks and warm regards
Ketan

---

### Post by oldos2er on 2009-04-30
That's a Core 2 Duo, correct? Are you trying to install from a LiveCD?

---

### Post by Sef on 2009-04-30
> That's a Core 2 Duo, correct?

[Yes it is]("http://ark.intel.com/cpu.aspx?groupId=35563").

> I am trying to install a 64-bit copy of Ubuntu (Intrpid Ibex). But it is throwing an erxception that processor doesnt support 64-bit OS

Instead of trying to install go down the list to 'Check Disk for Errors' or something similar.  Make sure the everything with the disk is ok.

---

### Post by Tucks on 2009-04-30
> **oldos2er said:**
> That's a Core 2 Duo, correct? Are you trying to install from a LiveCD?

Hello [oldos2er]("http://ubuntuforums.org/member.php?u=338320"),
Yep thats a Core 2 Duo.. 
Yep, i was trying from a live cd. Also gave it a shot using the netinst. But had the same issue. I thought of installing via virtualbox but then backed out.

Thanks
Ketan

---

### Post by oldos2er on 2009-04-30
Did you run 'Check CD for defects,' or md5sum ([https://help.ubuntu.com/community/HowToMD5SUM)?](https://help.ubuntu.com/community/HowToMD5SUM)?)

---

### Post by Tucks on 2009-04-30
> **oldos2er said:**
> Did you run 'Check CD for defects,' or md5sum ([https://help.ubuntu.com/community/HowToMD5SUM)?]("https://help.ubuntu.com/community/HowToMD5SUM%29?")

Hello oldos2er / Sef,

Yeah i did try doing the step suggested. The signatures matched, so i believe there is no error/issue on that front. One of my colleagues mentioned something about configuring something in BIOS, which I found a little strange. Any pointers??

Well in the meantime let me try installing in VirtualBox. If that is successful then maybe I will give another try.

---

### Post by Tucks on 2009-05-02
> **Tucks said:**
> Hello oldos2er / Sef,

Yeah i did try doing the step suggested. The signatures matched, so i believe there is no error/issue on that front. One of my colleagues mentioned something about configuring something in BIOS, which I found a little strange. Any pointers??

Well in the meantime let me try installing in VirtualBox. If that is successful then maybe I will give another try.

Hello All,

Well I was able to run it successfully in virtualbox. so probably it would work in the normal env. Will give it a try sometime during the week. Hoping it would work

---

