---
title: "Ubuntu and 2 versions of windows?"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by drmario on 2009-05-05
I have a laptop with Vista installed as the primary OS. I installed Ubuntu through wubi, so it isn't in a partition. My question is, can I create a partition, install Windows 7 in it and keep ubuntu? I think this question fits here better than a windows forum since grub handles the OS choices. To clarify what my installation would look like. I want Vista and Ubuntun on one partition (Ubuntu is already installed through Wubi)and then I would make a new partition to put Windows 7 on. Thanks.

---

### Post by Bartender on 2009-05-05
Hmmm -
Good question.  When you install Ubuntu via Wubi, does Wubi make any changes to the Windows Master Boot Record?
I'm guessing not.
If that's the case, the real question *is* a Windows question - does installing 7 after Vista's already installed screw up the Vista MBR?
If not, you should be fine.

---

### Post by drmario on 2009-05-05
> **Bartender said:**
> Hmmm -
Good question.  When you install Ubuntu via Wubi, does Wubi make any changes to the Windows Master Boot Record?
I'm guessing not.
If that's the case, the real question *is* a Windows question - does installing 7 after Vista's already installed screw up the Vista MBR?
If not, you should be fine.

Well I know you can dual-boot Vista and Windows 7. So I don't think there would be a problem with it. But I'm not sure if Windows 7 will try to replace the OS selection screen that Ubuntu installed.

---

### Post by Mark Phelps on 2009-05-05
Don't know exactly what Wubi does to create the boot menu, but it's likely that Windows 7 will overwrite that boot menu with it's own.  It will most certainly write its boot loader files to the Vista partition -- if it sees it at install time.  Whether it will remove the Ubuntu entry in the boot loader menu -- just don't know.

---

