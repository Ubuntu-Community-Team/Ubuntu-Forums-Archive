---
title: "can not install ubuntu on my notebook (sony vgn 365E)"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by xmzhu on 2008-12-14
I want to install ubuntu 8.04 but I failed. It stopped at the partition just after test the keyboard. 
The problem may be I first choose to install ubuntu under windows and I can not uninstall it (the uninstall.exe does not response to my click). Then, I format the disk when I installed ubuntu and tried completely install. I do not know why it stop at partition step. Can you tell me how to fix it?
Thank you

---

### Post by xmzhu on 2008-12-14
NO one reply
I am thinking about why this happens.
Since it stops at "partman" , I believe the installation under windows should have written sth into somewhere,which can not be cleared under windows. (I restore windows to the checkpoint before installation and I also clear mbr by fixmbr). But it still failed at partman. I pressed Ctr+Alt+F2 and try to write log but it ouputed no such command. 
I am really curious about how ubuntu writes and reads disk index table.
Thank you

---

### Post by 2hot6ft2 on 2008-12-15
It would help if you provide some useful info so that you can be helped such as RAM but someone will come thru with a solution. you could add noacpi to the end of the boot options when booting the livecd, I believe it's F6 key when starting the disc.

---

### Post by xmzhu on 2008-12-15
Thank you for your reply.
I added acpi=off but I have not tried noacpi.

---

### Post by xmzhu on 2008-12-15
By the way, how to provide some useful information.How to get out of the log ? Where is the log stored when installed with livecd?
Thank you

---

