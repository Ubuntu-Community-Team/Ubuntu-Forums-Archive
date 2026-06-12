---
title: "Dual Boot DV7 Question"
date: 2012-07-09
forum: Hardware
---

### Post by cancelledczech on 2012-07-09
I have an HP DV7-6187 that has two 750GB hard drives installed.  I would like to dual boot Win7 and 12.04, with each OS on its own hard drive.

Searching the forums I found threads that said to install 12.04 on the second drive as usual, just making sure that I change the boot loader to point to sdb. Then I just change my BIOS to load off the second drive, update GRUB, and I should be up and running.  If that's not right, please tell me.

My question is this: When I go into BIOS now, the boot order only gives me the option of notebook HDD and then the other options. The HDD option is not broken up into two different drives.  Is this because BIOS only sees an OS on one drive? Once I have two OS's will the BIOS give me the option of booting to the second drive first?

If I cannot specify the second drive to boot into, do I need to move the boot loader to sda? If I do that will I need to repair the Windows boot loader?

Thanks for any help you guys can give!

---

### Post by YannBuntu on 2012-07-10
Hello

Installing an OS an the other disk will not make this disk appear in the BIOS.

If i were you, I would:
1) try installing Ubuntu on the "hidden" disk (this will install GRUB on the first disk, which may work, but maybe not)
2) If that fails, you will have to install Ubuntu on the same disk as Windows.

---

### Post by cancelledczech on 2012-07-10
Thanks for the reply. I will just have to try installing and see what happens!

---

